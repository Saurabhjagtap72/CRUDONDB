# CRUDONDB

package crud;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.util.Scanner;

public class CRUD{

	public static void main(String[] args) throws ClassNotFoundException, SQLException 
	{

		Class.forName("com.mysql.cj.jdbc.Driver");
		Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3306/players","root", "Saurabh@123");
		
		Scanner sc = new Scanner(System.in);
		
		
		System.out.print("Enter Choice : "+"  ");
		System.out.print("1.Insert data"+"  ");
		System.out.print("2.Update data"+"  ");
		System.out.print("3.Delete data"+"   ");
		System.out.println("4.Fetch data "+"   ");
		System.out.println("5.Test Data "+ "  ");


		
		System.out.println("Enter the Choise : ");
		int choise = sc.nextInt();
		switch (choise)
		{
		
		     case 1:
		           {
			            System.out.println("Insert the data ");
			            
			            
			            PreparedStatement ps =  con.prepareStatement("insert into india(Pname,Pid,Psatate) values(?,?,?)");

			    		Scanner scn = new Scanner(System.in);
			    		
			    		System.out.println("Enter Pname :");
			    		String Pname  = scn.next();
			    		
			    		System.out.println("Enter Pid : ");
			    		int Pid = scn.nextInt();
			    		
			    		System.out.println("Enter the PState : ");
			    		String Psatate = scn.next();
			    		
			    		ps.setString(1, Pname);
			    		ps.setInt(2, Pid);
			    		ps.setString(3, Psatate);
			    		
			    		
			     		ps.execute();
			     		
			     		System.out.println("Values are Inserted ");
			     		break;
		           }
		           
		     case 2:
		     {
		    	 System.out.println("Update Data");
		    	
		    	 
		    	 PreparedStatement ps  = con.prepareStatement("update india  set Pname=? where Pid =?");
		    	 
		    	 Scanner scn =  new Scanner(System.in);
		    	 
		    	 System.out.println("Enter Pname :");
		    	 String Pname  = scn.next();
		    	 
		    	 
		    	 System.out.println("Enter Pid : ");
		    	 int Pid = scn.nextInt();

		    	 ps.setString(1, Pname);
		    	 ps.setInt(2, Pid);
		    	 
		         ps.execute();
		         
		         
		         System.out.println("Data Udated ");
		    	 break;
		     }
		     
		     case 3:
		     {
		    	 System.out.println("Delete Data");
		    	 
		    	 
		    	 PreparedStatement ps = con.prepareStatement("delete from india where Pid  = ?");
		    	 Scanner scn  = new Scanner(System.in);
		    	 System.out.println("Enter the Pid : ");
		    	 int Pid  = scn.nextInt();
		    	 
		    	 ps.setInt(1, Pid);
		    	 
		    	 ps.execute();
		    	 
		    	 
		    	 System.out.println("Data Deleted ");
		    	 break;
		     }
		     
		     case 4:
		     {
		    	 System.out.println("Fetch the Data ");
		    	 
		    	 PreparedStatement ps = con.prepareStatement("select * from india where Pid = ?");
		    	 
		    	 Scanner scn = new Scanner(System.in);
		    	 int Pid  = scn.nextInt();
		    	 
		    	 ps.setInt(1,Pid);
		    	 ps.execute();
		    	 
		    	 System.out.println(" Data Fetch Successfully");
		    	 
		    	 break;
		    	 
		     }
		     
		     
		     case 5:
		     {
                 System.out.println("Fetch the Data ");
		    	 
		    	 PreparedStatement ps = con.prepareStatement("select * from india where Pid = ?");
		    	 
		    	 Scanner scn = new Scanner(System.in);
		    	 int Pid  = scn.nextInt();
		    	 
		    	 ps.setInt(1,Pid);
		    	 ps.execute();
		    	 
		    	 System.out.println(" Data Fetch Successfully");
		    	 
		    	 break;
		    	 
		     }
		     
		     
		     
		     
		
		}
	}

}
