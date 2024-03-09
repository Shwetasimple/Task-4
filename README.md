public class BankAccount {



	    private double balance;



	    public BankAccount(double balance) {

	        this.balance = balance;

	    }



	    public double getBalance() {

	        return balance;

	    }



	    public void deposit(double amount) {

	        if (amount > 0) {

	            balance += amount;

	            System.out.println("Deposit successful. Current balance: " + balance);

	        } else {

	            System.out.println("Invalid deposit amount.");

	        }

	    }



	    public boolean withdraw(double amount) {

	        if (amount > 0 && balance >= amount) {

	            balance -= amount;

	            System.out.println("Withdrawal successful. Remaining balance: " + balance);

	            return true;

	        } else {

	            System.out.println("Insufficient funds or invalid withdrawal amount.");

	            return false;

	        }

	    }

	}



	class ATM {

	    private BankAccount account;



	    public ATM(BankAccount account) {

	        this.account = account;

	    }



	    public void withdraw(double amount) {

	        if (account.withdraw(amount)) {

	            System.out.println("Please take your cash.");

	        } else {

	            System.out.println("Unable to process your request.");

	        }

	    }



	    public void deposit(double amount) {

	        account.deposit(amount);

	    }



	    public void checkBalance() {

	        System.out.println("Your current balance is: " + account.getBalance());

	    }

	    

	}

public class ClassBankAccount {

	    public static void main(String[] args) {

	        BankAccount userAccount = new BankAccount(1000); 

	        ATM atm = new ATM(userAccount);

	        Scanner scanner = new Scanner(System.in);



	        while (true) {

	            System.out.println("\nChoose an option:");

	            System.out.println("1. Withdraw");

	            System.out.println("2. Deposit");

	            System.out.println("3. Check Balance");

	            System.out.println("4. Exit");



	            int choice = scanner.nextInt();

	            double amount;



	            switch (choice) {

	                case 1:

	                    System.out.println("Enter amount to withdraw:");

	                    amount = scanner.nextDouble();

	                    atm.withdraw(amount);

	                    break;

	                case 2:

	                    System.out.println("Enter amount to deposit:");

	                    amount = scanner.nextDouble();

	                    atm.deposit(amount);

	                    break;

	                case 3:

	                    atm.checkBalance();

	                    break;

	                case 4:

	                    System.out.println("Exiting ATM. Thank you for using our service!");

	                    System.exit(0);

	                default:

	                    System.out.println("Invalid choice. Please choose again.");

	            }

	        }

	    }

	}
