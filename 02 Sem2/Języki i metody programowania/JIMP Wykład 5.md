## Package mesh:
#### Plik Mesh.java
```java
package mesh;

import java.util.List;

public class Mesh {

    private List<Vertex> v;

    private List<Tetra> tet;

    private List<Triangle> tri;

}
```

#### Plik SparseMatrix.java
```java
package mesh;

public interface SparseMatrix {

    public double [] multuply( double [] x );  // returns M*x

    public SparseMatrix transpose();

}
```

#### Plik SparseMatrixImplementation.java
```java
package mesh;

import java.util.HashMap;

import java.util.Map;

public class SparseMatrixImplementation implements SparseMatrix {

  

    private Map<Integer, Map<Integer, Double>> m = new HashMap<>();

  

    public void addTo(int i, int j, double a) {

        // m[i,j] += a

        if (!m.containsKey(i)) {

            m.put(i, new HashMap<Integer, Double>());

        }

        Map<Integer, Double> row = m.get(i);

        if (row.containsKey(j)) {

            row.put(j, row.get(j) + a);

        } else {

            row.put(j, a);

        }

    }

  

    public double get(int i, int j) {

        if (m.containsKey(i)) {

            Map<Integer, Double> r = m.get(i);

            if (r.containsKey(j)) {

                return r.get(j);

            } else {

                return 0.0;

            }

        } else {

            return 0.0;

        }

    }

  

    @Override

    public String toString() {

        int n = 10;

        String ret = new String();

        for (int i = 0; i < n; i++) {

                for (int j = 0; j < n; j++)

                    ret += get(i,j) + " ";

                ret += "\n";

        }

        return ret;

    }

  

    @Override

    public double[] multuply(double[] x

    ) {

        throw new UnsupportedOperationException("Not supported yet."); // Generated from nbfs://nbhost/SystemFileSystem/Templates/Classes/Code/GeneratedMethodBody

    }

  

    @Override

    public SparseMatrix transpose() {

        throw new UnsupportedOperationException("Not supported yet."); // Generated from nbfs://nbhost/SystemFileSystem/Templates/Classes/Code/GeneratedMethodBody

    }

  

    public static void main(String[] args) {

        SparseMatrixImplementation m = new SparseMatrixImplementation();

        java.util.Random r = new java.util.Random();

        int n = 10;

        int nz = r.nextInt(30) + 1;

        for (int k = 0; k < nz; k++) {

            m.addTo(r.nextInt(n), r.nextInt(n), 1.0);

        }

        System.out.println(m);

        for( int i= 0; i < n; i++ )

            m.addTo( i, i, 5.0 );

       System.out.println("-----");

        System.out.println(m);

  

    }

  

}
```

#### Plik Tetra.java
```java
package mesh;

import java.util.Iterator;

public class Tetra implements Iterable<Integer> {

    private int [] v;

    public Tetra( int [] v ) {      

        if( v.length != 4 )

            throw new IllegalArgumentException("Tetrahedron must have 4 nodes!");

        this.v = v;

    }

  

    /**

     * @return the v

     */

    public int[] getV() {

        return v;

    }

  

    /**

     * @param v the v to set

     */

    public void setV(int[] v) {

        if( v.length != 4 )

            throw new IllegalArgumentException("Tetrahedron must have 4 nodes!");

        this.v = v;

    }

  

    @Override

    public Iterator<Integer> iterator() {

        return new Iterator<Integer> () {

            private int i= 0;

            @Override

            public boolean hasNext() {

                return i < 4;

            }

  

            @Override

            public Integer next() {

                return v[i++];

            }

        };

    }

}
```

#### Plik Triangle.java
```java
package mesh;

public class Triangle {

    private int [] v;

    public Triangle( int [] v ) {

        if( v.length != 3 )

            throw new IllegalArgumentException("Triangle must have 3 nodes!");

        this.v = v;

    }

  

    /**

     * @return the v

     */

    public int[] getV() {

        return v;

    }

  

    /**

     * @param v the v to set

     */

    public void setV(int[] v) {

        this.v = v;

    }

}
```

