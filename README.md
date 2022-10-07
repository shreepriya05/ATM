# ATM
Java code for ATM operations  

import java.util.*;
public class Main {
	static List<customerDetails> detail=new ArrayList<>();
	static Scanner sc=new Scanner(System.in);
	static loadCash l1=new loadCash();
	public static void main(String[] args) {
		customerdetails();
		l1.upadate_cash(20, 100, 100);
		int choice;
		do {
			System.out.println("1.Load Cash to ATM");
			System.out.println("2.Balance in ATM");
			System.out.println("3.Details of the customer");
			System.out.println("4.Operations in ATM");
			System.out.println("Enter Choices to do Operation");
			choice=sc.nextInt();
			switch(choice) {
			case 1:
			    loadcash();
				break;
			case 2:
				displayatmdenomenation();
				break;
			case 3:
				displaydetails();
				break;
	 		case 4:
	 			atmoperation();
	 			break;
	 		case 5:
	 		   break;
	 		 default:
	 			 System.out.println("Enter correct choice");
	 			 
	 			 break;
			}
		}while(choice!=5);
		
	}

   static void atmoperation() {
		AtmOperations ao=new AtmOperations(); 
	}
	static void loadcash() {
		System.out.println("---Load to Cash---");
	    System.out.println("Enter note count--->");
	    System.out.println("Enter count_2000");
	    int _2000=sc.nextInt();
	    System.out.println("Enter count_500");
	    int _500=sc.nextInt();
	    System.out.println("Enter count_100");
	    int _100=sc.nextInt();
	    l1.upadate_cash(_2000,_500,_100);
	    displayatmdenomenation();
	}
	static void customerdetails() {
		customerDetails c1=new customerDetails(101,"Suresh",2343,25234);
		customerDetails c2=new customerDetails(102,"Ganesh",5432,34123);
		customerDetails c3=new customerDetails(103,"Magesh",7854,26100);
		customerDetails c4=new customerDetails(104,"Naresh",2345,80000);
		customerDetails c5=new customerDetails(105,"Harish",1907,103400);
        detail.addAll(Arrays.asList(c1,c2,c3,c4,c5));
	}
    static void displaydetails() {
    	System.out.println("---Customer Details---");
		System.out.printf("%8s %20s %12s %16s", "Acc No", "Account Holder", "Pin Number", "Account Balance");  
		System.out.println();    
		for(customerDetails customerdeatail: detail)  
		{  
		System.out.format("%7s %14s %14s %16s",customerdeatail.getAccNo(), customerdeatail.getAhName(), customerdeatail.getsPin(), customerdeatail.getBalance());  
		System.out.println();  
		}  
		System.out.print("\n");
	}
    static void displayatmdenomenation() {
    	System.out.println("---Atm Balance---"); 
		System.out.printf("%8s %12s %12s ", "Denomination", "Number", "Value");  
		System.out.println();  
		System.out.format("%7s %16s %12s ","2000", a12.getCount_2000(),a12.getTotal_2000());
		System.out.println();
		System.out.format("%7s %16s %12s ","500", a12.getCount_500(),a12.getTotal_500());  
		System.out.println();
		System.out.format("%7s %16s %12s ","100", a12.getCount_100(),a12.getTotal_100()); 
		System.out.println();
		System.out.print("\n");
    }
	
}
class loadCash extends Main{
   int count_2000=0;
   int count_500=0;
   int count_100=0;
   int total_2000=0;
   int total_500=0;
   int total_100=0;
   int atmbalance=0;
   
   public int getTotal_2000() {
	return total_2000;
}
public void setTotal_2000(int total_2000) {
	this.total_2000 = total_2000;
}
public int getTotal_500() {
	return total_500;
}
public void setTotal_500(int total_500) {
	this.total_500 = total_500;
}
public int getTotal_100() {
	return total_100;
}
public void setTotal_100(int total_100) {
	this.total_100 = total_100;
}
public int getAtmbalance() {
	return atmbalance;
}
public void setAtmbalance(int atmbalance) {
	this.atmbalance = atmbalance;
}
public int getCount_2000() {
	    return count_2000;
   }
   public void setCount_2000(int count_2000) {
        this.count_2000 = count_2000;
    }
   public int getCount_500() {
	   return count_500;
   }
   public void setCount_500(int count_500) {
	   this.count_500 = count_500;
    }
   public int getCount_100() {
	   return count_100;
    }
   public void setCount_100(int count_100) {
	   this.count_100 = count_100;
   }
   public void upadate_cash(int count_2000, int count_500, int count_100) {
	   this.count_2000+=count_2000;
	   this.count_500+=count_500;
	   this.count_100+=count_100;
	   total_2000=count_2000*2000;
	   total_500=count_500*500;
	   total_100=count_100*100;
       atmbalance=total_2000+total_500+total_100;	   
       return;
   }
   public boolean update_withdrawl(int amt,int _2000count,int _500count,int _100count) {
	   if(_2000count<=count_2000&&_500count<=count_500&&_100count<=count_100) {
		   count_2000-=_2000count;
		   count_500-=_500count;
		   count_100-=_100count;
		   total_2000-=_2000count*2000;
		   total_500-=_500count*500;
		   total_100-=_100count*100;
	       atmbalance-=amt;
		   return true;
	   }
	   return false;
   }   
}
import java.text.DateFormat.Field;
class customerDetails extends Main{
	int accNo;
	String AccName;
	int Pin;
	int Balance;
	public customerDetails(int accNo, String AccName, int Pin, int Balance) {
		super();
		this.accNo = accNo;
		this.AccName = AccName;
		this.Pin = Pin;
		this.Balance = Balance;
	}
	public int getAccNo() {
		return accNo;
	}
	public void setAccNo(int accNo) {
		this.accNo = accNo;
	}
	public String getAccName() {
		return AccName;
	}
	public void setAccName(String AccName) {
		this.AccName = AccName;
	}
	public int getPin() {
		return Pin;
	}
	public void setPin(int Pin) {
		this.Pin = Pin;
	}
	public int getBalance() {
		return Balance;
	}
	public void setBalance(int Balance) {
		this.Balance = Balance;
	}
	public void updateBalance(int amt) {
		Balance-=amt;
		return;
	}
	void customercashupdate(customerDetails obj,int amt,int _2000count,int _500count,int _100count) {
		if(amt<=obj.Balance) {
    		if(l1.update_withdrawl(amt,_2000count,_500count,_100count)) {
    		  obj.updatebalaance(amt);
    		} 
    		else {
    			System.out.println("Sorry Atm Balance Is Low");
    		}
    	}
    	else {
    		System.out.println("Sorry Your Account Balance Is Low");
    	}
		return;
	}
	public String toString() {
		return  accNo + AccName + Pin + Balance;
	}	
}
import java.util.Scanner;
import java.util.function.Predicate;

