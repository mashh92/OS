1.1
//Write a Java program to display all the alphabets between ‘A’ to ‘Z’ after every 2
seconds.

public class Main extends Thread {
	char c;
	public void run() {
		for (c = 'A'; c <= 'Z'; c++) {
			System.out.println("" + c);
			try
			{
				Thread.sleep(2000);
			} catch (Exception e) {
				e.printStackTrace();
			}
		}
	}

	public static void main(String args[]) {
		Main t = new Main();
		t.start();
	}
}

1.2
//Write a Java program to accept the details of Employee (Eno, EName, Designation,
Salary) from a user and store it into the database. (Use Swing)

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.sql.*;

class one extends JFrame implements ActionListener {

	JFrame f;
	JLabel l1, l2, l3, l4;
	JTextField t1, t2, t3, t4;
	JButton b1, b2;

	one() {
		f = new JFrame("Main");
		l1 = new JLabel("Eno");
		l2 = new JLabel("EName");
		l3 = new JLabel("Designation");
		l4 = new JLabel("Salary");
		
		t1 = new JTextField(15);
		t2 = new JTextField(15);
		t3 = new JTextField(15);
		t4 = new JTextField(15);
		b1 = new JButton("Insert ");
		b2 = new JButton("clear ");
		f.setLayout(new GridLayout(5,2));
		f.setVisible(true);
		f.setSize(300, 300);
		b1.addActionListener(this);
		b2.addActionListener(this);
		f.add(l1);
		f.add(t1);
		f.add(l2);
		f.add(t2);
		f.add(l3);
		f.add(t3);
		f.add(l4);
		f.add(t4);
		f.add(b1);
		f.add(b2);
	}

	public void actionPerformed(ActionEvent e) {
		if (e.getSource() == b1) {
			try {
				Class.forName("com.mysql.cj.jdbc.Driver");
				Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
				Statement stmt = con.createStatement();

				String name = t2.getText();
				int eno = Integer.parseInt(t1.getText());
				String des = t3.getText();
				double sal = Double.parseDouble(t4.getText());
				String sql = "insert into emp values(";
				sql = sql + eno + ",'" + name + "','" + des + "'," + sal + ")";
				System.out.println(sql);
				int i = stmt.executeUpdate(sql);
				if (i > 0) {
					System.out.println("record added ");
				}
				con.close();
			} // try close
			catch (Exception a) {
				System.out.println("Couldn't!" + a);
			}
		}

		if (e.getSource() == b2) {
			t1.setText("");
			t2.setText("");
			t3.setText("");
			t4.setText("");
		}
	}
}

class Main {
	public static void main(String args[]) {
		new one();
	}
}

2.1
//Write a java program to read ‘N’ names of your friends, store it into HashSet and display them in ascending order. 

import java.util.*;

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		System.out.print("Enter the number of friends: ");
		int n = sc.nextInt();
		Set<String> friends = new HashSet<>();
		for (int i = 1; i <= n; i++) {
			System.out.print("Enter name " + i + ": ");
			String name = sc.next();
			friends.add(name);
		}
		List<String> sortedFriends = new ArrayList<>(friends);
		Collections.sort(sortedFriends);
		System.out.println("\nList of friends in ascending order:");
		for (String friend : sortedFriends) {
			System.out.println(friend);
		}
		sc.close();
	}
}

2.2
//Design a servlet that provides information about a HTTP request from a client, such as IP-Address and browser type. The servlet also provides information about the server on which the servlet is running, such as the operating system type, and the names of currently loaded servlets.

import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class Main extends HttpServlet implements Servlet {
	protected void doGet(HttpServletRequest req, HttpServletResponse res) throws IOException, ServletException {
		res.setContentType("text/html");
		PrintWriter pw = res.getWriter();
		pw.println("<html><body><h2>Information about Http Request</h2>");
		pw.println("<br>Server Name: " + req.getServerName());
		pw.println("<br>Server Port: " + req.getServerPort());
		pw.println("<br>Ip Address: " + req.getRemoteAddr());
		pw.println("<br>Server Path: " + req.getServerPath());
		pw.println("<br>Client Browser: " + req.getHeader("User-Agent"));
		pw.println("</body></html>");
		pw.close();
	}
}

//web.xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<web-app>
<servlet>
<servlet-name>serverInfo</servlet-name>
<servlet-class>ServerInfo</servlet-class>
</servlet>
<servlet-mapping>
<servlet-name>serverInfo</servlet-name>
<url-pattern>/server</url-pattern>
</servlet-mapping>
</web-app>

3.1
//Write a JSP program to display the details of Patient (PNo, PName, Address, age, disease) in tabular form on browser.

<%@page contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<body>
	<%@ page import="java.sql.*;"%>
	<%!int pno, age;
	String pname, paddress, disease;%>
	<%
	try {
		Class.forName("com.mysql.cj.jdbc.Driver");

		Connection cn = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
		Statement st = cn.createStatement();
		ResultSet rs = st.executeQuery("select * from Patient");
	%>
	<table border="1">
		<tr>
			<td>Patient No</td>
			<td>Patient Name</td>
			<td>Patient Address</td>
			<td>Age</td>
			<td>Disease</td>
		</tr>
		<%
		while (rs.next()) {
		%>
		<tr>
			<td><%=rs.getInt("pno")%></td>
			<td><%=rs.getString("pname")%></td>
			<td><%=rs.getString("address")%></td>
			<td><%=rs.getInt("age")%></td>
			<td><%=rs.getString("disease")%></td>
		</tr>
		<%
		}
		cn.close();
		} catch (Exception e) {
		out.println(e);
		}
		%>
	</table>
</body>
</html>

3.2
//Write a Java program to create LinkedList of String objects and perform the following:

import java.util.*;
class Main{
	
	static void reverseLL(int n, LinkedList<String> ll) {
		LinkedList<String> ll1 = new LinkedList<String>();
		ll1.addAll(ll);
		System.out.println("Linked list in reverse order is: ");
		while(!ll1.isEmpty()){
			System.out.print(ll1.getLast() + " ");
			ll1.removeLast();
		}
		System.out.println();
	}
	
	public static void main(String[] args) {
		int choice = 0, n = 0;
		Scanner sc = new Scanner(System.in);
		String name = "";
		LinkedList<String> ll = new LinkedList<String>();
		
		while(choice != 5) {
			System.out.println("1. Add element at the end of the list. 2. Delete first element of the list. 3. Display in reverse. 4 Display Linked List. 5"
					+ ". Exit");
			System.out.print("Enter choice: ");
			choice = sc.nextInt();
			switch(choice) {
			case 1:
				System.out.print("Enter element name: ");
				name = sc.next();
				ll.addLast(name);
				n++;
				break;
			case 2:
				ll.removeFirst();
				n--;
				break;
			case 3:
				reverseLL(n, ll);
				break;
			case 4:
				System.out.println(ll);
				break;
			case 5:
				System.exit(0);
			}
		}
	}
}

4.1
//Write a Java program using Runnable interface to blink Text on the frame.

import java.awt.*;

public class Main extends Frame implements Runnable {
	Thread t;
	Label l1;
	int f;

	public Main() {
		t = new Thread(this);
		t.start();
		setLayout(null);
		l1 = new Label("Hello JAVA");
		l1.setBounds(100, 100, 100, 40);
		add(l1);
		setSize(300, 300);
		setVisible(true);
		f = 0;
	}

	public void run() {
		try {
			if (f == 0) {
				t.sleep(200);
				l1.setText("");
				f = 1;
			}
			if (f == 1) {
				t.sleep(200);
				l1.setText("Hello Java");
				f = 0;
			}
		} catch (Exception e) {
			System.out.println(e);
		}
		run();
	}

	public static void main(String args[]) {
		new Main();
	}
}

4.2
//Write a Java program to store city names and their STD codes using an appropriate
collection and perform following operations:

import java.util.*;

class Main{
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int choice = 0, code;
		String city;
		HashMap<String, Integer> hm = new HashMap<String, Integer>();
		
