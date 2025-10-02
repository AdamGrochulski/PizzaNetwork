#### Plik AGroup.java
```java
package jcflecture;

  

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
package jcflecture;

  

import java.util.Arrays;

import java.util.Comparator;

import java.util.Iterator;

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
package jcflecture;

  

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
package jcflecture;

  

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
package jcflecture;

  

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

        GroupInterface g = new AGroup();

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
package jcflecture;

  

import java.util.Comparator;

public class SAComparator implements Comparator<Student> {

  

    @Override

    public int compare(Student sa, Student sb) {

        return sa.getAlbum() - sb.getAlbum();

   }

  

}
```

#### Plik Student.java
```java
package jcflecture;

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

        int sc = sureN.compareTo(s.sureN);

        return sc != 0 ? sc : firstN.compareTo(s.firstN);

    }

  

    @Override

    public String toString() {

        return firstN + " " + sureN + " (" + album + ")";

    }

  

    @Override

    public boolean equals(Object o) {

        return o instanceof Student && album == ((Student) o).album;

    }

  

    @Override

    public int hashCode() {

        return album;

    }

}
```