class AtmOperations extends Main{
	customerDetails cd;
	Scanner sc=new Scanner(System.in);
	public AtmOperations() {
	    System.out.println("1.Balance Checking");
	    System.out.println("2.Money withdrawl");
	    System.out.println("3.Money Transfer");
	    System.out.println("4.Check ATM balance");
	    System.out.println("5.Amount Deposit");
	    int choice=sc.nextInt();
	    switch(choice) {
	    case 1:
	    	checkbalance();
	    	break;
	    case 2:
	    	withdrawmoney();
	    	break;
	    case 3:
	    	transfermoney();
	    	break;
	    case 4:
	    	atmbalance();
	    	break;
	    case 5:
	    	DepositAmount();
	    	break;
	    }
	}
	void checkbalance() {
		System.out.println("Enter Secret Pin");
		int pin=sc.nextInt();
		for(customerDetails customerdeatail: detail)  
		{  
		if(customerdeatail.getsPin()==pin){
			System.out.println(customerdeatail.getBalance());  
		
		}  
		}  	
	}
	void withdrawmoney() {
		System.out.println("Enter Secret Pin");
		int pin=sc.nextInt();
		for(customerDetails customerdeatail: detail)  
		{  
		if(customerdeatail.getsPin()==pin){
			cd=customerdeatail;
			int amt;
			int flag=1;
		    do {
		     System.out.println("Enter Amount Multiples by 100 and less than 10000:");
			 amt=sc.nextInt();
			 if(amt>=100&&amt<=10000 && amt%100==0) {
				 flag=0;
			 }
		    }while(flag!=0);
			int _2000count=0,_500count=0,_100count=0;
			int amt_copy=amt;
			while(amt>=100)
			{	if(amt>=2000) {
					_2000count++;
					amt-=2000;
				}
				else if(amt>=500&&amt<2000) {
					_500count++;
					amt-=500;
				}
				else if(amt>=100&&amt<500) {
			            _100count++;
			            amt-=100;
				}
		   }
	customerdeatail.customercashupdate(cd,amt_copy, _2000count,_500count ,_100count);	 
		}		   
		}  	
	}
	void transfermoney() {
		System.out.println("Enter pin");
		int pin=sc.nextInt();
		for(customerDetails customerdeatail: detail)  
		{  
		if(customerdeatail.getsPin()==pin){
			customerDetails obj1=customerdeatail;
			 moneyupdate(obj1);
		}
		}  		
	}
	void  moneyupdate(customerDetails obj) {
		System.out.println("Enter Account Holder Name:");
		String s=sc.next();
		System.out.println("Enter account number to transfer:");
		int accno=sc.nextInt();
		for(customerDetails customerdeatail1: detail)  
		{  
		if(customerdeatail1.getAccNo()==accno){
		int amt;
	    do {
	     System.out.println("Enter Amount less than 10000:");
		 amt=sc.nextInt();
	    }while(amt>10000);
	    
	    if(obj.balance>=amt) {
	    	obj.balance-=amt;
	    	customerdeatail1.balance+=amt;
	    	System.out.println("Amount transfered successfully!");
	    }
		}
		}
	}
	void atmbalance() {
		displayatmdenomenation();		
	}
	void DepositAmount() {
		System.out.println("Enter pin");
		int pin=sc.nextInt();
		for(customerDetails customerdeatail: detail)  
		{  
		if(customerdeatail.getsPin()==pin){
			System.out.println("Enter Amount to Deposit:");
			int amount=sc.nextInt();
			customerdeatail.balance+=amount;
		}
		}  		
	}
	

}