		while(choice != 4) {
			System.out.println("1. Add a new city. 2. Remove a city. 3. Search for a city. 4. Exit");
			System.out.print("Enter choice: ");
			choice = sc.nextInt();
			switch(choice) {
			case 1:
				System.out.print("Enter city name: ");
				city = sc.next();
				System.out.print("Enter city stdcode: ");
				code = sc.nextInt();
				if(hm.containsKey(city)) {
					System.out.println("Already exist!");
				}
				else
					hm.put(city, code);
				break;
			
			case 2:
				System.out.print("Enter city name: ");
				city = sc.next();
				hm.remove(city);
				break;
			case 3:
				System.out.print("Enter city name: ");
				city = sc.next();
				if(hm.containsKey(city)) {
					System.out.println(hm.get(city));
				}
				else
					System.out.println("City doesn't exist!");
				break;
			case 4:
				System.exit(0);
			}
		}
	}
}

5.1
//Write a Java Program to create the hash table that will maintain the mobile number and student name. Display the details of student using Enumeration interface.

import java.util.*;
class Main{
	public static void main(String[] args) {
		 Hashtable<String, Integer> ht = new Hashtable<String, Integer>(); 

     ht.put("aaa", 123456789); 
     ht.put("bbb", 456789123); 
     ht.put("ccc", 987654321); 
     
     Enumeration e = ht.elements(); 
     while (e.hasMoreElements()) { 
         System.out.println(e.nextElement()); 
     } 
     
	}
}


5.2
//Create a JSP page for an online multiple choice test. The questions are randomly selected
from a database and displayed on the screen.
<html>
<body>
	<%
	out.println("Your Score.: " + session.getAttribute("score"));
	session.invalidate();
	%>
</body>
</html>


<html>
<head>
<title>Online Test</title>
</head>
<body>

	<%@ page import="java.sql.*"%>
	<%@ page import="javax.sql.*"%>

	<%!Integer score = 0;%>

	<%
	Class.forName("com.mysql.jdbc.Driver");
	java.sql.Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
	Statement st = con.createStatement();
	ResultSet rs = st.executeQuery("SELECT * FROM test ORDER BY RAND() LIMIT 1");

	if (session.isNew()) {
		session.setAttribute("score", score);
	}

	else {
		Integer total = 0;
		total = (Integer) session.getAttribute("score");
		total = total + 1;

		String choice = new String(request.getParameter("cha"));
		String ans = new String(request.getParameter("ans"));

		if (choice.equals(ans))
			session.setAttribute("score", total);

	}

	out.println("<form action=\"test.jsp\">");
	while (rs.next()) {
		out.println("\t" + rs.getString(2));
		out.println("<br>" + "<input type=\"radio\" name=\"cha\" value=\"" + rs.getString(3) + "\">" + rs.getString(3));
		out.println("<br>" + "<input type=\"radio\" name=\"cha\" value=\"" + rs.getString(4) + "\">" + rs.getString(4));
		out.println("<br>" + "<input type=\"radio\" name=\"cha\" value=\"" + rs.getString(5) + "\">" + rs.getString(5));
		out.println("<br>" + "<input type=\"radio\" name=\"cha\" value=\"" + rs.getString(6) + "\">" + rs.getString(6));
		out.println("<br>" + "<input type= \"hidden\" name=\"ans\" value=\"" + rs.getString(7) + "\">");
		out.println("<br>" + "<input type=\"submit\" value=\"Next\" name=\"next\">");
	}
	out.println("</form>");

	out.println("<form action=\"submit.jsp\">");
	out.println("<br>" + "<input type=\"submit\" value=\"Submit\" name=\"submit\" >");
	out.println("</form>");
	%>

</body>
</html>

6.1
//Write a Java program to accept ‘n’ integers from the user and store them in a collection. Display them in the sorted order. The collection should not accept duplicate elements.(Use a suitable collection). Search for a particular element using predefined search
method in the Collection framework.

import java.util.*;
class Main {
	public static void main(String[] args) throws Exception {
		int no, element, i;
		Scanner sc = new Scanner(System.in);
		TreeSet<Integer> ts = new TreeSet<Integer>();
		System.out.print("Enter how many elements: ");
		no = sc.nextInt();
		for (i = 0; i < no; i++) {
			System.out.print("Enter the element: ");
			element = sc.nextInt();
			ts.add(element);
		}

		System.out.println("The elements in sorted order : " + ts);
		System.out.print("Enter element to be serach : ");
		element = sc.nextInt();
		if (ts.contains(element))
			System.out.println("Element is found");
		else
			System.out.println("Element NOT found");
	}
}

6.2
//Write a java program to simulate traffic signal using threads.

import java.util.*;

public class Main implements Runnable {
	public enum Color {
		RED, ORANGE, GREEN
	}

	private List<Color> light = Arrays.asList(Color.GREEN, Color.ORANGE, Color.RED);

	private static volatile int counter = 0;
	private int i;

	private static final Object lock = new Object();

	public Main(Color color) {
		this.i = light.indexOf(color);
	}

	@Override
	public void run() {
		try {
			synchronized (lock) {
				while (true) {
					while (counter % light.size() != i)
						lock.wait();
					System.out.println(Thread.currentThread().getName() + " :: " + light.get(counter % light.size()));
					counter++;
					Thread.sleep(1000);
					lock.notifyAll();
				}
			}
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
	}

	public static void main(String[] args) {
		new Thread(new Main(Main.Color.GREEN)).start();
		new Thread(new Main(Main.Color.ORANGE)).start();
		new Thread(new Main(Main.Color.RED)).start();
	}
}

7.1
//Write a java program that implements a multi-thread application that has three threads. First thread generates random integer number after every one second, if the number is even; second thread computes the square of that number and print it. If the number is odd, the third thread computes the of cube of that number and print it.

import java.util.*;
class FirstThread extends Thread {
	Random r = new Random();
	public int n;

