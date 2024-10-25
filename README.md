Slip 1_1: Write a Program to print all Prime numbers in an array of ‘n’
elements.(use command line arguments)
class PrNo
{
public static void main (String[] args)
{
int size = args.length;
int[] array = new int [size];
for(int i=0; i<size; i++)
{
array[i] = Integer.parseInt(args[i]);
}
for(int i=0; i<array.length; i++)
{
boolean isPrime = true;
for (int j=2; j<array[i]; j++)
{
if(array[i]%j==0)
{
isPrime = false;
break;
}
}
if(isPrime)
System.out.println(array[i] + " are the prime numbers in the array ");
}
}
}
========================================================================
======================================================
Slip 1_2: Define an abstract class Staff with protected members id and name. Define a
parameterized
constructor. Define one subclass OfficeStaff with member department. Create n objects of
OfficeStaff and display all details.
Solution:
import java.util.*;
abstract class Staff
{
protected int id;
protected String name;
public Staff(int id,String name)
{
this.id=id;
this.name=name;
}
}
class OfficeStaff extends Staff
{
String dept;
OfficeStaff(int id,String name,String dept)
{
super(id,name);
this.dept=dept;
}
public void display()
{
System.out.println("ID :"+id+" Name :"+name+" Department :"+dept);
}
public static void main(String args[])
{
int n,id;
String name,dept;
Scanner sc=new Scanner(System.in);
System.out.println("How many staff members?");
n=sc.nextInt();
OfficeStaff ob[]=new OfficeStaff[n];
System.out.println("Enter details of "+n+" staff");
for(int i=0;i<n;i++)
{
System.out.println("Enter id,name, department");
id=sc.nextInt();
name=sc.next();
dept=sc.next();
ob[i]=new OfficeStaff(id,name,dept);
}
System.out.println("Entered Details are\n");
for(int i=0;i<n;i++)
{
ob[i].display();
}
}
}
========================================================================
==============================================
Slip2_1:
class BM {
public static void main(String args[]) {
String fname = args[0];
String lname = args[1];
double weight = Double.parseDouble(args[2]);
double height = Double.parseDouble(args[3]);
double BMI = weight / (height * height);
System.out.println("First name is:" +fname);
System.out.println("Last Name is:" + lname);
System.out.println("weight is:" + weight);
System.out.println("height is:"+ height);
System.out.println("The Body Mass Index (BMI) is " + BMI + " kg/m2");
}
}
========================================================================
==============================================
Slip2_2: Define a class CricketPlayer (name,no_of_innings,no_of_times_notout, totatruns,
bat_avg). Create an array of n player objects .Calculate the batting average for each player
using static method avg(). Define a static sort method which sorts the array on the basis of
average. Displaythe player details in sorted order.
import java.io.*;
class Cricket {
String name;
int inning, tofnotout, totalruns;
float batavg;
public Cricket(){
name=null;
inning=0;
tofnotout=0;
totalruns=0;
batavg=0;
}
public void get() throws IOException{
BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
System.out.println("Enter the name, no of innings, no of times not out, total runs: ");
name=br.readLine();
inning=Integer.parseInt(br.readLine());
tofnotout=Integer.parseInt(br.readLine());
totalruns=Integer.parseInt(br.readLine());
}
public void put(){
System.out.println("Name="+name);
System.out.println("no of innings="+inning);
System.out.println("no times notout="+tofnotout);
System.out.println("total runs="+totalruns);
System.out.println("bat avg="+batavg);
}
static void avg(int n, Cricket c[]){
try{
for(int i=0;i<n;i++){
c[i].batavg=c[i].totalruns/c[i].inning;
}
}catch(ArithmeticException e){
System.out.println("Invalid arg");
}
}
static void sort(int n, Cricket c[]){
String temp1;
int temp2,temp3,temp4;
float temp5;
for(int i=0;i<n;i++){
for(int j=i+1;j<n;j++){
if(c[i].batavg<c[j].batavg){
temp1=c[i].name;
c[i].name=c[j].name;
c[j].name=temp1;
temp2=c[i].inning;
c[i].inning=c[j].inning;
c[j].inning=temp2;
temp3=c[i].tofnotout;
c[i].tofnotout=c[j].tofnotout;
c[j].tofnotout=temp3;
temp4=c[i].totalruns;
c[i].totalruns=c[j].totalruns;
c[j].totalruns=temp4;
temp5=c[i].batavg;
c[i].batavg=c[j].batavg;
c[j].batavg=temp5;
}
}
}
}
}
class Name {
public static void main(String args[])throws IOException{
BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
System.out.println("Enter the limit:");
int n=Integer.parseInt(br.readLine());
Cricket c[]=new Cricket[n];
for(int i=0;i<n;i++){
c[i]=new Cricket();
c[i].get();
}
Cricket.avg(n,c);
Cricket.sort(n, c);
for(int i=0;i<n;i++){
c[i].put();
}
}
}
========================================================================
==============================================
Slip3_1: Write a program to accept ‘n’ name of cities from the user and sort them in
ascendingorder.
import java.util.Scanner;
class SortStr
{
public static void main(String args[])
{
String temp;
Scanner SC = new Scanner(System.in);
System.out.print("Enter the value of N: ");
int N= SC.nextInt();
SC.nextLine(); //ignore next line character
String names[] = new String[N];
System.out.println("Enter names: ");
for(int i=0; i<N; i++)
{
System.out.print("Enter name [ " + (i+1) +" ]: ");
names[i] = SC.nextLine();
}
for(int i=0; i<N; i++)
{
for(int j=1; j<N; j++)
{
if(names[j-1].compareTo(names[j])>0)
{
temp=names[j-1];
names[j-1]=names[j];
names[j]=temp;
}
}
}
System.out.println("\nSorted names are in Ascending Order: ");
for(int i=0;i<N;i++)
{
System.out.println(names[i]);
}
}
}
========================================================================
==============================================
Slip 3_2:
Define a class patient(patient_name,patient_age,patient_oxy_level,patient_HRCT_report).
Create an object of patient. Handle
appropriate exception while patient oxygen level less than 95% and HRCT scan
report greater than 10, then throw user defined Exception “Patient is CovidPositive(+)
and Need to Hospitalized” otherwise display its information.
import java.io.*;
class CovidException extends Exception{
public CovidException(){
System.out.println("Patient is Covid Positive and needs to be hospitalized");
}
}
class Patient{
String name;
int age;
double level,hrct;
public Patient(String name,int age,double level,double hrct)
{
this.name=name;
this.age=age;
this.level=level;
this.hrct=hrct;
}
public static void main(String[] args)throws IOException
{
String name;
int age;
double level,hrct;
BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
System.out.println("Enter name: ");
name=br.readLine();
System.out.println("Enter the age: ");
age=Integer.parseInt(br.readLine());
System.out.println("Oxygen level: ");
level=Double.parseDouble(br.readLine());
System.out.println("HRCT report: ");
hrct=Double.parseDouble(br.readLine());
Patient ob=new Patient(name,age,level,hrct);
try{
if(ob.level<95 && ob.hrct>10)
throw new CovidException();
else
System.out.println("Patient Info: \n"+"Name: "+ob.name+"\nAge: "+ob.age+"\nHRCT
report: "+ob.hrct+"\nOxygen level:"
+ob.level);
}catch(CovidException e){
}
}
}
========================================================================
==============================================
Slip5_1: Write a program for multilevel inheritance such that Country is inherited from
Continent.State is inherited from Country. Display the place, State, Country and Continent.
import java.io.InputStreamReader;
import java.io.BufferedReader;
import java.io.IOException;
class Continent{
String con;
InputStreamReader i = new InputStreamReader(System.in);
BufferedReader r = new BufferedReader(i);
void con_input() throws IOException
{
System.out.println("Enter the continent name:");
con = r.readLine();
}
}
class Country extends Continent
{
String cou;
void cou_input()throws IOException
{
System.out.println("Enter the country name:");
cou = r.readLine();}
}
class State extends Country
{
String sta;
void sta_input()throws IOException
{
System.out.println("Enter the state name:");
sta = r.readLine();}
}
class Main extends State
{
String pla;
void pla_input()throws IOException
{
System.out.println("Enter the place name:");
pla = r.readLine();}
public static void main(String args[])throws IOException
{
Main s = new Main();
s.con_input();
s.cou_input();
s.sta_input();
s.pla_input();
System.out.println("place is:"+s.pla);
System.out.println("state is:"+s.sta);
System.out.println("country is:"+s.cou);
System.out.println("continent is:"+s.con);
}
}
========================================================================
==============================================
Slip5_2:Write a menu driven program to perform the following operations on
multidimensional arrayie matrices :
.Addition
.Multiplication
import java.util.*;
class Matrix
{
Scanner sc = new Scanner(System.in);
int a = sc.nextInt();
int b = sc.nextInt();
int M[][] = new int[a][b];
void accept()
{
int a = this.a;
int b = this.b;
System.out.println("enter the "+(a*b)+ " values to matrix:");
for(int i=0;i<a;i++)
{
for(int j=0;j<b;j++)
{
this.M[i][j] = sc.nextInt();
}
}
}
void display()
{
for(int i =0;i<a;i++)
{
for(int j =0;j<b;j++)
{
System.out.print(" "+this.M[i][j]);
}
System.out.println(" ");
}
}
public static void main(String a[])
{
System.out.println("enter size 2*2 or 3*3 or ...");
Matrix m1 = new Matrix();
m1.accept();
System.out.println("values to matrix 1:");
m1.display();
System.out.println("enter the size:");
Matrix m2 = new Matrix();
m2.accept();
System.out.println("values to matrix 2:");
m2.display();
int choice;
Scanner scanner = new Scanner(System.in);
while(true) {
System.out.println("Press 1: Addition, 2: Multiplication, 3: Exit");
choice = scanner.nextInt();
switch (choice) {
case 1:
System.out.println("Addition is:" );
for(int i=0;i<m1.a;i++)
{
for(int j=0;j<m1.b;j++)
{
System.out.print(" "+ (m1.M[i][j]+m2.M[i][j]));
}
System.out.println(" ");
}
break;
case 2:
System.out.println("Multiplication is:");
for(int i=0;i<m2.a;i++)
{
for(int j=0;j<m2.b;j++)
{
System.out.print(" "+
(m1.M[i][j]*m2.M[i][j]));
}
System.out.println(" ");
}
break;
case 3:
System.exit(0);
}
}
}
}
========================================================================
==============================================
Slip6_1: Write a program to display the Employee(Empid, Empname,
mpdesignation, Empsal)information using toString().
.
class Emp
{
int id,salary;
String name;
String desig;
Emp(int id, String name, int salary ,String desig)
{
this.id=id;
this.name=name;
this.salary=salary;
this.desig=desig;
}
public String toString() // overrides toString() method
{
return id+" "+name+" "+salary+" "+desig;
}
public static void main(String args[])
{
Emp E1=new Emp(111,"Rakesh",50000,"bsc cs");
Emp E2=new Emp(112,"Suresh",25000,"msc cs");
System.out.println("Employee details: "+E1);
System.out.println("Employee details: "+E2);
}
}
========================================================================
==============================================
Slip6_2: Create an abstract class “order” having members id, description. Create two
subclasses “PurchaseOrder” and “Sales Order” having members customer name and
Vendor name respectively. Definemethods accept and display in all cases. Create 3
objects each of Purchase Order and Sales Order and accept and display details.
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
abstract class Order{
String id,des;
}
class Porder extends Order{
String cnm, vnm;
public void accept()throws IOException{
System.out.println("enter id, description,names of customers and vendors");
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
id = br.readLine();
des= br.readLine();
cnm = br.readLine();
vnm = br.readLine();
}
public void display(){
System.out.println("id"+id);
System.out.println("Description"+des);
System.out.println("Customer Name"+cnm);
System.out.println("Vendor Name"+vnm);
System.out.println("-------------------");
}
}
class Sorder extends Order
{
String cnm, vnm;
public void accept()throws IOException{
System.out.println("enter id, description,names of customers and vendors");
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
id = br.readLine();
des= br.readLine();
cnm = br.readLine();
vnm = br.readLine();
}
public void display(){
System.out.println("id:"+id);
System.out.println("Description:"+des);
System.out.println("Customer Name:"+cnm);
System.out.println("Vendor Name:"+vnm);
System.out.println("-------------------");
}
}
class Main{
public static void main(String args[])throws IOException{
int i;
System.out.println("Select any one:");
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
System.out.println("1.purchase order:");
System.out.println("2.Sales order:");
System.out.println("3.Exit:");
int ch = Integer.parseInt(br.readLine());
switch(ch){
case 1:
System.out.println("enter the no of purchas order:");
int n = Integer.parseInt(br.readLine());
Porder[] l = new Porder[n];
for(i=0;i<n;i++)
{
l[i] = new Porder();
l[i].accept();
}
for(i=0;i<n;i++)
{
l[i].display();
System.out.println("Object is created:");
}
case 2:
System.out.println("enter the no of sales order:");
int m = Integer.parseInt(br.readLine());
Porder[] h = new Porder[m];
for(i=0;i<m;i++)
{
h[i] = new Porder();
h[i].accept();
}
for(i=0;i<m;i++)
{
h[i].display();
System.out.println("Object is created:");
}
case 3:
System.out.println("exit:");
System.exit(0);
}
}
}
========================================================================
==============================================
Slip7_1: Design a class for Bank. Bank Class should support following operations;
a. Deposit a certain amount into an account
b. Withdraw a certain amount from an account
c. Return a Balance value specifying the amount with details
class Bank
{
private double balance;
public Bank()
{
balance = 0;
}
public Bank(double initialBalance)
{
balance = initialBalance;
}
public void deposit(double amount)
{
balance = balance + amount;
}
public void withdraw(double amount)
{
balance = balance - amount;
}
public double getBalance()
{
return balance;
}
public static void main(String[] args)
{
Bank b = new Bank(1000);
b.withdraw(250);
System.out.println("the withdraw is:"+ b.balance);
b.deposit(400);
System.out.println("the deposit is:"+ b.balance);
System.out.println("the balance is:"+ b.getBalance());
}
}
========================================================================
==============================================
Slip7_2: Write a program to accept a text file from user and display the contents of a file in
reverse order and change its case.
import java.io.*;
import java.util.*;
class ReverseFile
{
public static void main(String args[])throws IOException
{
Scanner sc = new Scanner(System.in);
System.out.println("enter file name:");
String fnm = sc.next();
File f = new File(fnm);
if(f.isFile())
{
BufferedInputStream bis = new BufferedInputStream(new
FileInputStream(fnm));
int size =bis.available();
for(int i = size-1;i>=0;i--)
{
bis.mark(i);
bis.skip(i);
char ch=((char)bis.read());
if(Character.isLowerCase(ch))
ch=Character.toUpperCase(ch);
else if(Character.isUpperCase(ch))
ch = Character.toLowerCase(ch);
System.out.print(ch);
bis.reset();
}
bis.close();
}
else
System.out.println("file not found");
}
}
========================================================================
==============================================
Slip8_1: Create a class Sphere, to calculate the volume and surface area of sphere.(Hint :
Surface
area=4*3.14(r*r), Volume=(4/3)3.14(r*r*r))
import java.util.*;
class Sphere
{
public static void main (String[] args)
{
Scanner sc=new Scanner(System.in);
System.out.println("Enter the radius of the sphere: ");
double radius=sc.nextDouble();
double surface_area = (4*3.14*(radius*radius));
double volume = ((double)4/3)*3.14*(radius*radius*radius);
System.out.println("The surface area of the sphere = "+surface_area);
System.out.println("The volume of sphere = "+volume);
}
}
========================================================================
==============================================
Slip8_2:
import java.awt.*;
import java.awt.event.*;
class MyFrame extends Frame
{
TextField t,t1;
Label l,l1;
int x,y;
Panel p;
MyFrame(String title)
{
super(title);
setLayout(new FlowLayout());
p=new Panel();
p.setLayout(new GridLayout(2,2,5,5));
t=new TextField(20);
l= new Label("Co-ordinates of mouse clicking");
l1= new Label("Co-ordinates of mouse movement");
t1=new TextField(20);
p.add(l);
p.add(t);
p.add(l1);
p.add(t1);
add(p);
addMouseListener(new MyClick());
addMouseMotionListener(new MyMove());
setSize(500,500);
setVisible(true);
}
class MyClick extends MouseAdapter
{
public void mouseClicked(MouseEvent me)
{
x=me.getX();
y=me.getY();
t.setText("X="+x+" Y="+y);
}
}
class MyMove extends MouseMotionAdapter
{
public void mouseMoved(MouseEvent me)
{
x=me.getX();
y=me.getY();
t1.setText("X="+ x +" Y="+y);
}
}
}
class frame1
{
public static void main(String args[])
{
MyFrame f = new MyFrame("Set A-2");
}
}
========================================================================
==============================================
Slip10_1: Write a program to find the cube of given number using functional interface.
import java.util.*;
interface Cube
{
float cube();
}
class Draw implements Cube
{
public float cube()
{
System.out.println("enter the number");
Scanner sc= new Scanner (System.in);
float cu = sc.nextInt();
double cue = cu*cu*cu;
System.out.println("cube of no is:"+cue);
return 0;
}
public static void main(String args[])
{
Draw d = new Draw();
d.cube();
}
}
========================================================================
==============================================
Slip10_2:
package student;
class StudentInfo
{
public int r_no;
public String name, clas;
public int a,b,c,d,e,f;
int sum=0;
double per;
public void display()
{
System.out.println("Roll_no : "+r_no);
System.out.println("Name : "+name);
System.out.println("class :"+clas);
System.out.println("-----MARKS-------");
System.out.println("Sub 1 : "+a);
System.out.println("Sub 2 : "+b);
System.out.println("Sub 3 : "+c);
System.out.println("Sub 4 : "+d);
System.out.println("Sub 5 : "+e);
System.out.println("Sub 6 : "+f);
System.out.println("Total : "+sum);
System.out.println("percentage: "+per);
System.out.println("------------------");
}
}
public class StudentPer extends StudentInfo {
public StudentPer(int roll, String nm, String cla,int m1,int m2,int m3,int m4, int
m5,int m6)
{
r_no = roll;
clas = cla;
name = nm;
a = m1;
b = m2;
c = m3;
d = m4;
e = m5;
f = m6;
sum = a+b+c+d+e+f;
per = sum/6;
}
}
Main File
import student.StudentPer;
import java.util.*;
import java.lang.*;
import java.io.*;
class StudentMain
{
public static void main(String[] args)
{
String nm, clas;
int roll;
Scanner sc = new Scanner(System.in);
System.out.print("Enter Roll no:= ");
roll = sc.nextInt();
System.out.print("Enter Name:= ");
nm = sc.next();
System.out.print("Enter class:= ");
clas= sc.next();
int m1,m2,m3,m4,m5,m6;
System.out.print("Enter 6 sub mark:= ");
m1 = sc.nextInt();
m2 = sc.nextInt();
m3 = sc.nextInt();
m4 = sc.nextInt();
m5 = sc.nextInt();
m6 = sc.nextInt();
StudentPer s = new StudentPer(roll,nm,clas,m1,m2,m3,m4,m5,m6);
s.display();
}
}
========================================================================
==============================================
Slip11_1: Define an interface “Operation” which has method volume( ).Define a constant PI
having a value 3.142 Create a class cylinder which implements this interface (members –
radius,height). Createone object and calculate the volume.
import java.io.*;
interface Operation
{
final static float pi=3.142f;
void area();
void volume();
}
class Cylinder implements Operation
{
double radius,height;
void input() throws Exception
{
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
System.out.print("\n Enter the radius and height=");
radius=Double.parseDouble(br.readLine());
height=Double.parseDouble(br.readLine());
}
public void area()
{
double a=(2*pi*radius*height)+(2*pi*radius*radius);
System.out.println("the area of cylinder is " +a);
}
public void volume()
{
double v=pi*radius*radius*height;
System.out.println("the volume of cylinder is "+v);
}
}
class slipno11a
{
public static void main(String args[]) throws Exception
{
Cylinder C1=new Cylinder();
C1.input();
C1.area();
C1.volume();
}
}
========================================================================
==============================================
Slip11_2:
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
class InvalidPasswordException extends Exception
{}
class Userpassword extends JFrame implements ActionListener
{
JLabel name, pass;
JTextField nameText;
JPasswordField passText;
JButton login, end;
static int cnt=0;
Userpassword()
{
name = new JLabel("Name : ");
pass = new JLabel("Password : ");
nameText = new JTextField(20);
passText = new JPasswordField(20);
login = new JButton("Login");
end = new JButton("End");
login.addActionListener(this);
end.addActionListener(this);
setLayout(new GridLayout(3,2));
add(name);
add(nameText);
add(pass);
add(passText);
add(login);
add(end);
setTitle("Login Check");
setSize(300, 300);
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
setVisible(true);
}
public void actionPerformed (ActionEvent e)
{
if(e.getSource()==end)
{
System.exit(0);
}
if(e.getSource()==login)
{
try
{
String user = nameText.getText();
String pass = new String(passText.getPassword());
if(user.compareTo(pass)==0)
{
JOptionPane.showMessageDialog(null, "Login Successful",
"Login", JOptionPane. INFORMATION_MESSAGE);
System.exit(0);
}
else
{
throw new InvalidPasswordException();
}
}
catch(Exception e1)
{
cnt++;
JOptionPane.showMessageDialog(null, "Login Failed", "Login",
JOptionPane.ERROR_MESSAGE);
nameText.setText("");
passText.setText("");
nameText.requestFocus();
if(cnt==3)
{
JOptionPane.showMessageDialog(null,"3 Attempts Over",
"Login", JOptionPane.ERROR_MESSAGE);
System.exit(0);
}
}
}
}
public static void main(String args[])
{
new Userpassword();
}
}
========================================================================
==============================================
Slip12_1: Write a program to create parent class College(cno, cname, caddr) and derived
classDepartment(dno, dname) from College. Write a necessary methods to display College
details.
import java.util.*;
class college
{
int no;
String name;
String addr;
}
class Dept extends college
{
int dno;
String dname;
Scanner sc = new Scanner(System.in);
public void accept()
{
System.out.println("enter no");
no=sc.nextInt();
System.out.println("enter name");
name=sc.next();
System.out.println("enter college address");
addr=sc.next();
System.out.println("enter depatrment no");
dno=sc.nextInt();
System.out.println("enter department name");
dname=sc.next();
}
public void display()
{
System.out.println("college no"+no);
System.out.println("college name"+name);
System.out.println("college address"+addr);
System.out.println("department number"+dno);
System.out.println("department number"+dname);
}
public static void main(String a[])
{
Dept ob=new Dept();
ob.accept();
ob.display();
}
}
========================================================================
==============================================
Slip12_2:
import java.awt.*;
import java.awt.event.*;
class FrameDemo extends Frame implements ActionListener
{
Float a,b,c;
int ch;
TextField t1;
Button bmul,b1,b2,b3,b4,b5,b6,b7,b8,b9,b0,bdot,badd,bsub,bdiv,bequal;
FrameDemo()
{
setVisible(true);
setSize(500,500);
setTitle("calculator");
setLayout(new FlowLayout());
b1=new Button("1");
b2=new Button("2");
b3=new Button("3");
b4=new Button("4");
b5=new Button("5");
b6=new Button("6");
b7=new Button("7");
b8=new Button("8");
b9=new Button("9");
b0=new Button("0");
bdot=new Button(".");
badd=new Button("+");
bsub=new Button("-");
bmul=new Button("*");
bdiv=new Button("/");
bequal=new Button("=");
t1=new TextField(15);
Panel P1=new Panel();
P1.setLayout(new GridLayout(4,4,10,20));
P1.add(b1);
P1.add(b2);
P1.add(b3);
P1.add(b4);
P1.add(b5);
P1.add(b6);
P1.add(b7);
P1.add(b8);
P1.add(b9);
P1.add(b0);
P1.add(bdot);
P1.add(badd);
P1.add(bsub);
P1.add(bmul);
P1.add(bdiv);
P1.add(bequal);
add(t1);
add(P1);
b1.addActionListener(this);
b2.addActionListener(this);
b3.addActionListener(this);
b4.addActionListener(this);
b5.addActionListener(this);
b6.addActionListener(this);
b7.addActionListener(this);
b8.addActionListener(this);
b9.addActionListener(this);
b0.addActionListener(this);
bdot.addActionListener(this);
badd.addActionListener(this);
bsub.addActionListener(this);
bmul.addActionListener(this);
bdiv.addActionListener(this);
bequal.addActionListener(this);
}
public void actionPerformed(ActionEvent ae)
{
if(ae.getSource()==b1)
t1.setText(t1.getText()+"1");
if(ae.getSource()==b2)
t1.setText(t1.getText()+"2");
if(ae.getSource()==b3)
t1.setText(t1.getText()+"3");
if(ae.getSource()==b4)
t1.setText(t1.getText()+"4");
if(ae.getSource()==b5)
t1.setText(t1.getText()+"5");
if(ae.getSource()==b6)
t1.setText(t1.getText()+"6");
if(ae.getSource()==b7)
t1.setText(t1.getText()+"7");
if(ae.getSource()==b8)
t1.setText(t1.getText()+"8");
if(ae.getSource()==b9)
t1.setText(t1.getText()+"9");
if(ae.getSource()==b0)
t1.setText(t1.getText()+"0");
if(ae.getSource()==bdot)
t1.setText(t1.getText()+".");
if(ae.getSource()==badd)
{
ch=1;
a=Float.parseFloat(t1.getText());
t1.setText("");
}if(ae.getSource()==bsub)
{
ch=2;
a=Float.parseFloat(t1.getText());
t1.setText("");
}if(ae.getSource()==bmul)
{
ch=3;
a=Float.parseFloat(t1.getText());
t1.setText("");
}if(ae.getSource()==bdiv)
{
ch=4;
a=Float.parseFloat(t1.getText());
t1.setText("");
}if(ae.getSource()==bequal)
{
b=Float.parseFloat(t1.getText());
switch(ch)
{
case 1:c=a+b;break;
case 2:c=a-b;break;
case 3:c=a*b;break;
case 4:c=a/b;break;
}
t1.setText(""+c);
}
}
public static void main(String arg[])
{
new FrameDemo();
}
}
========================================================================
==============================================
Slip13_1:
import java.io.*;
class slip13_1
{
public static void main(String argd[]) throws Exception
{
String fname=argd[0];
File f=new File(fname);
if(f.isFile())
{
FileInputStream fis=new FileInputStream(fname);
int ch,cnt=0;
while((ch=fis.read())!=-1)
{
if(ch=='\n')
{
cnt++;
}
}
System.out.println("Number of line in Given file is "+cnt);
}
else
{
System.out.println("file not exists");
}
}
}
========================================================================
==============================================
Slip 13_2: Write a program to display the system date and time in various
formats shown below:Current date is : 31/08/2021
Current date is : 08-31-2021
Current date is : Tuesday August 31 2021
Current date and time is : Fri August 31
15:25:59 IST 2021Current date and time is :
31/08/21 15:25:59 PM +0530
import java.text.SimpleDateFormat;
import java.util.Date;
class slip13_2
{
public static void main(String[] args)
{
Date date = new Date();
SimpleDateFormat formatter = new SimpleDateFormat("dd/MM/yyyy");
String strDate= formatter.format(date);
System.out.println(strDate);
SimpleDateFormat formatter1 = new SimpleDateFormat("MM-dd-yyyy");
String strDate1= formatter1.format(date);
System.out.println(strDate1);
SimpleDateFormat formatter2 = new SimpleDateFormat("EEEEE
MMMMM dd yyyy");
String strDate2= formatter2.format(date);
System.out.println(strDate2);
SimpleDateFormat formatter3 = new SimpleDateFormat("EEEEE
MMMMM dd HH:mm:ss z yyyy");
String strDate3= formatter3.format(date);
System.out.println(strDate3);
SimpleDateFormat formatter4 = new SimpleDateFormat("dd/MM/yyyy
HH:mm:ss a");
String strDate4= formatter4.format(date);
System.out.println(strDate4);
}
}
========================================================================
==============================================
Slip14_1: Write a program to accept a number from the user, if number is zero then throw user
definedexception “Number is 0” otherwise check whether no is prime or not (Use static
keyword).
import java.util.Scanner;
import java.util.*;
class Zerono extends Exception
{}
class Prime
{
static int count=0;
public static void main(String args[])
{
int no,i,j;
Scanner sc=new Scanner(System.in);
try
{
System.out.println("enter no");
no=sc.nextInt();
if(no==0)
throw new Zerono();
if(no>0)
{
for(i=2;i<=no/2;i++)
{
if(no%i==0)
{
count++;
}
}
}
if(count==0)
System.out.println("No is Prime");
else
System.out.println("Not a Prime number");
}
catch(Zerono ob)
{
System.out.println("no can not be zero");
}
}
}
========================================================================
==============================================
Slip14_2:
Package
package SY;
public class SYMarks
{
int ct,mt,et;
public SYMarks(int ct,int mt,int et)
{
this.ct=ct;
this.mt=mt;
this.et=et;
}
public void display()
{
System.out.println("\nMarks are;");
System.out.println("Computer\tMaths\tElectronics");
System.out.println(ct+"\t"+mt+"\t"+et);
}
}
Package 2
package TY;
public class TYMarks
{
int Theory,Practicals;
public TYMarks(int Theory,int Practicals)
{
this.Theory=Theory;
this.Practicals=Practicals;
}
public void display()
{
System.out.println("\nMarks are:");
System.out.println("Theory\tPracticals");
System.out.println(Theory+"\t"+Practicals);
}
}
Mainfile
import SY.SYMarks;
import TY.TYMarks;
import java.io.*;
class SYTY
{
int rollno;
int ComputerTotal, MathsTotal, ElecTotal, Theory, Practicals;
String name;
BufferedReader br =new BufferedReader(new InputStreamReader(System.in));
public SYTY()
{}
public SYTY(int rollno,String name) throws Exception
{
this.rollno = rollno;
this.name = name;
System.out.println("Enter SY marks: ");
System.out.println("\nEnter computer marks");
ComputerTotal = Integer.parseInt(br.readLine());
while((ComputerTotal<0 || ComputerTotal>100))
{
System.out.println("\n\tInvalid marks.....");
System.out.println("Please ReEnter the marks: ");
ComputerTotal = Integer.parseInt(br.readLine());
}
System.out.println("\nEnter maths marks");
MathsTotal=Integer.parseInt(br.readLine());
while((MathsTotal<0 || MathsTotal>100))
{
System.out.println("\n\tInvalid marks.....");
System.out.println("Please Reenter the marks: ");
MathsTotal=Integer.parseInt(br.readLine());
}
System.out.println("\nEnter electronics marks");
ElecTotal = Integer.parseInt(br.readLine());
while((ElecTotal<0 || ElecTotal>100))
{
System.out.println("\n\tInvalid marks.....");
System.out.println("Please Reenter the marks: ");
ElecTotal = Integer.parseInt(br.readLine());
}
SYMarks sy = new SYMarks(ComputerTotal, MathsTotal, ElecTotal);
System.out.print("\nEnter TY marks: ");
System.out.print("\nEnter theory marks ");
Theory = Integer.parseInt(br.readLine());
while((Theory<0 || Theory>100))
{
System.out.println("\n\tInvalid marks.....");
System.out.println("Please Reenter the marks: ");
Theory = Integer.parseInt(br.readLine());
}
System.out.print("\nEnter practicals marks ");
Practicals = Integer.parseInt(br.readLine());
while((Practicals<0 || Practicals>100))
{
System.out.println("\n\tInvalid marks.....");
System.out.println("Please Reenter the marks: ");
Practicals = Integer.parseInt(br.readLine());
}
TYMarks ty = new TYMarks(Theory, Practicals);
CalculateGrade();
}
public void getdata() throws Exception
{
System.out.println("\nEnter number of students: ");
int n=Integer.parseInt(br.readLine());
SYTY object[]=new SYTY[n];
for(int i=0; i<n; i++)
{
System.out.println("\nEnter name: ");
String name = br.readLine();
System.out.println("\nEnter roll no: ");
int roll = Integer.parseInt(br.readLine());
object[i] = new SYTY(roll,name);
System.out.println("----------------------");
}
}
public void CalculateGrade()
{
double percentage;
percentage = (ComputerTotal+ MathsTotal + ElecTotal + Theory +
Practicals)/5;
System.out.println("Result:");
if(percentage >= 70)
System.out.println("Grade:A");
else if(percentage >= 60)
System.out.println("Grade:B");
else if(percentage >= 50)
System.out.println("Grade:C");
else if(percentage >= 40)
System.out.println("Grade:PASS");
else
System.out.println("Grade:FAIL\n\tTry Again..........");
}
public static void main(String args[]) throws Exception
{
SYTY st = new SYTY();
st.getdata();
}
}
========================================================================
==============================================
Slip18_1:
import java.awt.*;
import javax.swing.*;
class FrameDemo extends JFrame
{
FrameDemo()
{
JButton b1=new JButton("North");
JButton b2=new JButton("South");
JButton b3=new JButton("East");
JButton b4=new JButton("West");
JButton b5=new JButton("Center");
setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
add(b1,BorderLayout.NORTH);
add(b2,BorderLayout.SOUTH);
add(b3,BorderLayout.EAST);
add(b4,BorderLayout.WEST);
add(b5,BorderLayout.CENTER);
setSize(300,300);
setVisible(true);
}
public static void main(String[] args)
{
FrameDemo ob=new FrameDemo();
}
}
========================================================================
==============================================
Slip18_2:Define a class CricketPlayer (name,no_of_innings,no_of_times_notout, totatruns,
bat_avg).Create an array of n player objects. Calculate the batting average for each player
using staticmethod avg(). Define a static sort method which sorts the array on the
basis of average.Display the player details in sorted order.
import java.util.Scanner;
class cricket
{
int inning, tofnotout, totalruns;
String name;
float batavg;
int i;
cricket()
{
name= null;
inning= 0;
tofnotout= 0;
totalruns=0;
batavg= 0;
}
void get()
{
Scanner s1= new Scanner(System.in);
System.out.println("name, no of innings, no of time(s) not out, total runs");
name= s1.nextLine();
inning= s1.nextInt();
tofnotout= s1.nextInt();
totalruns= s1.nextInt();
}
void put()
{
System.out.println("name: "+name);
System.out.println("no of innings: "+inning);
System.out.println("no of time(s) not out: "+tofnotout);
System.out.println("total runs: "+totalruns);
System.out.println("batting average: "+batavg);
}
static void avg(int n, cricket c[])
{
for(int i=0; i<n; i++)
{
c[i].batavg= c[i].totalruns/c[i].inning;
}
}
static void sort(int n, cricket c[])
{
String temp1;
int temp2, temp3, temp4;
float temp5;
for(int i=0; i<n; i++)
{
for(int j=i+1; j<n; j++)
{
if(c[i].batavg<c[j].batavg)
{
temp1= c[i].name;
c[i].name= c[j].name;
c[j].name= temp1;
temp2= c[i].inning;
c[i].inning= c[j].inning;
c[j].inning= temp2;
temp3= c[i].tofnotout;
c[i].tofnotout= c[j].tofnotout;
c[j].tofnotout= temp3;
temp4= c[i].totalruns;
c[i].totalruns= c[j].totalruns;
c[j].totalruns= temp4;
temp5= c[i].batavg;
c[i].batavg= c[j].batavg;
c[j].batavg= temp5;
}
}
}
}
}
class setBb
{
public static void main(String args[])
{
Scanner s1= new Scanner(System.in);
System.out.println("Enter The Limit: ");
int n= s1.nextInt();
cricket c[]= new cricket[n];
for(int i=0; i<n; i++)
{
c[i]= new cricket();
c[i].get();
}
cricket.avg(n, c);
cricket.sort(n,c);
for(int i=0; i<n; i++)
{
c[i].put();
}
}
}
========================================================================
==============================================
Slip20_1: Write a Program to illustrate multilevel Inheritance such that country is
inherited from continent. State is inherited from country. Display the place, state,
country and continent.
import java.util.*;
class continent
{
String c1;
}
class country extends continent
{
String c2;
}
class state extends country
{
String s1;
String p1;
public void display()
{
System.out.println("Continent name: "+c1+"\n"+"Country name:
"+c2+"\n"+"State Name: "+s1+"\n"+"Place: "+p1);
}
public static void main(String args[])
{
state ob=new state();
Scanner sc=new Scanner(System.in);
System.out.println("Enter the continent");
ob.c1=sc.next();
System.out.println("Enter the Country");
ob.c2=sc.next();
System.out.println("Enter the state");
ob.s1=sc.next();
System.out.println("Enter the place");
ob.p1=sc.next();
ob.display();
}
}
========================================================================
==============================================
Slip20_2:
import java.util.*;
class Addition
{
public int ans,n1,n2;
public float answer,num1,num2;
public Addition(int n1,int n2,float num1,float num2)
{
this.n1=n1;
this.n2=n2;
this.num1=num1;
this.num2=num2;
}
public void add()
{
ans=n1+n2;
System.out.println("addition is="+ans);
}
public void sub()
{
answer=num1-num2;
System.out.println("subtraction is="+answer);
}
}
public class Maximum extends Addition
{
public Maximum(int n1,int n2, float num1, float num2)
{
super(n1,n2,num1,num2);
}
public void max()
{
if (n1>n2)
System.out.println(n1+" is greater than "+n2);
else
System.out.println(n2+" is greater than "+n1);
}
}
MainFile
import operation.Maximum;
import java.util.*;
class Arithmatic
{
public static void main (String args[])
{
int n1,n2;
float num1,num2;
Scanner sc=new Scanner(System.in);
System.out.println("Enter first no=");
n1=sc.nextInt();
System.out.println("Enter second no=");
n2=sc.nextInt();
System.out.println("Enter third no=");
num1=sc.nextFloat();
System.out.println("Enter fourth no=");
num2=sc.nextFloat();
Maximum ob1=new Maximum(n1,n2,num1,num2);
ob1.add();
ob1.sub();
ob1.max();
}
}
========================================================================
==============================================
Slip21_1: Define a class MyDate(Day, Month, year) with methods to accept and display a
MyDateobject. Accept date as dd,mm,yyyy. Throw user defined exception
"InvalidDateException" if the date is invalid.
import java.util.*;
class InvalidDateException extends Exception
{
}
class MyDate
{
int day,month,year;
public void accept()
{
System.out.println("Enter Date, Month and Year");
try
{
Scanner sc=new Scanner(System.in);
day=sc.nextInt();
if(day<1 || day>31)
throw new InvalidDateException();
month=sc.nextInt();
if(month>12 ||month<1)
throw new InvalidDateException();
year=sc.nextInt();
if(year>10000 ||year<1000)
throw new InvalidDateException();
}
catch(InvalidDateException e)
{
System.out.println("Invalid Date entered");
System.exit(0);
}
catch(Exception e)
{
System.out.println("Enter Valid Date");
System.exit(0);
}
}
}
public void display()
{
System.out.println("Entered Date is "+day+":"+month+":"+year);
}
public static void main(String args[])
{
MyDate ob=new MyDate();
ob.accept();
ob.display();
}
========================================================================
==============================================
Slip21_2: Create an employee class(id,name,deptname,salary). Define a default and
parameterized constructor. Use ‘this’ keyword to initialize instance variables. Keep a
count of objects created. Create objects using parameterized constructor and display the
object count after each object is created. (Use static member and method). Also display
the contents of each object.
class Employee
{
int id;
String name,deptname;
double sal;
static int cnt=0;
Employee()
{
cnt++;
displayCount();
}
Employee(int id,String name,String deptname,double sal)
{
this.id=id;
this.name=name;
this.deptname=deptname;
this.sal=sal;
cnt++;
displayCount();
}
public static void displayCount()
{
System.out.println("Total Objects created "+cnt);
}
public void displayData()
{
System.out.println(this.id+"\t\t"+this.name+"\t\t\t"+this.deptname+"\t\t"+this.sal);
}
public static void main(String args[])
{
Employee e1=new Employee(101,"Maithili","HR",120020.20);
Employee e2=new Employee(102,"Soham","IT",140020.20);
Employee e3=new Employee(104,"Akshay","Accounts",100020.20);
System.out.println("EID\t\tName\t\t\tDepartment\t\tSalary");
e1.displayData();
e2.displayData();
e3.displayData();
}
}
========================================================================
==============================================
Slip25_1:Create a class Student(rollno, name ,class, per), to read student information
from the console and display them (Using BufferedReader class)
import java.io.* ;
class Student
{
public static void main(String args[])throws Exception
{
InputStreamReader r=new InputStreamReader(System.in);
BufferedReader br=new BufferedReader(r);
System.out.println("Enter name:");
String name = br.readLine();
System.out.println("Enter roll no.:");
String number=br.readLine();
System.out.println("Enter percentage:");
String marks=br.readLine();
System.out.println("Enter class");
String classname=br.readLine();
System.out.println("name:"+name);
System.out.println("Roll No.:"+number);
System.out.println("Marks:"+marks);
System.out.println("Class:"+classname);
}
}
========================================================================
==============================================
Slip25_2:
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
public class HobbiesDemo extends JFrame implements ActionListener,ItemListener
{
JLabel l1,l2,l3,l4,l5;
JTextField tf1;
JRadioButton rb1,rb2,rb3;
ButtonGroup bg;
JCheckBox cb1,cb2,cb3;
JPanel p1,p2,p3,p4;
HobbiesDemo ()
{
l1=new JLabel("Your Name : ");
l2=new JLabel("Your Class :");
l3=new JLabel("Your Hobbies :");
l4=new JLabel(" ");
l5=new JLabel(" ");
tf1=new JTextField();
rb1=new JRadioButton("FY");
rb2=new JRadioButton("SY");
rb3=new JRadioButton("TY");
rb1.addActionListener(this);
rb2.addActionListener(this);
rb3.addActionListener(this);
bg=new ButtonGroup();
bg.add(rb1);
bg.add(rb2);
bg.add(rb3);
cb1=new JCheckBox("Music");
cb2=new JCheckBox("Dance");
cb3=new JCheckBox("Sports");
cb1.addItemListener(this);
cb2.addItemListener(this);
cb3.addItemListener(this);
p1=new JPanel();
p1.setLayout(new GridLayout(1,2));
p1.add(l1); p1.add(tf1);
p2=new JPanel();
p2.setLayout(new GridLayout(4,1));
p2.add(l2);
p2.add(rb1);
p2.add(rb2);
p2.add(rb3);
p3=new JPanel();
p3.setLayout(new GridLayout(4,1));
p3.add(l3);
p3.add(cb1);
p3.add(cb2);
p3.add(cb3);
p4=new JPanel();
p4.setLayout(new GridLayout(1,2));
p4.add(l4);
p4.add(l5);
BorderLayout bob=new BorderLayout();
setLayout(bob);
add(p1,BorderLayout.NORTH);
add(p2,BorderLayout.WEST);
add(p3,BorderLayout.EAST);
add(p4,BorderLayout.SOUTH);
setTitle("INFORMATION");
setSize(500,300);
setVisible(true);
setDefaultCloseOperation(EXIT_ON_CLOSE);
}
public void actionPerformed(ActionEvent ae)
{
String s="NAME : "+tf1.getText()+ " CLASS : " +ae.getActionCommand();
l4.setText(s);
}
public void itemStateChanged(ItemEvent ie)
{
String s="";
if(cb1.isSelected())
s=s+cb1.getText()+" ";
if(cb2.isSelected())
s=s+cb2.getText()+" ";
if(cb3.isSelected())
s=s+cb3.getText()+" ";
l5.setText(" HOBBIES : "+s);
}
public static void main(String args[])
{
HobbiesDemo hob=new HobbiesDemo();
}
}
========================================================================
==============================================
Slip26_1: Define a Item class (item_number, item_name, item_price). Define a default
and parameterized constructor. Keep a count of objects created. Create objects using
parameterized constructor and display the object count after each object is created.(Use
static member and method). Also display the contents of each object
class Item
{
int ino;
String iname;
double iprice;
static int count=0;
Item()
{ }
Item(int no,String nm,double d)
{
ino=no;
nm=iname;
iprice=d;
count++;
}
public void display()
{
System.out.println("Total objects created "+count);
System.out.println(ino+" "+iname+" "+iprice);
}
public static void main(String args[])
{
Item ob1=new Item(1,"Laptop",20000.00);
ob1.display();
Item ob2=new Item(1,"Laptop",20000.00);
ob2.display();
}
}
========================================================================
==============================================
Slip26_2: Define a class ‘Donor’ to store the below mentioned details of a blood donor.
name, age, address, contactnumber, bloodgroup, date of last donation. Create ‘n’ objects
of this class for all the regular donors at Pune. Write these objects to a file. Read these
objects from the file and display only those donors’ details whose blood group is ‘A+ve’
and had not donated for the recent six months.
import java.io.*;
import java.util.*;
class Donor
{
String name, address,group;
int age, contact, lod;
public Donor(String Name,String address, String group,int age,int contact,int lod)
{
this.name=name;
this.address=address;
this.group=group;
this.age=age;
this .contact=contact;
this.lod=lod;
}
public static void main(String args[])
{
Scanner s=new Scanner(System.in);
System.out.println("Enter how many records you want");
int n=s.nextInt();
try
{
ObjectOutputStream o=new ObjectOutputStream(new FileOutputStream("save.txt"));
Donor d[]=new Donor[n];
for(int i=0;i<n;i++)
{
System.out.println("Name: ");
String name=s.next();
System.out.println("Age: ");
int age=s.nextInt();
System.out.println("Address: ");
String address=s.next();
System.out.println("Contact: ");
String contact=s.next();
System.out.println("Group: ");
String group=s.next();
System.out.println("Last donation: ");
int lod=s.nextInt();
o.writeObject(d[i]);
}
}
catch(IOException e)
{
System.out.println(e);
}
try
{
ObjectInputStream z=new ObjectInputStream(new FileInputStream("save.txt"));
for(int i=0;i<n;i++)
{
Donor d=(Donor)z.readObject();
if(d.group.equals("A+ve")&&d.lod>=6)
System.out.println(d);
}
}
catch(Exception e)
{
System.out.println(e);
}
}
}
========================================================================
==============================================
Slip29_1:
import java.util.Scanner;
class Customer
{
int cno;
String cname,cmob,cadd;
public static void main(String [] args)
{
int i=0;
{
Scanner sc = new Scanner(System.in);
Customer ob[]=new Customer[5];
for(i=0;i<5;i++)
{
System.out.println("Enter cno,cname,cmob,cadd");
ob[i]=new Customer();
ob[i].cno=sc.nextInt();
ob[i].cname=sc.next();
ob[i].cmob=sc.next();
ob[i].cadd=sc.next();
}
String mb;
System.out.print("enter mob to search");
for(i=0;i<5;i++)
{
if(mb.equals(ob[i]).cmob)
{
System.out.println("Name"+ob[i].cname);
}
}
}
}
}
========================================================================
==============================================
Slip29_2:
import java.io.*;
class Vehicle
{
String company;
double price;
public void accept() throws IOException
{
System.out.println("Enter the Company and price of the
Vehicle: ");
BufferedReader br=new BufferedReader(new
InputStreamReader(System.in));
company=br.readLine();
price=Double.parseDouble(br.readLine());
}
public void display()
{
System.out.println("Company: "+company+" Price: "+price);
}
}
class LightMotorVehicle extends Vehicle
{
double mileage;
public void accept() throws IOException
{
super.accept();
System.out.println("Enter the mileage of the vehicle: ");
BufferedReader br=new BufferedReader(new
InputStreamReader(System.in));
mileage=Double.parseDouble(br.readLine());
}
public void display()
{
super.display();
System.out.println("Mileage: "+mileage);
}
}
class HeavyMotorVehicle extends Vehicle
{
double captons;
public void accept() throws IOException
{
super.accept();
System.out.println("Enter the capacity of vehicle in tons: ");
BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
captons=Double.parseDouble(br.readLine());
}
public void display()
{
super.display();
System.out.println("Capacity in tons: "+captons);
}
}
class Sa3
{
public static void main(String [] args) throws IOException
{
int i;
System.out.println("Enter the type of vehicle: ");
BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
System.out.println("1.Light Vehicle");
System.out.println("2.Heavy Vehicle");
int ch=Integer.parseInt(br.readLine());
switch(ch)
{
case 1:
System.out.println("Enter the number of Light vehicles: ");
int n=Integer.parseInt(br.readLine());
LightMotorVehicle [] l=new LightMotorVehicle[n];
for(i=0;i<n;i++)
{
l[i]=new LightMotorVehicle();
l[i].accept();
}
for(i=0;i<n;i++)
{
l[i].display();
}
break;
case 2:
System.out.println("Enter the number of Heavy vehicles: ");
int m=Integer.parseInt(br.readLine());
HeavyMotorVehicle [] h=new HeavyMotorVehicle[m];
for(i=0;i<m;i++)
{
h[i]=new HeavyMotorVehicle();
h[i].accept();
}
for(i=0;i<m;i++){
h[i].display();
}
break;
}
}
}
========================================================================
==============================================
