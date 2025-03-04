#### Plik Echo.java
```java
public class Echo {
	public static void main( String [] args ) {
		for( int i= 0; i < args.length; i++ )
			System.out.print( " " + args[i] );
		System.out.println();
	}
}
```

#### Plik Echo2.java
```java
class Echo2 {

    public void echo( String [] a ) {

        for( String s : a )

            System.out.println( s );

    }

}
```
#### Plik Echo3.java
```java
class Echo3 {

    public static void main( String [] args ) {

        Echo2 e = new Echo2();

        e.echo( args );

    }

}
```

#### Plik DT.java
```java
public class DT {

    private double [] t = null;

    private int n = 0;;

  

    public DT() {

        t = new double[16];

        n = 0;

    }

  

    public void append( double x ) {

        // dopisuje x na koniec t

        if( n == t.length )

            doubleSize();

        t[n++] = x;

    }

  

    public double get( int i ) {

        // zwraca t[i]

        if( i < 0 || i >= n )

            throw new ArrayIndexOutOfBoundsException( "Tablica ma tylko " + n + " elementów" );

        return t[i];

    }

  

    public int size() {

        return n;

    }

  

    public void sort() {

        java.util.Arrays.sort( t, 0, n );

    }

  

    public String toString() {

        String o = "[";

        for( int i= 0; i < n; i++ )

            o += " " + t[i];

        return o + " ]";

    }

  

    private void doubleSize() {

        double [] nt = new double[2*n];  // t.length tak samo fajne jak n

        for( int i= 0; i < n; i++ )

            nt[i] = t[i];

        t = nt;

    }

  

// ZOSTAWIONE DLA PRZESTROGI

    private void reSize() {

        double [] nt = new double[n+1];  // t.length tak samo fajne jak n

        for( int i= 0; i < n; i++ )

            nt[i] = t[i];

        t = nt;

    }

}
```

#### Plik TestDT.java
```java
public class TestDT {

    public static void main( String [] args ) {

        DT d1 = new DT();

  

        for( int i= 0; i < 20; i++ )

            d1.append( i / 10.0 );

  
  

        System.out.println( "d1 ma " + d1.size() + " elementów" );

  

        for( int i= 0; i < d1.size(); i++ )

            System.out.println( d1.get(i) );

  

        try {

            System.out.println( "get(31): " + d1.get(31) );

            System.out.println( "get(32): " + d1.get(32) );

        } catch( Exception ex ) {

            System.err.println( "ERROR: " + ex.getMessage() );

            ex.printStackTrace();

            System.exit(1);

        }

  

    }

}
```

#### Plik Test2_DT.java
```java
public class Test2_DT {

    public static void main( String [] args ) {

        DT d1 = new DT();

        DT d2 = new DT();

  

        for( int i= 0; i < 20; i++ ) {

            d1.append( i / 10.0 );

            if( i % 2 == 0 )

                d2.append( 1.9 - i / 10. );

        }

  
  

        System.out.println( "d1 ma " + d1.size() + " elementów" );

  

        for( int i= 0; i < d1.size(); i++ )

            System.out.println( d1.get(i) );

  

        System.out.println( "d2 ma " + d2.size() + " elementów" );

  

        for( int i= 0; i < d2.size(); i++ )

            System.out.println( d2.get(i) );

  

    }

}
```

#### Plik Test3_DT.java
```java
public class Test3_DT {

    public static void main( String [] args ) {

        DT d1 = new DT();

  

        int n = args.length > 0 ? Integer.parseInt( args[0] ) : 10000;

  

        for( int i= 0; i < n; i++ ) {

            d1.append( i / 10.0 );

        }

  

        System.out.println( "d1 ma " + d1.size() + " elementów" );

  

    }

}
```

#### Plik Test4_DT.java
```java
import java.util.Random;

  

public class Test4_DT {

    public static void main( String [] args ) {

        int n = args.length > 0 ? Integer.parseInt( args[0] ) : 10;

  

        DT [] tdt = new DT[n];

  

        Random r = new Random();

  

        for( int i= 0; i < n; i++ ) {

            tdt[i] = new DT();

            int l = 1 + r.nextInt(5);

            for( int j= 0; j < l; j++ )

                tdt[i].append( r.nextDouble() );

            if( args.length > 1 && args[1].equals("sort") )

                tdt[i].sort();

        }

  

        for( int i= 0; i < n; i++ )

            System.out.println( tdt[i] );

  

    }

}
```