	public void run() {
		try {
			for (int i = 0; i < 5; i++) {
				n = r.nextInt(10);
				System.out.println("Genrated Random number" + n);
				if (n % 2 == 0) {
					SecondThread t2 = new SecondThread(n);
					t2.start();
				} else {
					ThirdThread t3 = new ThirdThread(n);
					t3.start();
				}
				sleep(100);
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}

class SecondThread extends Thread {
	int square;

	SecondThread(int n) {
		square = n * n;
	}

	public void run() {
		try {
			System.out.println("Square of no: " + square);
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}

class ThirdThread extends Thread {
	int cube;

	ThirdThread(int n) {
		cube = n * n * n;
	}

	public void run() {
		try {
			System.out.println("cube of no" + cube);
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}

public class Main {
	public static void main(String[] args) {
		FirstThread t1 = new FirstThread();
		t1.start();
	}
}

7.2
//Write a java program for the following:
i. To create a Product(Pid, Pname, Price) table.
ii. Insert at least five records into the table.
iii. Display all the records from a table. 

import java.sql.*;
import java.util.*;

class Main {
	static Connection cn;
	static Statement st;
	static ResultSet rs;
	static Scanner sc = new Scanner(System.in);

	public static void display() throws SQLException {
		rs = st.executeQuery("select * from Product");

		System.out.println("|| Product id || Name || Price ||");
		while (rs.next()) {
			System.out.println("||     " + rs.getInt("pid") + "      || " + rs.getString("pname") + "  ||   "
					+ rs.getString("price") + "     ||");
		}
	}

	public static void insert() throws SQLException {
		PreparedStatement ps = cn.prepareStatement("Insert into product values(?,?,?);");
		int pid;
		String name, price;

		System.out.println("Enter the product ID: ");
		pid = sc.nextInt();
		System.out.println("Enter the product name: ");
		name = sc.next();
		System.out.println("Enter the product price: ");
		price = sc.next();
		ps.setInt(1, pid);
		ps.setString(2, name);
		ps.setString(3, price);
		ps.executeUpdate();
	}

	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		Class.forName("com.mysql.cj.jdbc.Driver");
		cn = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
		st = cn.createStatement();
		int choice = 0;

		while (choice != 3) {
			System.out.println("1. Insert. 2. Display. 3. Exit.");
			System.out.print("Enter choice: ");
			choice = sc.nextInt();
			switch (choice) {
			case 1:
				insert();
				break;
			case 2:
				display();
				break;
			case 3:
				System.exit(0);
			}
		}
	}
}

8.1
//Write a java program to define a thread for printing text on output screen for ‘n’ number of times. Create 3 threads and run them. Pass the text ‘n’ parameters to the thread constructor.

public class Main extends Thread {
	String str;
	int n;

	Main(String str,int n)
  {
    this.str=str;
    this.n=n;
  }

	public void run() {
		try {
			for (int i = 0; i < n; i++) {
				System.out.println(getName() + ":" + str);
			}
		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	public static void main(String[] args) {
		Main t1 = new Main("COVID19", 10);
		Main t2 = new Main("LOCKDOWN2020", 20);
		Main t3 = new Main("VACCINATED2021", 30);

		t1.run();
		t2.run();
		t3.run();
	}
}

8.2
//Write a JSP program to check whether a given number is prime or not. Display the result
in red color.

//Main.html
<!DOCTYPE html>
<html>
<body>

	<form action="Main.jsp" method="post">
		Enter Number : <input type="text" name="num"> 
		<input type="submit" value="Submit">
	</form>

</body>
</html>

//Main.jsp
<%@page contentType="text/html" pageEncoding="UTF-8"%>
<%
int n = Integer.parseInt(request.getParameter("num"));
int m = n / 2;
int flag = 0;
for (int i = 2; i <= m; i++) {
	if (n % i == 0) {
		flag = 1;
		break;
	}
}
if (flag == 0) {
%>
<html>
<body>
	<font size="14" color="red"> <%
 out.println("\tIt is prime " + n);
 %>
	</font>

</body>
</html>
<%
} else {
%>
<html>
<body>
	<font size="14" color="red"> <%
 out.println("\tIt is not prime " + n);
 %>
	</font>

</body>
</html>
<%
}
%>

9.1
//Write a Java program to create a thread for moving a ball inside a panel vertically. The ball should be created when the user clicks on the start button.

import java.awt.*;
import javax.swing.*;

class Main extends JFrame implements Runnable {
	Thread t;
	int x, y;

	Main() {
		super();
		t = new Thread(this);
		x = 10;
		y = 10;
		t.start();
		setSize(1000, 1000);
		setVisible(true);
		setTitle("BOUNCING BALL WINDOW");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
	}

	public void run() {
		try {
			while (true) {
				x += 10;
				y += 10;
				repaint();
				Thread.sleep(1000);
			}
		} catch (Exception e) {

		}
	}

	public void paint(Graphics g) {

		g.drawOval(x, y, 40, 40);

	}

	public static void main(String a[]) throws Exception {
		Main t = new Main();
		Thread.sleep(1000);
	}
}

9.2
//Write a Java program using Spring to display the message “If you can't explain it
simply, you don't understand it well enough”. 

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
	@GetMapping
	public String hello() {
		return "If you can't explain it simply, you don't understand it well enough";
	}
}

10.1
//Write a Java program to display the Current Date using spring. 

import java.util.Date;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
	@GetMapping
	public String hello() {
		Date current_Date = new Date();
		return current_Date.toString();
	}
}

10.2
//Write a Java program to display first record from student table (RNo, SName, Per) onto
the TextFields by clicking on button. (Assume Student table is already created)

import java.awt.*;
import java.awt.event.*;
import java.sql.*;
import javax.swing.*;

class Main implements ActionListener{
	JTextField t1, t2, t3;
	JButton b1;
	JFrame f;
	String rno, name, per;
	
	Main() throws SQLException, ClassNotFoundException{
		Class.forName("com.mysql.cj.jdbc.Driver");
		Connection cn = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
		Statement st = cn.createStatement();
		ResultSet rs = st.executeQuery("select * from Student;");
		b1 = new JButton("Click here to fetch");
		t1 = new JTextField();
		t2 = new JTextField();
		t3 = new JTextField();
		f = new JFrame();
		b1.addActionListener(this);
		
		rs.next();
		rno = rs.getString(1);
		name = rs.getString(2);
		per = rs.getString(3);
		f.add(t1);
		f.add(t2);
		f.add(t3);
		f.add(b1);
		
		f.setLayout(new GridLayout(4,1));
		f.setVisible(true);
		f.setSize(500,500);
	}

	@Override
	public void actionPerformed(ActionEvent e) {
		t1.setText(rno);
		t2.setText(name);
		t3.setText(per);
	}
	
	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		new Main();
	}
}

11.1
//Design an HTML page which passes customer number to a search servlet. The servlet searches for the customer number in a database (customer table) and returns customer details if found the number otherwise display error message. 

//html file
<!DOCTYPE html>
<html>
<body>

	<form action="servlet/Main.java" method="GET">  
	Enter Customer number: <input type="text" name="cno"/><br/>  
	<input type="submit" value="search"/> 
	</form>

</body>
</html>

//Main.java servlet
package servlet;
import java.io.*;
import java.sql.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class Main extends HttpServlet implements Servlet {

	protected void doGet(HttpServletRequest req, HttpServletResponse res) throws IOException, ServletException {
		res.setContentType("text/html");
		PrintWriter out = res.getWriter();
		String cno = req.getParameter("cno");
		int cno1 = Integer.valueOf(cno);

		try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");

			PreparedStatement ps = con.prepareStatement("select * from customer where cno=?");
			ps.setInt(1, cno1);

			out.print("<table width=50% border=1>");
			out.print("<caption>Customer info:</caption>");

			ResultSet rs = ps.executeQuery();

			/* Printing column names */
			ResultSetMetaData rsmd = rs.getMetaData();
			int total = rsmd.getColumnCount();
			out.print("<tr>");
			for (int i = 1; i <= total; i++) {
				out.print("<th>" + rsmd.getColumnName(i) + "</th>");
			}

			out.print("</tr>");

			/* Printing result */

			while (rs.next()) {
				out.print("<tr><td>" + rs.getInt(1) + "</td><td>" + rs.getString(2) + "</td><td>" + rs.getString(3)
						+ "</td><td>" + rs.getString(4) + "</td></tr>");

			}

			out.print("</table>");

		} catch (Exception e2) {
			e2.printStackTrace();
		}

		finally {
			out.close();
		}

	}
}


11.2
//Write a Java program to display information about all columns in the DONAR table
using ResultSetMetaData. 

import java.sql.*;

class Main{
	public static void main(String args[]) {
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");

			PreparedStatement ps = con.prepareStatement("select * from donar");
			ResultSet rs = ps.executeQuery();
			ResultSetMetaData rsmd = rs.getMetaData();
			int col = rsmd.getColumnCount();

			System.out.println("Total columns: " + col);
			
			for(int i=1;i<=col;i++) {
				System.out.println("Column Name of column " + i + ": " + rsmd.getColumnName(i));
				System.out.println("Column Type Name of column " + i + ": " + rsmd.getColumnTypeName(i));
			}
			con.close();
		} catch (Exception e) {
			System.out.println(e);
		}
	}
}

12.1
//Write a JSP program to check whether given number is Perfect or not. (Use Include directive). 

//Html file
<!DOCTYPE html>
<html>
<head>
<title>PERFECT NUMBER</title>
</head>
<body>
	<form action="Main.jsp" method="post">
		Enter Number : <input type="text" name="num"> <input type="submit" value="Submit" name="s1">
	</form>
</body>
</html>

//jsp file
<%@ page import="java.util.*" %>

<%
if(request.getParameter("s1")!=null)
  {
	Integer num,a,i,sum = 0;
	num = Integer.parseInt(request.getParameter("num"));
	a = num;
	for(i=1;i<a;i++)
	{
		if(a%i==0)
		{
			sum=sum + i;
		}
	}
	if(sum==a)
	{
		out.println(num+ " is a perfect number");
	}
	else
	{
		out.println(num+ " is not a perfect number");
	}
  }	
%>

12.2
//Write a Java Program to create a PROJECT table with field’s project_id, Project_name,
Project_description, Project_Status. Insert values in the table. Display all the details of
the PROJECT table in a tabular format on the screen.(using swing).

import java.sql.*;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.table.*;

class Main extends JFrame implements ActionListener {

    Connection con;
    ResultSet rs;
    Statement st;

    static JTable table;
    String[] columnNames = { "p_id", "p_name", "p_description", "p_status" };
    JFrame frm;
    JPanel p1;
    String p_id = "", p_name = "", p_description = "", p_status = "";
    JTextField txtid, txtname, txtdesc, textstatus;
    JButton Insert, Display, Exit;
    Insert iobj;

    Main() {
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setTitle("PROJECT INFO");

        p1 = new JPanel();
        p1.setLayout(new GridLayout(3, 3, 30, 30));
        Insert = new JButton("Insert");
        p1.add(Insert);
        Display = new JButton("Display");
        p1.add(Display);
        Exit = new JButton("Exit");
        p1.add(Exit);
        Insert.addActionListener(this);
        Display.addActionListener(this);
        Exit.addActionListener(this);
        add(p1, BorderLayout.CENTER);
        setVisible(true);
        setSize(600, 600);
    }

    public void actionPerformed(ActionEvent ae) {
        if (ae.getSource() == Display) {
            frm = new JFrame("DISPLAY");
            setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
            setLayout(new BorderLayout());
            DefaultTableModel model = new DefaultTableModel();
            model.setColumnIdentifiers(columnNames);
            table = new JTable();
            table.setModel(model);
            table.setAutoResizeMode(JTable.AUTO_RESIZE_ALL_COLUMNS);
            table.setFillsViewportHeight(true);
            JScrollPane scroll = new JScrollPane(table);
            scroll.setHorizontalScrollBarPolicy(JScrollPane.HORIZONTAL_SCROLLBAR_AS_NEEDED);
            scroll.setVerticalScrollBarPolicy(JScrollPane.VERTICAL_SCROLLBAR_AS_NEEDED);
            try {
            	Class.forName("com.mysql.cj.jdbc.Driver");
        		con = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
                st = con.createStatement();
                rs = st.executeQuery("select * from project");
                while (rs.next()) {
                    p_id = rs.getString(1);
                    p_name = rs.getString(2);
                    p_description = rs.getString(3);
                    p_status = rs.getString(4);
                    model.addRow(new Object[] { p_id, p_name, p_description, p_status });
                }
                frm.add(scroll);
                frm.setVisible(true);
                frm.setSize(400, 400);
            }
            catch (Exception e) {
                JOptionPane.showMessageDialog(null, e, "Error", JOptionPane.ERROR_MESSAGE);
            }
        }
        if (ae.getSource() == Insert) {
            iobj = new Insert();
        }
        if (ae.getSource() == Exit) {
            System.exit(1);
        }
    }
    public static void main(String arg[]) {
        new Main();
    }
}

class Insert extends JFrame implements ActionListener {
    JTextField txtst, txtpid, txtpname, txtdsc;
    JButton btnadd, btnclear;
    Insert() {
        setTitle("Project Record Inserts");
        setSize(400, 500);
        setVisible(true);
        setLayout(new GridLayout(6, 2, 40, 40));
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);

        JLabel id = new JLabel("Enter Project Id: ");
        add(id);
        txtpid = new JTextField(10);
        add(txtpid);
        JLabel name = new JLabel("Enter Project Name: ");
        add(name);
        txtpname = new JTextField(10);
        add(txtpname);
        JLabel dsc = new JLabel("Enter Project Description: ");
        add(dsc);
        txtdsc = new JTextField(10);
        add(txtdsc);
        JLabel st = new JLabel("Enter Project Status: ");
        add(st);
        txtst = new JTextField(10);
        add(txtst);
        btnadd = new JButton("Insert");
        add(btnadd);
        btnadd.addActionListener(this);
        btnclear = new JButton("Cancel");
        add(btnclear);
        btnclear.addActionListener(this);
    }
    public void actionPerformed(ActionEvent ae) {
        int p_id = Integer.parseInt(txtpid.getText());
        String pname = (txtpname.getText());
        String ds = (txtdsc.getText());
        String st = (txtst.getText());
        Connection conn = null;
        PreparedStatement pstmt = null;
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
            if (ae.getSource() == btnadd) {
                pstmt = conn.prepareStatement("insert into project values(?,?,?,?)");
                pstmt.setInt(1, p_id);
                pstmt.setString(2, pname);
                pstmt.setString(3, ds);
                pstmt.setString(4, st);
                int result = pstmt.executeUpdate();
                if (result == 1) {
                    JOptionPane.showMessageDialog(null, "Succesfully Inserted", st, JOptionPane.INFORMATION_MESSAGE);
                }
                pstmt.close();
                conn.close();
            }
            if (ae.getSource() == btnclear) {
                txtpid.setText("");
                txtdsc.setText("");
                txtpname.setText("");
                txtst.setText("");
            }
        }
        catch (Exception e) {
            JOptionPane.showMessageDialog(null, e, "ERROR OCCURED", JOptionPane.ERROR_MESSAGE);
            System.out.println(e);
        }
    }
}

13.1
//Write a Java program to display information about the database and list all the tables in the database. (Use DatabaseMetaData). 

import java.sql.*;
public class Main {
   public static void main(String[] args) throws SQLException, ClassNotFoundException {
      Connection conn = null;
      Class.forName("com.mysql.jdbc.Driver");
      conn = (Connection) DriverManager.getConnection("jdbc:mysql://localhost/student", "root", "student");
      ResultSet rs = null;
      DatabaseMetaData meta = (DatabaseMetaData) conn.getMetaData();
      rs = meta.getTables(null, null, null, new String[] {
         "TABLE"
      });
      int count = 0;
      System.out.println("All table names in database are ");
      while (rs.next()) {
         String tblName = rs.getString("TABLE_NAME");
         System.out.println(tblName);
         count++;
      }
      System.out.println(count + " tables founds");
   }
}

13.2
//Write a Java program to show lifecycle (creation, sleep, and dead) of a thread. Program
should print randomly the name of thread and value of sleep time. The name of the
thread should be hard coded through constructor. The sleep time of a thread will be a
random integer in the range 0 to 4999. 

class MyThread extends Thread {
	public MyThread(String s) {
		super(s);
	}