#### Plik Vertex.java
```java
package mesh;

public class Vertex {

    private int dim;

    private double [] x;

    public Vertex( double [] x ) {

        dim = x.length;

        this.x = x;

    }

  

    /**

     * @return the dim

     */

    public int getDim() {

        return dim;

    }

  

    /**

     * @param dim the dim to set

     */

    public void setDim(int dim) {

        this.dim = dim;

    }

  

    /**

     * @return the x

     */

    public double[] getX() {

        return x;

    }

  

    /**

     * @param x the x to set

     */

    public void setX(double[] x) {

        this.x = x;

    }

}
```

## Package students:
#### Plik AGroup.java
```java
package students;

import java.util.Arrays;

import java.util.Comparator;

import java.util.Iterator;

public class AGroup implements GroupInterface {

  

    private Student[] g = new Student[16];

    private int n = 0;

  

    @Override

    public void add(Student s) {

        if (n == g.length) {

            doubleSize();

        }

        g[n++] = s;

    }

  

    private void doubleSize() {

        Student[] ng = new Student[2 * n];

        System.arraycopy(g, 0, ng, 0, n);

        g = ng;

    }

  

    @Override

    public void sort() {

        Arrays.sort(g, 0, n);

    }

  

    @Override

    public void sort(Comparator<Student> c) {

        Arrays.sort(g, 0, n, c);

    }

    @Override

    public Iterator<Student> iterator() {

        return new GIterator(g, n);

    }

  

    class GIterator implements Iterator<Student> {

        private Student[] t;

        private int i= 0;

  

        public GIterator(Student[] g, int ls) {

            t = new Student[ls];

            System.arraycopy(g, 0, t, 0, ls);

        }

        @Override

        public boolean hasNext() {

            return i < t.length;

        }

        @Override

        public Student next() {

            return t[i++];

        }

    }

  

}
```

#### Plik BGroup.java
```java
package students;

import java.text.Collator;

import java.util.Arrays;

import java.util.Comparator;

import java.util.Iterator;

import java.util.Locale;

public class BGroup implements GroupInterface {

  

    private Student[] g = new Student[16];

    private int n = 0;

  

    @Override

    public void add(Student s) {

        if (n == g.length) {

            doubleSize();

        }

        g[n++] = s;

    }

  

    private void doubleSize() {

        Student[] ng = new Student[2 * n];

        System.arraycopy(g, 0, ng, 0, n);

        g = ng;

    }

  

    @Override

    public void sort() {

        Arrays.sort(g, 0, n);

    }

  

    @Override

    public void sort(Comparator<Student> c) {

        Arrays.sort(g, 0, n, c);

    }

  

    @Override

    public Iterator<Student> iterator() {

        return new Iterator<Student>() {

            private Student[] t = new Student[n];

            private int i = 0;

            {

                System.arraycopy(g, 0, t, 0, n);

            }

  

            @Override

            public boolean hasNext() {

                return i < t.length;

            }

  

            @Override

            public Student next() {

                return t[i++];

            }

        };

    }

}
```

#### Plik Group.java
```java
package students;

import java.util.ArrayList;

import java.util.Collections;

import java.util.Comparator;

import java.util.Iterator;

import java.util.List;

public class Group implements GroupInterface {

    private List<Student> g;

    public Group() {

        g = new ArrayList<>();

    }

    @Override

    public void add( Student s ) {

        for( Student e : g )

            if( e.equals(s))

                //throw new IllegalArgumentException( s + " już jest" );

                return;

        g.add(s);

    }

    @Override

    public void sort() {

        Collections.sort(g);

    }

    @Override

    public void sort( Comparator<Student> c) {

        g.sort(c);

    }

  

    @Override

    public Iterator<Student> iterator() {

        return g.iterator();

    }

    @Override

    public String toString() {

        StringBuilder r = new StringBuilder();

        for( Student s : g )

            r.append(s).append('\n');

        return "[\n" + r.toString() + "]";

    }

}
```

