import java.util.Scanner;
import java.util.StringTokenizer;


public class Controller2 {
	private Employee2[] e;
	private int counter = 0;
	private Scanner scanner = new Scanner(System.in);
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Controller2 c = new Controller2();
		c.getInput();
	}

	Controller2()
	{
		this.e = new Employee2[0];
	}
	
	void add()
	{
		this.e = ePlus(this.e);
		scanner = new Scanner(System.in);
		System.out.println("Please enter employeeId, lastName, firstName, department, jobTitle, and ssn:");
		StringTokenizer st = new StringTokenizer(scanner.nextLine());
		int employeeId = Integer.parseInt(st.nextToken());
		String lastName = st.nextToken();
		String firstName = st.nextToken();
		String department = st.nextToken();
		String jobTitle = st.nextToken();
		long ssn = Long.parseLong(st.nextToken());
		e[e.length - 1] = new Employee2(firstName, lastName, ssn, employeeId,
		  department, jobTitle);
	}
	
	void delete()
	{
		scanner = new Scanner(System.in);
		System.out.println("Index to delete?");
		this.e = eMinus(this.e, scanner.nextInt());
	}
	
	Employee2[] eMinus(Employee2[] e, int index)
	{
		Employee2[] e2 = new Employee2[e.length - 1];
		for (int loop = 0; loop < index; loop++)
		{
			e2[loop] = e[loop];
		}
		for (int loop = index; loop < e2.length; loop++)
		{
			e2[loop] = e[loop + 1];
		}
		return e2;
	}
	
	Employee2[] ePlus(Employee2[] e)
	{
		Employee2[] e2 = new Employee2[e.length + 1];
		for (int loop = 0; loop < e.length; loop++)
		{
			e2[loop] = e[loop];
		}
		return e2;
	}
	
	void exit()
	{
		System.out.println("Thank you for using our Employee Management Application!");
		System.exit(0);
	}
	
	void getInput()
	{
		while(true)
		{
			System.out.println("Please enter your input:");
			scanner = new Scanner(System.in);
			String input = scanner.nextLine();
			switch(input)
			{
			case "add": add(); break;
			case "delete": delete(); break;
			case "update field": updateField(); break;
			case "update employee": updateEmployee(); break;
			case "read": read(); break;
			case "exit": exit(); break;
			}
		}
	}
	
	void read()
	{
		for (int loop = 0; loop < e.length; loop++)
		{
			String s = loop + "\t" + e[loop].getEmployeeId() + "\t" + 
			  e[loop].getLastName() + "\t" + e[loop].getFirstName() +
			  "\t" + e[loop].getDepartment() + "\t "+ e[loop].getJobTitle() +
			  "\t" + e[loop].getSsn();
			System.out.println(s);
		}
	}
	
	void updateEmployee()
	{
		scanner = new Scanner(System.in);
		System.out.println("Index to update?");
		int index = scanner.nextInt();
		scanner = new Scanner(System.in);
		System.out.println("Please enter employeeId, lastName, firstName, department, jobTitle, and ssn:");
		StringTokenizer st = new StringTokenizer(scanner.nextLine());
		int employeeId = Integer.parseInt(st.nextToken());
		String lastName = st.nextToken();
		String firstName = st.nextToken();
		String department = st.nextToken();
		String jobTitle = st.nextToken();
		long ssn = Long.parseLong(st.nextToken());
		e[index] = new Employee2(firstName, lastName, ssn, employeeId,
		  department, jobTitle);
	}
	
	void updateField()
	{
		scanner = new Scanner(System.in);
		System.out.println("Update: department or jobTitle, old value, new value");
		StringTokenizer st = new StringTokenizer(scanner.nextLine());
		String input = st.nextToken();
		String oldValue = st.nextToken();
		String newValue = st.nextToken();
		
		for (int loop = 0; loop < e.length; loop++)
		{
			if(input.equals("department") &&
			  oldValue.equals(e[loop].getDepartment()))
			{
				e[loop].setDepartment(newValue);
			}
			else if(input.equals("jobTitle") &&
			  oldValue.equals(e[loop].getJobTitle()))
			{
				e[loop].setJobTitle(newValue);
			}
		}
	}
}

class Employee2
{
	private String lastName;
	private String firstName;
	private String department;
	private String jobTitle;
	private long ssn;
	private int employeeId;
	
	Employee2(String firstName, String lastName, long ssn, int employeeId)
	{
		this.department = "unknown";
		this.employeeId = employeeId;
		this.firstName = firstName;
		this.jobTitle = "unknown";
		this.lastName = lastName;
		this.ssn = ssn;
	}
	
	Employee2(String firstName, String lastName, long ssn, int employeeId,
		String department, String jobTitle)
	{
		this.department = department;
		this.employeeId = employeeId;
		this.firstName = firstName;
		this.jobTitle = jobTitle;
		this.lastName = lastName;
		this.ssn = ssn;
	}
	
	String getDepartment()
	{
		return this.department;
	}
	
	long getEmployeeId()
	{
		return this.employeeId;
	}
	
	String getFirstName()
	{
		return this.firstName;
	}
	
	String getJobTitle()
	{
		return this.jobTitle;
	}
	
	String getLastName()
	{
		return this.lastName;
	}
	
	long getSsn()
	{
		return this.ssn;
	}
	
	void setDepartment(String department)
	{
		this.department = department;
	}
	
	void setEmployeeId(int employeeId)
	{
		this.employeeId = employeeId;
	}
	
	void setFirstName(String firstName)
	{
		this.firstName = firstName;
	}
	
	void setJobTitle(String jobTitle)
	{
		this.jobTitle = jobTitle;
	}
	
	void setLastName(String lastName)
	{
		this.lastName = lastName;
	}
	
	void setSsn(long ssn)
	{
		this.ssn = ssn;
	}
}