	public void run() {
		System.out.println(getName() + "thread created.");
		while (true) {
			System.out.println(this);
			int s = (int) (Math.random() * 5000);
			System.out.println(getName() + "is sleeping for : " + s + "msec");
			try {
				Thread.sleep(s);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}
}

class Main {
	public static void main(String args[]) {
		MyThread t1 = new MyThread("t1"), t2 = new MyThread("t2");
		t1.start();
		t2.start();
		try {
			t1.join();
			t2.join();
		} catch (Exception e) {
		}
		System.out.println(t1.getName() + "thread dead.");
		System.out.println(t2.getName() + "thread dead.");
	}
}

14.1
//Write a Java program for a simple search engine. Accept a string to be searched. Search the string in all text files in the current folder. Use a separate thread for each file. The result should display the filename and line number where the string is found.

import java.io.*;
import java.util.Scanner;

class Mythread extends Thread {
	String str;
	String filename;

	Mythread(String str, String filename) {
		this.str = str;
		this.filename = filename;
	}

	public void run() {
		int count = 0;
		try {
			int flag = 0;
			File f = new File(filename);
			BufferedReader br = new BufferedReader(new FileReader(f));
			String line = " ";
			while ((line = br.readLine()) != null) {
				count++;
				if (line.contains(str) == true) {
					flag = 1;
					break;
				}
			}
			if (flag == 1) {
				System.out.println("String found in floder/file:" + filename + " line no is:" + count);
			} else {
				System.out.println("String not found in floder/file:" + filename);
			}
			br.close();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}

public class Main{
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		System.out.println("enter search string");
		String str = sc.nextLine();
		String dirname = "thread";
		File d = new File(dirname);
		if (d.isDirectory()) {
			String s[] = d.list();
			for (int i = 0; i < s.length; i++) {
				File f = new File(dirname + "/" + s[i]);
				if (f.isFile() && s[i].endsWith(".txt")) {
					Mythread t = new Mythread(str, dirname + "/" + s[i]);
					t.start();
				}
			}
		}
		sc.close();
	}
}

14.2
//Write a JSP program to calculate sum of first and last digit of a given number. Display
sum in Red Color with font size 18. 

//html
<!DOCTYPE html>
<html>
<head>
<title>PERFECT NUMBER</title>
</head>
<body>
	<form action="Main.jsp" method="post">
		Enter Number : <input type="text" name="num"> <input type="submit" value="Submit" name="num">
	</form>
</body>
</html>

//jsp
<html>
<body>
	<%!int n, rem, r;%>
	<%
	n = Integer.parseInt(request.getParameter("num"));
	if (n < 10) {
		out.println("Sum of first and last digit is ");
	%><font size=18 color=red><%=n%> </font>
	<%
	} else {
	rem = n % 10;
	do {
		r = n % 10;
		n = n / 10;
	} while (n > 0);
	n = rem + r;
	out.println("Sum of first and last digit is: ");
	%><font size=18 color=red><%=n%> </font>
	<%
	}
	%>
</body>
</html>

15.1//Write a java program to display name and priority of a Thread.

class Main{
	public static void main(String[] args) {
		String s;
		int p;
		Thread t = Thread.currentThread();
		s = t.getName();
		p = t.getPriority();
		System.out.println("Current thread name: " + s);
		System.out.println("Thread priority: " + p);
	}
}

15.2
//Write a SERVLET program which counts how many times a user has visited a web
page. If user is visiting the page for the first time, display a welcome message. If the
user is revisiting the page, display the number of times visited. (Use Cookie)

import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class Main extends HttpServlet {
	static int i = 1;

	public void doGet(HttpServletRequest request, HttpServletResponse response) throws IOException, ServletException {
		response.setContentType("text/html");
		PrintWriter out = response.getWriter();
		String k = String.valueOf(i);
		Cookie c = new Cookie("visit", k);
		response.addCookie(c);
		int j = Integer.parseInt(c.getValue());
		if (j == 1) {
			out.println("Welcome to web page ");
		} else {
			out.println("You visited this site " + i + " times");
		}
		i++;
	}
}

16.1
//Write a java program to create a TreeSet, add some colors (String) and print out the content of TreeSet in ascending order.

import java.util.*;
public class Main
{
  public static void main(String []args)
  {
    Scanner sc=new Scanner(System.in);
    TreeSet<String>a=new TreeSet<>();
    System.out.print("\nEnter no of colors: ");
    int n=sc.nextInt();
    System.out.print("\nEnter " +n+ " elements: ");
    for(int i=0;i<n;i++)
    { 
      a.add(sc.next());
    }  
    System.out.println("TreeSet elements in ascending order: "+a);
    sc.close();
  }
}

16.2
//Write a Java program to accept the details of Teacher (TNo, TName, Subject). Insert at
least 5 Records into Teacher Table and display the details of Teacher who is teaching
“JAVA” Subject. (Use PreparedStatement Interface) 

import java.sql.*;
import java.util.*;

class Main {
	static Connection cn;
	static Statement st;
	static ResultSet rs;
	static Scanner sc = new Scanner(System.in);

	public static void display() throws SQLException {
		rs = st.executeQuery("select * from Teacher where subject = 'JAVA';");

		System.out.println("|| Tno || TName || Subject ||");
		while (rs.next()) {
			System.out.println("||     " + rs.getInt("tno") + "      || " + rs.getString("tname") + "  ||   "
					+ rs.getString("Subject") + "     ||");
		}
	}

	public static void insert() throws SQLException {
		PreparedStatement ps = cn.prepareStatement("Insert into teacher values(?,?,?);");
		int tno;
		String tname, sub;

		System.out.println("Enter the Teacher no: ");
		tno = sc.nextInt();
		System.out.println("Enter the Teacher name: ");
		tname = sc.next();
		System.out.println("Enter the subject: ");
		sub = sc.next();
		ps.setInt(1, tno);
		ps.setString(2, tname);
		ps.setString(3, sub);
		ps.executeUpdate();
	}

	public static void main(String[] args) throws ClassNotFoundException, SQLException {
		Class.forName("com.mysql.cj.jdbc.Driver");
		cn = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
		st = cn.createStatement();
		int choice = 0;

		while (choice != 3) {
			System.out.println("1. Insert. 2. Display. 3. Exit.");
			System.out.print("Enter choice: ");
			choice = sc.nextInt();
			switch (choice) {
			case 1:
				insert();
				break;
			case 2:
				display();
				break;
			case 3:
				System.exit(0);
			}
		}
	}
}

17.1
//Write a java program to accept ‘N’ integers from a user. Store and display integers in sorted order having proper collection class. The collection should not accept duplicate elements.

import java.util.*;

public class Main
{
    public static void main(String[] args) 
    {
        TreeSet<Integer> ts = new TreeSet<Integer>();
        int n;
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter how many integers: ");
        n = sc.nextInt();
        for(int i=0;i<n;i++) {
        	System.out.print("enter integer: ");
        	ts.add(sc.nextInt());
        }
        System.out.println(ts);
        sc.close();
    }
}

17.2
//Write a Multithreading program in java to display the number’s between 1 to 100
continuously in a TextField by clicking on button. (Use Runnable Interface)

import java.awt.*;
import java.awt.event.*;

public class Main extends Frame implements ActionListener, Runnable {
	Thread y;
	TextField t;
	Button b;

	Main() {
		t = new TextField(20);
		b = new Button("start");
		setLayout(new FlowLayout());
		add(b);
		add(t);
		b.addActionListener(this);
		setSize(300, 300);
		setVisible(true);
		y = new Thread(this);
	}

	public void actionPerformed(ActionEvent e) {
		String msg = e.getActionCommand();
		if (msg.equals("start")) {
			y.start();
		}
	}

	public void run() {
		for (int i = 1; i <= 100; i++) {
			t.setText(i + "");
			try {
				Thread.sleep(100);
			} catch (Exception e) {
			}
		}
	}

	public static void main(String[] d) {
		new Main();
	}

}

18.1
//Write a java program to display name and priority of a Thread.

class Main{
	public static void main(String[] args) {
		String s;
		int p;
		Thread t = Thread.currentThread();
		s = t.getName();
		p = t.getPriority();
		System.out.println("Current thread name: " + s);
		System.out.println("Thread priority: " + p);
	}
}

18.2
//Write a SERVLET program in java to accept details of student (SeatNo, Stud_Name,
Class, Total_Marks). Calculate percentage and grade obtained and display details on
page.

//html
<html>
<body>
	<form name="f1" method="Post" action="Student">
		<fieldset>
			<legend>
				<b><i>Enter Student Details :</i></b>
			</legend>
			Enter Seat No : <input type="text" name="txtsno"><br>
			<br> Enter Name <input type="text" name="txtnm"><br>
			<br> Enter class :<input type="text" name="txtclass"><br>
			<br>
			<fieldset>
				<legend>
					<b><i>Enter Student Marks Details : </i></b>
				</legend>
				Subject 1 : <input type="text" name="txtsub1"><br>
				<br> Subject 2 : <input type="text" name="txtsub2"><br>
				<br> Subject 3 : <input type="text" name="txtsub3"><br>
				<br>
			</fieldset>
		</fieldset>
		<div align=center>
			<input type="submit" value="Result">
		</div>
	</form>
</body>
</html>

//servlet

import java.io.*;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/Student")
public class Student extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		int sno,s1,s2,s3,total;
        String snm,sclass;
        float per;
        res.setContentType("text/html");
        PrintWriter out=res.getWriter();
        sno=Integer.parseInt(req.getParameter("txtsno"));
        snm=req.getParameter("txtnm");
        sclass=req.getParameter("txtclass");
        s1=Integer.parseInt(req.getParameter("txtsub1"));
        s2=Integer.parseInt(req.getParameter("txtsub2"));
        s3=Integer.parseInt(req.getParameter("txtsub3"));
        total=s1+s2+s3;
        per=(total/3);
        out.println("<html><body>");
        out.print("<h2>Result of student</h2><br>");
        out.println("<b><i>Roll No :</b></i>"+sno+"<br>");
        out.println("<b><i>Name :</b></i>"+snm+"<br>");
        out.println("<b><i>Class :</b></i>"+sclass+"<br>");
        out.println("<b><i>Subject1:</b></i>"+s1+"<br>");
        out.println("<b><i>Subject2:</b></i>"+s2+"<br>");
        out.println("<b><i>Subject3:</b></i>"+s3+"<br>");
        out.println("<b><i>Total :</b></i>"+total+"<br>");
        out.println("<b><i>Percentage :</b></i>"+per+"<br>");
        out.close();
	}
}

19.1
//Write a java program to accept ‘N’ Integers from a user store them into LinkedList Collection and display only negative integers.

import java.util.*;
class Main {
	public static void main(String[] args) {
		int n;
		Scanner sc = new Scanner(System.in);
		System.out.print("Enter the size of Linked List: ");
		n = sc.nextInt();
		LinkedList<Integer> ll = new LinkedList<Integer>();
		for (int i = 0; i < n; i++) {
			System.out.print("Enter the element: ");
			ll.add(sc.nextInt());
		}
		Iterator<Integer> it = ll.iterator();
		System.out.println("List of negative numbers: ");
		while (it.hasNext()) {
			int no = it.next();
			if (no < 0)
				System.out.println("\t" + no);
		}
	}
}

19.2
//Write a SERVLET application to accept username and password, search them into
database, if found then display appropriate message on the browser otherwise display
error message.

//html
<html>
<body>
<form method=post action="UserPass">
User Name : <input type=text name=user><br><br>
Password : <input type=text name=pass><br><br>
<input type=submit value="Login">
</form>
</body>
</html>

//servlet
import java.io.*;
import java.sql.*;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/UserPass")
public class UserPass extends HttpServlet {
	private static final long serialVersionUID = 1L;