#### Plik GroupInterface.java
```java
package students;

import java.util.Comparator;

import java.util.Iterator;

public interface GroupInterface extends Iterable<Student> {

  

    void add(Student s);

  

    Iterator<Student> iterator();

  

    void sort();

  

    void sort(Comparator<Student> c);

}
```

#### Plik JCFLecture.java
```java
package students;

import java.util.ArrayList;

import java.util.Arrays;

import java.util.Collections;

import java.util.Iterator;

import java.util.List;

public class JCFLecture {

  

    public static void withTable() {

        Student[] g = new Student[6];

        System.out.println("Tablica :" + g);

        g[0] = new Student(123456, "Jan", "Kowalski");

        g[1] = new Student(123457, "Zofia", "Nowak");

        g[2] = new Student(123458, "Adela", "Nowosielska");

        g[3] = new Student(123459, "Franciszek", "Ufalski");

        g[4] = new Student(123460, "Ewelina", "Zielińska");

        g[5] = new Student(123461, "Jan", "Świderski");

        Arrays.sort(g);

        System.out.println("Alfabetycznie:");

        for (Student s : g) {

            System.out.println("\t" + s);

        }

        Arrays.sort(g, new SAComparator());

        System.out.println("Po numerach albumów:");

        for (Student s : g) {

            System.out.println("\t" + s);

        }

    }

  

    public static void withList() {

        List<Student> g = new ArrayList<>();

        System.out.println("Lista :" + g);

        g.add(new Student(123456, "Jan", "Kowalski"));

        g.add(new Student(123457, "Zofia", "Nowak"));

        g.add(new Student(123458, "Adela", "Nowosielska"));

        g.add(new Student(123459, "Franciszek", "Ufalski"));

        g.add(new Student(123460, "Ewelina", "Zielińska"));

        g.add(new Student(123461, "Jan", "Świderski"));

        Collections.sort(g);

        System.out.println(g);

        System.out.println("Alfabetycznie:");

        for (Student s : g) {

            System.out.println("\t" + s);

        }

        Collections.sort(g, new SAComparator());

        System.out.println("Po numerach albumów:");

        for (Student s : g) {

            System.out.println("\t" + s);

        }

    }

  

    public static void withClass() {

        GroupInterface g = new BGroup();

        System.out.println("Group :" + g);

        g.add(new Student(123456, "Jan", "Kowalski"));

        g.add(new Student(123457, "Zofia", "Nowak"));

        g.add(new Student(123458, "Adela", "Nowosielska"));

        g.add(new Student(123459, "Franciszek", "Ufalski"));

        g.add(new Student(123460, "Ewelina", "Zielińska"));

        g.add(new Student(123461, "Jan", "Świderski"));

        g.add(new Student(123461, "Adam", "Świderski"));

        g.sort();

        System.out.println(g);

        g.sort(new SPLComparator());

        System.out.println("Alfabetycznie:");

        for (Student s : g) {

            System.out.println("\t" + s);

        }

        g.sort(new SAComparator());

        System.out.println("Po numerach albumów:");

        for (Student s : g) {

            System.out.println("\t" + s);

        }

        Iterator<Student> is = g.iterator();

        while( is.hasNext())

            System.out.println( is.next() );

    }

  

    /**

     * @param args the command line arguments

     */

    public static void main(String[] args) {

        if (args.length > 0) {

            if (args[0].equals("G")) {

                withClass();

            } else {

                withList();

            }

        } else {

            withTable();

        }

    }

  

}
```

#### Plik SAComparator.java
```java
package students;

import java.util.Comparator;

public class SAComparator implements Comparator<Student> {

  

    @Override

    public int compare(Student sa, Student sb) {

        return sa.getAlbum() - sb.getAlbum();

   }

  

}
```

