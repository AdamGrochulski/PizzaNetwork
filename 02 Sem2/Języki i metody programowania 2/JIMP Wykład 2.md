#### Plik Main.java
```java
package klasy.cmplx;

public class Main {

    public static void main( String [] args ) {

        Cmplx c1 = new Cmplx();

        Cmplx c2 = new Cmplx(1,2);

        Cmplx c3 = new Cmplx(c2);

        System.out.println("c1= " + c1.toString() + " hashCode=" + c1.hashCode() );

        System.out.println("c2= " + c2.toString() + " hashCode=" + c2.hashCode() );

        System.out.println("c3= " + c3.toString() + " hashCode=" + c3.hashCode() );

        System.out.println( " c1 == c2 ? - " + c1.equals(c2));

        System.out.println( " c2 == c2 ? - " + c2.equals(c2));

        System.out.println( " c2 == c3 ? - " + c2.equals(c3));

        c1.setRe( c2.re() );

    }

}
```

#### Plik Cmplx.java
```java
package klasy.cmplx;
  
public class Cmplx {

    private double re = 0.0;

    private double im = 0.0;

    public Cmplx() {}

    public Cmplx( double r, double i ) {

        re = r;

        im = i;

    }

    public Cmplx( Cmplx o ) {

        this.re = o.re;

        this.im = o.im;

    }

    public void add( Cmplx o ) {

        re += o.re;

        im += o.im;

    }

    public void sub( Cmplx o ) {

        re -= o.re;

        im -= o.im;

    }

    public void mul( Cmplx o ) {

        re = this.re * o.re - this.im * o.im;

        im = this.re * o.im + this.im * o.re;

    }

    public void div( Cmplx o ) {

        throw new IllegalStateException("Not yet implemented");

    }

    public double abs() {

        return Math.sqrt( re*re + im*im );

    }

    public double angle() {

        return Math.atan2( im,re );

    }

    public void add( double o ) {

        re += o;

    }

    public void setRe( double re ) {

        this.re = re;

    }

    public void setIm( double im ) {

        this.im = im;

    }

    public double re( ) {

        return re;

    }

    public double im( ) {

        return im;

    }

    @Override

    public String toString() {

        return re + "+" + im + "i";

    }

    @Override

    public boolean equals( Object o ) {

        if( ! (o instanceof Cmplx) )

            return false;

        Cmplx oc = (Cmplx)o;

        return oc.re == re && oc.im == im;

    }

  

    @Override

    public int hashCode() {

        return 251 + (int) (Double.doubleToLongBits(this.re) ^ (Double.doubleToLongBits(this.re) >>> 32)) +

        79 * (int) (Double.doubleToLongBits(this.im) ^ (Double.doubleToLongBits(this.im) >>> 32));

    }

  

    public static void main( String [] args ) {

        Cmplx c1 = new Cmplx();

        Cmplx c2 = new Cmplx(1,2);

        Cmplx c3 = new Cmplx(c2);

        System.out.println("c1= " + c1.toString() + " hashCode=" + c1.hashCode() );

        System.out.println("c2= " + c2.toString() + " hashCode=" + c2.hashCode() );

        System.out.println("c3= " + c3.toString() + " hashCode=" + c3.hashCode() );

        System.out.println( " c1 == c2 ? - " + c1.equals(c2));

        System.out.println( " c2 == c2 ? - " + c2.equals(c2));

        System.out.println( " c2 == c3 ? - " + c2.equals(c3));

        c1.setRe( c2.re() );

        System.out.println( "c1=" + c1 + " = " + c1.abs() + "e^i*(" + c1.angle() + ")");

    }

}
```

#### Plik LList.java
```java
package klasy.list;

public class LList {

    private class Node {

        Object s;

        Node next;

        Node( Object s ) {

            this.s = s;

            this.next = null;

        }

        Node( Object s, Node next ) {

            this.s = s;

            this.next = next;

        }

    }

    private Node head = null;

    public void insert( Object s ) {

        head = new Node( s, head );

    }

    public void append( Object s ) {

        if( head == null )

            head = new Node(s);

        else {

            Node it = head;

            while( it.next != null )

                it = it.next;

            it.next = new Node(s);

        }

    }

    public void remove( Object s ) {

        if( head == null )

            return;

        if( head.s.equals(s) )

            head = head.next;

        Node it= head;

        while( it.next != null && ! it.next.s.equals(s))

            it= it.next;

        if( it.next == null )

            return;

        it.next = it.next.next;    

    }

    @Override

    public String toString() {

       String s = new String();

       Node it = head;

       while( it != null ) {

           s += "[" + it.s + "] -> ";

           it = it.next;

       }

       return s + "NULL";

    }

    public static void main( String [] args ) {

        LList wl = new LList();

        LList nl = new LList();

        LList ll = new LList();

        for( String s : args ) {

            nl.append(s);

            try {

                int i = Integer.parseInt(s);

                ll.insert(i);

            } catch( NumberFormatException ex ) {

                wl.insert(s);

            }

        }

        System.out.println( nl );

        System.out.println( wl );

        System.out.println( ll );

        nl.remove("Janek");

        System.out.println(nl);

        nl.remove("Ala");

        System.out.println(nl);

        nl.remove("6.7");

        System.out.println(nl);

    }

}
```