	protected void doPost(HttpServletRequest request, HttpServletResponse response)
			throws ServletException, IOException {
		PrintWriter out = response.getWriter();
		try {
			String us = request.getParameter("user");
			String pa = request.getParameter("pass");
			Class.forName("com.mysql.cj.jdbc.Driver");
			Connection cn = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
			Statement st = cn.createStatement();
			ResultSet rs = st.executeQuery("select * from UserPass");
			while (rs.next()) {
				if (us.equals(rs.getString("user")) && pa.equals(rs.getString("pass")))
					out.println("Valid user");
				else
					out.println("Invalid user");
			}
		} catch (Exception e) {
			out.println(e);
		}
	}

}

20.1
//Create a JSP page to accept a number from a user and display it in words: Example: 123 – One Two Three. The output should be in red color. 

//html
<html>
<body>
<form method=get action="Main.jsp">
Enter Any Number : <input type=text name=num><br><br>
<input type=submit value="Display">
</form>
<body>
</html>

//jsp
<html>
<body>
<font color=red>
<%! int i,n;
       String s1;
%>
<%   s1=request.getParameter("num");
         n=s1.length();
         i=0;
         do
         {
           char ch=s1.charAt(i);
           switch(ch)
            {
                case '0': out.println("Zero  ");break;
                case '1': out.println("One  ");break;
                case '2': out.println("Two  ");break;
                case '3': out.println("Three  ");break;
                case '4': out.println("Four ");break;
                case '5': out.println("Five  ");break;
               case '6': out.println("Six  ");break;
               case '7': out.println("Seven  ");break;
               case '8': out.println("Eight  ");break;
               case '9': out.println("Nine  ");break;
           }
           i++;
         }while(i<n);
%>
</font>
</body>
</html>

20.2
//Write a java program to blink image on the JFrame continuously. 

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.image.BufferedImage;
import java.io.*;
import javax.imageio.ImageIO;
import javax.swing.*;

class Main extends JPanel implements ActionListener{
	private Image image;
	private Timer timer;
	private boolean visible;
	
