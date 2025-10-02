#### Plik Account.java
```java
package minibank;

public abstract class Account {

    protected final String number;

    protected double balance;

    public Account( String number, double initialBalance) {

        this.number = number;

        this.balance = initialBalance;

    }

  

    /**

     * @return the number

     */

    public String getNumber() {

        return number;

    }

  

    /**

     * @return the balance

     */

    public double getBalance() {

        return balance;

    }

  

    /**

     * @param balance the balance to set

     */

    public void setBalance(double balance) {

        this.balance = balance;

    }

    public void deposit( double deposit ) {

        balance += deposit;

    }

    public boolean withdraw( double amount ) {

        if( balance >= amount ) {

            balance -= amount;

            return true;

        } else {

            throw new IllegalStateException( "Not enough funds on account #" + number + " !");

        }

    }

    @Override

    public String toString() {

        return "Acount # " + number + " current balance=" + balance;

    }

    public abstract void calculateInterest();

    public  String [] getLog() { return new String[0]; }

}
```

#### Plik SavingsAccount.java
```java
package minibank;

public class SavingsAccount extends Account {

    private double interestRate;

    public SavingsAccount( String number, double initialBalance, double interestRate ) {

        super(number,initialBalance);

        this.interestRate = interestRate;

    }

    @Override

    public void calculateInterest() {

        double interest = balance * interestRate / 100.0;

        balance += interest;

    }

    @Override

    public String toString() {

        return "Savings " + super.toString();

    }

}
```

#### Plik MiniBank.java
```java
package minibank;

public class MiniBank {

  

    /**

     * @param args the command line arguments

     */

    public static void main(String[] args) {

        Account[] bank = new Account[3];

        bank[0] = new AccountWithLog("L1717", 5000, 10);

        bank[1] = new SavingsAccount("123456", 5000.0, 5.0);

        bank[2] = new BussinessAccount("X1717", 5000, 10);

        Account savings = bank[1];

        Account bussiness = bank[2];

  

        savings.deposit(100);

        bussiness.withdraw(1000);

  

        for (Account a : bank) {

            a.withdraw(100);

        }

  

        for (Account a : bank) {

            a.withdraw(200);

        }

  

        for (Account a : bank) {

            a.deposit(230);

        }

  

        try {

            savings.withdraw(2000);

        } catch (Exception e) {

            System.err.println(e.getMessage());

        }

  

        for (Account a : bank) {

            System.out.println(a.getNumber() + " : " + a.getBalance());

        }

  

        for (Account a : bank) {

            a.calculateInterest();

        }

  

        for (Account a : bank) {

            System.out.println(a);

        }

  

        for (Account a : bank) {

            //if (a instanceof AccountWithLog) {

                System.out.println("Operations on account #" + a.getNumber());

                for (String s : a.getLog()) {

                    System.out.println("\t" + s);

                }

            //}

        }

  

    }

  

}
```

#### Plik BussinessAccount.java
```java
package minibank;

public class BussinessAccount extends Account {

  

    private double transactionFee;

  

    public BussinessAccount(String number, double initialBalance, double transactionFee) {

        super(number, initialBalance);

        this.transactionFee = transactionFee;

    }

  

    @Override

    public void deposit(double deposit) {

        if( deposit < transactionFee )

            throw new IllegalArgumentException("Deposit can not be lower than TF=" + transactionFee );

        super.deposit(deposit-transactionFee);

    }

    @Override

    public boolean withdraw(double amount ) {

        if( balance >= amount + transactionFee ) {

            balance -= amount + transactionFee;

            return true;

        } else {

            throw new IllegalStateException( "Not enough funds!" );

        }

    }

  

    @Override

    public void calculateInterest() {

    }

        @Override

    public String toString() {

        return "Bussiness " + super.toString();

    }

  

}
```

#### Plik AccountWithLog.java
```java
package minibank;

public class AccountWithLog extends BussinessAccount {

    private String [] log = new String[16];

    private int logLgt = 0;

  

    public AccountWithLog(String number, double initialBalance, double transactionFee) {

        super(number, initialBalance, transactionFee);

    }

    @Override

    public void deposit( double deposit ) {

        try {

            super.deposit(deposit);

            addLog( "Succesfull deposit of " + deposit );

        } catch( IllegalArgumentException e ) {

            addLog( "UNsuccessfull try to deposit " + deposit );

            throw e;

        }

    }

    @Override

    public boolean withdraw( double amount ) {

        try {

            super.withdraw(amount);

            addLog( "Succesfull withdraw of " + amount );

            return true;

        } catch( IllegalStateException e ) {

            addLog( "UNsuccessfull try to withdraw " + amount );

            throw e;

        }

    }

    @Override

    public String [] getLog() {

        String [] log = new String[logLgt];

        System.arraycopy(this.log, 0, log, 0, logLgt);

        return log;

    }

    private void addLog( String logItem ) {

        if( logLgt == log.length ) {

            String [] newlog = new String[logLgt*2];

            System.arraycopy(log, 0, newlog, 0, logLgt);

            log = newlog;

        }

        log[logLgt++] = logItem;

    }

  

}
```