#### Plik SPLComparator.java
```java
package students;

import java.text.Collator;

import java.util.Comparator;

import java.util.Locale;

public class SPLComparator implements Comparator<Student> {

    private final Comparator plCollator = Collator.getInstance(new Locale("pl","PL"));

  

    @Override

    public int compare(Student sa, Student sb) {

        int sc = plCollator.compare(sa.getSureN(),sb.getSureN());

        return sc != 0 ? sc : plCollator.compare(sa.getFirstN(), sb.getFirstN());

   }

  

}
```

#### Plik Student.java
```java
package students;

public class Student implements Comparable<Student> {

  

    private int album;

    private String firstN;

    private String sureN;

  

    public Student(int a, String f, String s) {

        album = a;

        firstN = f;

        sureN = s;

    }

    public int getAlbum() {

        return album;

    }

  

    @Override

    public int compareTo(Student s) {

        int sc = getSureN().compareTo(s.getSureN());

        return sc != 0 ? sc : getFirstN().compareTo(s.getFirstN());

    }

  

    @Override

    public String toString() {

        return getFirstN() + " " + getSureN() + " (" + album + ")";

    }

  

    @Override

    public boolean equals(Object o) {

        return o instanceof Student && album == ((Student) o).album;

    }

  

    @Override

    public int hashCode() {

        return album;

    }

  

    /**

     * @return the firstN

     */

    public String getFirstN() {

        return firstN;

    }

  

    /**

     * @return the sureN

     */

    public String getSureN() {

        return sureN;

    }

}
```

## Package wordcount
#### Plik WordCounter.java
```java
package wordcount;

import java.io.FileInputStream;

import java.io.InputStream;

import java.net.URL;

import java.util.*;

  

public class WordCounter {

  

    public static void main(String[] args) throws Exception {

        //String input = "https://wolnelektury.pl/katalog/lektura/krzyzacy-tom-pierwszy.html";

        String input = "https://wolnelektury.pl/katalog/lektura/chlopi-czesc-pierwsza-jesien.html";

        //String input = "data/txt";

        final int limit = 10;

  

        // Pobierz dokument

        String text = getText(input);

  

        // Policz słowa

        Map<String, Integer> counter = countWords(text);

  

        // Wyświetl najczęściej występujące

        System.out.println( limit + " najczęstszych słów:");

        List<Map.Entry<String, Integer>> list = new ArrayList<>(counter.entrySet());

  

        Collections.sort(list, new Comparator<Map.Entry<String, Integer>>() {

            @Override

            public int compare(Map.Entry<String, Integer> e1, Map.Entry<String, Integer> e2) {

                return e2.getValue() - e1.getValue();

            }

        });

  

        for (int i = 0; i < limit && i < list.size(); i++) {

            Map.Entry<String, Integer> e = list.get(i);

            System.out.println(e.getKey() + ": " + e.getValue());

        }

        // To samo ale funkcyjnie

        /*

        counter.entrySet().stream()

            .sorted((e1, e2) -> Integer.compare(e2.getValue(), e1.getValue()))

            .limit(10)

            .forEach(e -> System.out.println(e.getKey() + ": " + e.getValue()));    

        */

  

    }

  

    public static String getText(String input) throws Exception {

        StringBuilder sb = new StringBuilder();

        InputStream f = input.startsWith("http") ? new URL(input).openStream() :new FileInputStream(input); // new URL(adresUrl).openStream();

        try (Scanner scanner = new Scanner(f, "UTF-8")) {

            while (scanner.hasNextLine()) {

                sb.append(scanner.nextLine()).append("\n");

            }

        }

        return sb.toString();

    }

  

    public static Map<String, Integer> countWords(String text) {

        Map<String, Integer> licznik = new HashMap<>();

  

        //text = text.replaceAll("<[^>]*>", " ");

        text = text.toLowerCase().replaceAll("[^a-ząćęłńóśźż0-9]+", " ");

        String[] words = text.split("\\s+");

  

        for (String w : words) {

            if (w.length() < 4) continue;

            licznik.put(w, licznik.getOrDefault(w, 0) + 1);

        }

  

        return licznik;

    }

}
```