	public Main() throws IOException {
		BufferedImage img = ImageIO.read(new File("image.png"));
		image = img.getScaledInstance(300, 300, Image.SCALE_SMOOTH);
		timer = new Timer(500, this);
		timer.start();
		visible = true;
	}
	
	public void paintComponent(Graphics g) {
		super.paintComponent(g);
		if(visible) {
			g.drawImage(image, 0, 0, null);
		}
	}
	
	public void actionPerformed(ActionEvent e) {
		visible = !visible;
		repaint();
	}
	
	public static void main(String[] args) throws IOException {
		JFrame frame = new JFrame("Blinking image");
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		Main panel = new Main();
		panel.setPreferredSize(new Dimension(300,300));
		panel.setBackground(Color.WHITE);
		frame.getContentPane().add(panel);
		frame.pack();
		frame.setVisible(true);
	}
}

21.1
//Write a java program to accept ‘N’ Subject Names from a user store them into LinkedList Collection and Display them by using Iterator interface.

import java.util.*;
class Main {
	public static void main(String[] args) {
		int n;
		Scanner sc = new Scanner(System.in);
		System.out.print("Enter how many n subjects: ");
		n = sc.nextInt();
		LinkedList<String> ll = new LinkedList<String>();
		for (int i = 0; i < n; i++) {
			System.out.print("Enter subject: ");
			ll.add(sc.next());
		}
		Iterator<String> it = ll.iterator();
		System.out.println("Subjects are: ");
		while (it.hasNext()) {
				System.out.println("\t" + it.next());
		}
	}
}

21.2
//Write a java program to solve producer consumer problem in which a producer
produces a value and consumer consume the value before producer generate the next
value. (Hint: use thread synchronization) 

class shop {
	int material;
	boolean flag = false;

	public synchronized int get() {
		while (flag == false) {
			try {
				wait();
			} catch (Exception e) {
				e.getStackTrace();
			}
		}
		flag = false;
		notify();
		return material;
	}

	public synchronized void put(int value) {
		while (flag == true) {
			try {
				wait();
			} catch (Exception e) {
				e.getStackTrace();
			}
		}
		material = value;
		flag = true;
		notify();
	}
}

class consumer extends Thread {
	shop sh;
	int no;

	public consumer(shop shp, int no) {
		sh = shp;
		this.no = no;
	}

	public void run() {
		int value = 0;
		for (int i = 0; i < 10; i++) {
			value = sh.get();
			System.out.println("Consumer#" + this.no + "get:" + value);
		}
	}
}

class producer extends Thread {
	shop sh;
	int no;

	public producer(shop s, int no) {
		sh = s;
		this.no = no;
	}

	public void run() {
		for (int i = 0; i < 10; i++) {
			sh.put(i);
			System.out.println("Producer#" + this.no + "put:" + i);
			try {
				sleep((int) (Math.random() * 100));
			} catch (Exception e) {
				e.getStackTrace();
			}
		}
	}
}

public class Main {
	public static void main(String[] args) {
		shop s = new shop();
		producer p = new producer(s, 1);
		consumer c = new consumer(s, 1);
		p.start();
		c.start();
	}
}

22.1
//Write a Menu Driven program in Java for the following: Assume Employee table with attributes (ENo, EName, Salary) is already created. 1. Insert 2. Update 3. Display 4. Exit. 

import java.sql.*;
import java.util.Scanner;

class Main {
	public static void main(String args[])
    {
        Scanner sc = new Scanner(System.in);
        int eno,k,ch,sal;
        String nm;
        String update;
        try{
        	Class.forName("com.mysql.cj.jdbc.Driver");
    		Connection cn = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
            Statement st=cn.createStatement();
            do            {
                System.out.println("1. Insert. 2. Update 3. Display. 4. Exit");
                System.out.print("Enter your choice: ");
                ch=sc.nextInt();
                System.out.println("............................................");
                switch(ch)
                {
                    case 1:
                        System.out.print("How many records you want to inserted ? : ");
                        int n=sc.nextInt();
                        for(int i=0;i<n;i++)
                        {
                            System.out.println("Enter Employee No : ");
                            eno=sc.nextInt();
                            System.out.println("Enter Employee Name : ");
                            nm=sc.next();
                            System.out.println("Enter Salary: ");
                            sal=sc.nextInt();
                            k=st.executeUpdate("insert into Employee values(" + eno + ",'"+ nm + "'," + sal +")");
                            if(k>0)
                            {
                                System.out.println("Record Inserted Successfully..!!");
                                System.out.println("..............................................");
                            }
                        }
                        break;
                    case 2:
                        System.out.print("Enter the Employee no: ");
                        eno=sc.nextInt();
                        System.out.print("Enter what to update: ");
                        update = sc.next();
                        System.out.print("Enter " + update + ": ");
                        nm = sc.next();
                        k=st.executeUpdate("update Employee set " + update + "='" + nm + "' where eno="+eno);
                        if(k>0)
                        {
                            System.out.println("Record Is Updated..!!");
                        }
                        System.out.println("...............................................");
                        break;
                    case 3:
                        ResultSet rs=st.executeQuery("select * from Employee");
                        while(rs.next())
                        {
                            System.out.println(rs.getInt(1) +"\t" +rs.getString(2)+"\t"+rs.getInt(3));
                        }
                        System.out.println(".............................................");
                        break;
                    case 4:
                        System.exit(0);
                }
            }
            while(ch!=4);
        }
        catch(Exception e)
        {
            System.out.println("Error");
        }
    }
}

22.2
//Write a JSP program which accepts UserName in a TextBox and greets the user
according to the time on server machine. 

//html
 <html>
    <body>
        <form action="Main.jsp" method="post">
            Enter Username : <input type="text" name="name"><br>
            <input type="submit" value="Submit">
        </form>
    </body>
</html>

//jsp
<%@page import="java.util.Calendar"%>
<%@page contentType="text/html" pageEncoding="UTF-8"%>

<%
String name = request.getParameter("name");

Calendar rightnow = Calendar.getInstance();
int time = rightnow.get(Calendar.HOUR_OF_DAY);

if (time > 0 && time <= 12) {
	out.println("Good Morning " + name);
} else if (time < 12 && time >= 16) {
	out.println("Good Afternoon" + name);
} else {
	out.println("Good Night " + name);
}
%>

23.1
//Write a java program to accept a String from a user and display each vowel from a String after every 3 seconds.

import java.util.*;

class Vowels extends Thread {
	String s1;

	Vowels(String s) {
		s1 = s;
		start();
	}

	public void run() {
		System.out.println("Vowels are:  ");
		for (int i = 0; i < s1.length(); i++) {
			char ch = s1.charAt(i);
			if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' || ch == 'A' || ch == 'E' || ch == 'I'
					|| ch == 'O' || ch == 'U')
				System.out.print(" " + ch);
				try {
					sleep(3000);
				} catch (InterruptedException e) {
					e.printStackTrace();
				}
		}
	}
}

public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter a string: ");
		String str1 = sc.next();
		new Vowels(str1);
	}
}

23.2
//Write a java program to accept ‘N’ student names through command line, store them
into the appropriate Collection and display them by using Iterator and ListIterator
interface.

import java.util.*;

public class Main {
	public static void main(String args[]) throws Exception {
		int n;
		LinkedList<String> li = new LinkedList<String>();
		String str = "";

		n = Integer.parseInt(args[0]);
		for (int i = 1; i <= n; i++) {
			str = args[i];
			System.out.println(str);
			li.add(str);
		}
		System.out.println("\nUsing iterator: ");
		Iterator<String> it = li.iterator();
		while(it.hasNext())
		{
			System.out.println(it.next());
		}
		
		System.out.println("\nUsing ListIterator: ");		
		ListIterator<String> lt = li.listIterator();
		while (lt.hasNext()) {
			System.out.println(lt.next());
		}
	}
}

24.1
//1Write a java program to scroll the text from left to right continuously.

import java.util.*;

public class Main {

	public static void main(String[] args) {

		Scanner sc = new Scanner(System.in);
		System.out.println("Enter the text to scroll: ");
		String text = sc.nextLine();
		int width = 20;
		int position = 0;
		int direction = 1;
		while (true) {
			for (int i = 0; i < width; i++) {
				System.out.print(" ");
			}
			for (int i = 0; i < text.length(); i++) {
				if (i + position >= 0 && i + position < width) {
					System.out.print(text.charAt(i));
				} else {
					System.out.print(" ");
				}
			}
			position += direction;
			if (position == width - text.length() || position == 0) {
				direction = -direction;
			}
			try {
				Thread.sleep(100);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
			for (int i = 0; i < width + text.length(); i++) {
				System.out.print("\b");
			}
		}
	}
}

24.2
//2Write a JSP script to accept username and password from user, if they are same then
display “Login Successfully” message in Login.html file, otherwise display “Login
Failed” Message in Error.html file.

//Main.html
<html>
<head>
<title>Login Page</title>
</head>
<body>
	<form action="Main.jsp">
		Enter User Id and Password
		<br>UserId: <input type="text" name="id" /> <br>
		<br> Password: <input type="text" name="pass" /> <br>
		<br> <input type="submit" value="Sign In" />
	</form>
</body>
</html>

//Main.jsp
<html>
<head>
<title>Check Credentials</title>
</head>
<body>
<%
        String uid=request.getParameter("id");
        String password=request.getParameter("pass");
        session.setAttribute("session-uid", uid);
        if(uid.equals(password))
        {
			response.sendRedirect("login.html");
        }
        else
		{
            response.sendRedirect("error.html");
        }
%>
</body>
</html>

//login.html
<html>
<head><title>Success Page</title></head>
<body>
        <h1>Login Successful..</h1>
</body>
</html>

//error.html
<html>
<head><title>Sign-in Failed Page</title></head>
<body>
        <h1>User Id and Password are not same. Please try Again.</h1>
</body>
</html>

25.1
//1) Write a JSP program to accept Name and Age of Voter and check whether he is eligible for voting or not. 

//html
<html>
<body>
	<form action="Main.jsp" method="post">
		Name : <input type="text" name="name"> Age : <input
			type="text" name="age"> <input type="submit" value="Check">
	</form>
</body>
</html>

//jsp
<%@page contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<%
String name = request.getParameter("name");
int age = Integer.parseInt(request.getParameter("age"));
if (age >= 18) {
	out.println(name + " is Allowed to vote");
} else {
	out.println(name + " is Not allowed to vote");
}
%>


25.2
//2) Write a Java Program for the following: Assume database is already created

26.1
//Write a Java program to delete the details of given employee (ENo EName Salary). Accept employee ID through command line. (Use PreparedStatement Interface)

import java.sql.*;

class Main {
	public static void main(String args[]) {
		Connection con;
		PreparedStatement ps;
		ResultSet rs;
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			con = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
			if (con == null) {
				System.out.println("Connection Failed....");
				System.exit(1);
			}
			System.out.println("Connection Established...");
			ps = con.prepareStatement("select * from employee where eid=?");
			int id = Integer.parseInt(args[0]);
			ps.setInt(1, id);

			rs = ps.executeQuery();
			System.out.println("eno\t" + "ename\t" + "salary");
			while (rs.next()) {
				System.out.println(
						"\n" + rs.getInt(1) + "\t" + rs.getString(2) + "\t" + rs.getString(3));
			}
			con.close();
		} catch (Exception e) {
			System.out.println(e);
		}
	}
}

26.2
//Write a JSP program to calculate sum of first and last digit of a given number. Display
sum in Red Color with font size 18.

//html
<!DOCTYPE html>
<html>
<head>
<title>PERFECT NUMBER</title>
</head>
<body>
	<form action="Main.jsp" method="post">
		Enter Number : <input type="text" name="num"> <input type="submit" value="Submit" name="num">
	</form>
</body>
</html>

//jsp
<html>
<body>
	<%!int n, rem, r;%>
	<%
	n = Integer.parseInt(request.getParameter("num"));
	if (n < 10) {
		out.println("Sum of first and last digit is ");
	%><font size=18 color=red><%=n%> </font>
	<%
	} else {
	rem = n % 10;
	do {
		r = n % 10;
		n = n / 10;
	} while (n > 0);
	n = rem + r;
	out.println("Sum of first and last digit is: ");
	%><font size=18 color=red><%=n%> </font>
	<%
	}
	%>
</body>
</html>

27.1
//Write a Java Program to display the details of College (CID, CName, address, Year) on JTable. 

import java.sql.*;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import javax.swing.table.*;

class Main extends JFrame implements ActionListener {

    Connection con;
    ResultSet rs;
    Statement st;

    static JTable table;
    String[] columnNames = { "CID", "CName", "Address", "Year" };
    JFrame frm;
    JPanel p1;
    String c_id = "", c_name = "", address = "", year = "";
    JTextField txtid, txtname, txtdesc, textstatus;
    JButton Display, Exit;

    Main() {
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setTitle("PROJECT INFO");

        p1 = new JPanel();
        p1.setLayout(new GridLayout(2, 2, 30, 30));
        Display = new JButton("Display");
        p1.add(Display);
        Exit = new JButton("Exit");
        p1.add(Exit);
        Display.addActionListener(this);
        Exit.addActionListener(this);
        add(p1, BorderLayout.CENTER);
        setVisible(true);
        setSize(600, 600);
    }

    public void actionPerformed(ActionEvent ae) {
        if (ae.getSource() == Display) {
            frm = new JFrame("DISPLAY");
            setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
            setLayout(new BorderLayout());
            DefaultTableModel model = new DefaultTableModel();
            model.setColumnIdentifiers(columnNames);
            table = new JTable();
            table.setModel(model);
            table.setAutoResizeMode(JTable.AUTO_RESIZE_ALL_COLUMNS);
            table.setFillsViewportHeight(true);
            JScrollPane scroll = new JScrollPane(table);
            scroll.setHorizontalScrollBarPolicy(JScrollPane.HORIZONTAL_SCROLLBAR_AS_NEEDED);
            scroll.setVerticalScrollBarPolicy(JScrollPane.VERTICAL_SCROLLBAR_AS_NEEDED);
            try {
            	Class.forName("com.mysql.cj.jdbc.Driver");
        		con = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
                st = con.createStatement();
                rs = st.executeQuery("select * from college");
                while (rs.next()) {
                    c_id = rs.getString(1);
                    c_name = rs.getString(2);
                    address = rs.getString(3);
                    year = rs.getString(4);
                    model.addRow(new Object[] { c_id, c_name, address, year });
                }
                frm.add(scroll);
                frm.setVisible(true);
                frm.setSize(400, 400);
            }
            catch (Exception e) {
                JOptionPane.showMessageDialog(null, e, "Error", JOptionPane.ERROR_MESSAGE);
            }
        }
        if (ae.getSource() == Exit) {
            System.exit(1);
        }
    }
    public static void main(String arg[]) {
        new Main();
    }
}

27.2
//Write a SERVLET program to change inactive time interval of session.

import java.io.*;
import javax.servlet.*;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.*;

@WebServlet("/MyServlet")
public class MyServlet extends HttpServlet {
	public void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
		res.setContentType("text/html");
		PrintWriter out = res.getWriter();
		HttpSession session = req.getSession();
		out.println("<HTML><HEAD><TITLE>SessionTimer</TITLE></HEAD>");
		out.println("<BODY><H1>Session Timer</H1>");
		out.println("The previous timeout was " + session.getMaxInactiveInterval());
		out.println("<BR>");
		session.setMaxInactiveInterval(2 * 60 * 60); // two hours
		out.println("The newly assigned timeout is " + session.getMaxInactiveInterval());
		out.println("</BODY></HTML>");
	}
}

28.1
//Write a JSP script to accept a String from a user and display it in reverse order.

<html>
<body>
	<form method = "post">
		Enter a string: <input type = "text" name = "str1"><br><br>
		<input type = "submit" value="Reverse">
	</form>
	<br><br>
	<%
		String str1 = request.getParameter("str1");
		if(str1 != null && !str1.isEmpty()){
			String revStr = new StringBuilder(str1).reverse().toString();
			out.println("Original string: " + str1 + "<br>");
			out.println("Reversed string: " + revStr + "<br>");
		}
	%>
</body>
</html>

28.2
//Write a java program to display name of currently executing Thread in multithreading.

class Main{
	public static void main(String[] args) {
		Thread t = Thread.currentThread();
		System.out.println("Currently executing thread is: " + t.getName());
	}
}

29.1
//Write a Java program to display information about all columns in the DONAR table using ResultSetMetaData. 

import java.sql.*;

class Main{
	public static void main(String args[]) {
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");

			PreparedStatement ps = con.prepareStatement("select * from donar");
			ResultSet rs = ps.executeQuery();
			ResultSetMetaData rsmd = rs.getMetaData();
			int col = rsmd.getColumnCount();

			System.out.println("Total columns: " + col);
			
			for(int i=1;i<=col;i++) {
				System.out.println("Column Name of column " + i + ": " + rsmd.getColumnName(i));
				System.out.println("Column Type Name of column " + i + ": " + rsmd.getColumnTypeName(i));
			}
			con.close();
		} catch (Exception e) {
			System.out.println(e);
		}
	}
}

29.2
//Write a Java program to create LinkedList of integer objects and perform the following:

import java.util.*;
class Main{
	
	public static void main(String[] args) {
		int choice = 0;
		Scanner sc = new Scanner(System.in);
		LinkedList<Integer> ll = new LinkedList<Integer>();
		
		while(choice != 5) {
			System.out.println("1. Add element at the first. 2. Delete last element of the list. 3. Display size. 4 Display Linked List. 5"
					+ ". Exit");
			System.out.print("Enter choice: ");
			choice = sc.nextInt();
			switch(choice) {
			case 1:
				System.out.print("Enter element name: ");
				ll.addFirst(sc.nextInt());
				break;
			case 2:
				ll.removeLast();
				break;
			case 3:
				System.out.println("Size of linked list is: " + ll.size());
				break;
			case 4:
				System.out.println("Linked list is: " + ll);
				break;
			case 5:
				System.exit(0);
			}
		}
	}
}

30.1
//Write a java program for the implementation of synchronization.

class Table {
	synchronized void printTable(int n) {
		for (int i = 1; i <= 5; i++) {
			System.out.println(n * i);

			try {
				Thread.sleep(400);
			} catch (Exception e) {
				System.out.println(e);
			}
		}
	}
}

class MyThread1 extends Thread {
	Table t;

	MyThread1(Table t) {
		this.t = t;
	}

	public void run() {
		t.printTable(5);
	}
}

class MyThread2 extends Thread {
	Table t;

	MyThread2(Table t) {
		this.t = t;
	}

	public void run() {
		t.printTable(20);
	}
}

class Main {
	public static void main(String args[]) {
		// shared object
		Table obj = new Table();
		MyThread1 t1 = new MyThread1(obj);
		MyThread2 t2 = new MyThread2(obj);
		t1.start();
		t2.start();
	}
}

30.2
//Write a Java Program for the implementation of scrollable ResultSet. Assume Teacher
table with attributes (TID, TName, Salary) is already created. 

import java.sql.*;
import java.util.*;

class Main {
	public static void main(String args[]) {
		Connection conn = null;
		Statement stmt = null;
		ResultSet rs = null;
		int ch;
		Scanner s = new Scanner(System.in);
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");
			conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/student", "root", "student");
			stmt = conn.createStatement(ResultSet.TYPE_SCROLL_SENSITIVE, ResultSet.CONCUR_UPDATABLE);
			rs = stmt.executeQuery("select * from teacher");
			int count = 0;
			while (rs.next())
				count++;
			System.out.println("Total Records are = " + count);
			do {
				System.out.println("1 First. 2 Last. 3 Next. 4 Prev. 5. Exit");
				ch = s.nextInt();
				switch (ch) {
				case 1:
					rs.first();
					System.out.println("TId :" + rs.getInt(1) + " TName :" + rs.getString(2) + " TSalary : " + rs.getString(3));
					break;
				case 2:
					rs.last();
					System.out.println("Roll :" + rs.getInt(1) + " Name :" + rs.getString(2) + " TSalary : " + rs.getString(3));
					break;
				case 3:
					rs.next();
					if (rs.isAfterLast())
						System.out.println("Can't move forword");
					else
						System.out.println("Roll :" + rs.getInt(1) + " Name :" + rs.getString(2) + " TSalary : " + rs.getString(3));
					break;
				case 4:
					rs.previous();
					if (rs.isBeforeFirst())
						System.out.println("Can't move backword");
					else
						System.out.println("Roll :" + rs.getInt(1) + " Name :" + rs.getString(2) + " TSalary : " + rs.getString(3));
					break;
				case 5:
					break;
				default:
					System.out.println("Enter valid operation");
				}
			} while (ch != 5);
		}
		catch (Exception e) {
			System.out.println(e);
		}
	}
}
