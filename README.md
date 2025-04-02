1
#include<iostream>
using namespace std;


inline int max(int a, int b) {
   return ((a > b) ? a : b);
}

inline int min(int a, int b) {
    return ((a < b) ? a : b);
}

int main() {
    int a, b;

    cout << "Enter 2 numbers" << endl;
    cout << "Number 1: ";
    cin >> a;
    cout << "Number 2: ";
    cin >> b;

    cout << "The maximum number is: " << max(a, b) << endl;
    cout << "The minimum number is: " << min(a, b) << endl;

    return 0;
}
#include <stdio.h>
#include <stdlib.h>
#include <istream>
#include <conio.h>
#include <ctype.h>
#include <fstream>
#include <iostream>

using namespace std;

#include <string.h>
#define MAXSIZE (10)

class myfile
{
    FILE *fp;
    char fn[MAXSIZE];

public:
    myfile(const char *fname)
    {
        strcpy(fn, fname);
    }
    myfile operator+(myfile);
    void operator!();
    void display();
};
void myfile::display()
{
    fp = fopen(fn, "r");
    char ch;
    while ((ch = fgetc(fp)) != EOF)
    {
        cout << ch;
    }
    fclose(fp);
}
void myfile::operator!()
{
    myfile f4("sy.txt");
    char ch;
    fp = fopen(fn, "r");
    f4.fp = fopen(f4.fn, "w");
    while ((ch = fgetc(fp)) != EOF)
    {
        if (isupper(ch))
            fputc(tolower(ch), f4.fp);
        else if (islower(ch))
            fputc(toupper(ch), f4.fp);
        else
            fputc(ch, f4.fp);
    }
    fclose(fp);
    fclose(f4.fp);
    remove("abc.txt");
    rename("sy.txt", "abc.txt");
}
myfile myfile::operator+(myfile f2)
{
    myfile f3("abc.txt");
    fp = fopen(fn, "r");
    f2.fp = fopen(f2.fn, "r");
    f3.fp = fopen(f3.fn, "w");
    char ch;
    while ((ch = fgetc(fp)) != EOF)
    {
        fputc(ch, f3.fp);
    }
    fclose(fp);
    while ((ch = fgetc(f2.fp)) != EOF)
    {
        fputc(ch, f3.fp);
    }
    _fcloseall();
    return f3;
}
int main()
{
    myfile f1("xyz.txt");
    myfile f2("lmn.txt");
    myfile f3("abc.txt");

    cout << "first file \n";
    f1.display();
    cout << "\nsecond file \n";
    f2.display();
    f3 = f1 + f2;
    cout << "\nAfter concatnation file is ";
    f3.display();
    cout << "\nAfter changes case \n";
    !f3;
    f3.display();

    return 0;
}
<?php
class MyCalculator {
private $_fval, $_sval;
public function __construct( $fval, $sval ) {
$this->_fval = $fval;
$this->_sval = $sval;
}
public function add() {
return $this->_fval + $this->_sval;
}
public function subtract() {
return $this->_fval - $this->_sval;
}
public function multiply() {
return $this->_fval * $this->_sval;
}
public function divide() {
return $this->_fval / $this->_sval;
}
}
$mycalc = new MyCalculator(12, 6); 
echo $mycalc-> add()."\n"; // Displays 18 
echo $mycalc-> multiply()."\n"; // Displays 72
echo $mycalc-> subtract()."\n"; // Displays 6
echo $mycalc-> divide()."\n"; // Displays 2
?>
<html>
<script type="text/javascript">
function display()
{
	name=f1.txt.value;
	var xmlhttp;
	if(window.XMLHttpRequest)
	{
		xmlhttp= new XMLHttpRequest();
	}
	else
	{
		xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
	}
        xmlhttp.open("GET", "slip1-p2-q2.php?txt="+ name,false);
        xmlhttp.send();
        document.getElementById('result').innerHTML=
        		xmlhttp.responseText;
}
</script>
<body>
	<form name="f1">
		Enter Employee name:
		<input type="text" name="txt" onKeyUp="display()"/><br>
	</form>
	 <div id='result'></div> 
	</body>
	</html>	

slip1-p1-q2.xml
<?xml version="1.0"?>
<Movie_Store>
<Movie>
<Category>Biography</Category>
<MovieName>Dangal</MovieName>
<ReleaseYear>2016</ReleaseYear>
</Movie>
<Movie>
<Category>Action</Category>
<MovieName>Tanhaji</MovieName>
<ReleaseYear>2020</ReleaseYear>
</Movie>
<Movie>
<Category>Family</Category>
<MovieName>The Sky is Pink</MovieName>
<ReleaseYear>2019</ReleaseYear>
</Movie>
</Movie_Store>

slip1-p2-q2.php
<?php
$msearch=$_GET['txt'];
$xml=simplexml_load_file("slip1-p2-q2.xml");
echo $xml->getName()."<br>";
$hint="";
$len=strlen($msearch!=="");
if($msearch !=="")
{
	foreach($xml->children() as $student)
	{
		//if(strstr($movie->MovieName,substr($msearch,0,$len)))
		if(strcmp($msearch,$student->sname)==0)
		{
			$hint=" Student Name: $student->sname <br>
			       Cname: $student->cname<br>
			       Percentage:$student->percentage<br>";
		}
	}

}
 echo $hint==="" ? "no suggestion":$hint;
 ?>

slip1-p2-q2.xml
<Course>
<SYBBACA>
<sname>Harsh</sname >
<cname>SYBBACA</cname >
<percentage>82</percentage>
<sname>Yash</sname >
<cname>SYBBA</cname >
<percentage>90</percentage>
<sname>Aman</sname >
<cname>SYBBAIB</cname >
<percentage>67</percentage>
<sname>Ajay</sname >
<cname>FYBBAIB</cname >
<percentage>77</percentage>
<sname>Raj</sname >
<cname>FYBBA</cname >
<percentage>87</percentage>
</SYBBACA>
</Course>

2
#include<iostream>
using namespace std;

float volume(float r, float h) {
    return (3.14*r*2*h);
}

float coneVol(float r, float h) {
    return (3.14*r*2*h/3);
}

float volume(float r) {
    return (4/3*3.14*r*r*r);
}


int main() {
    float cy_h, cy_r, co_h, co_r, sp_r;

    cout << "Enter dimensions" << endl;

    cout << "1. Cylinder" << endl;
    cout << "Height: ";
    cin >> cy_h;
    cout << "Radius: ";
    cin >> cy_r;

    cout << endl;

    cout << "2. Cone" << endl;
    cout << "Height: ";
    cin >> co_h;
    cout << "Radius: ";
    cin >> co_r;

    cout << endl;

    cout << "3. Sphere" << endl;
    cout << "Radius: ";
    cin >> sp_r;

    cout << endl;

    cout << "The volume of Cylinder is: " << volume(cy_h, cy_r) << endl;
    cout << "The volume of Cone is: " << coneVol(co_h, co_r) << endl;
    cout << "The volume of Sphere is: " << volume(sp_r) << endl;

    return 0;
}
<?php
class Myclass
{
            public $a;
            public $b=305;
            public $c='Akshay';
            function Myclass()
    {
                        //Myclass function
            }
            function myfun1()
    {
                        //functin
    }
            function myfun2()
    {
                        //functin
    }
}
            $class=get_declared_classes();
            foreach($class as $cname)
            {
                        echo"$cname<br>";
            }
            echo"<br>Class Methods are : <br>";
            $m=get_class_methods('Myclass');
            foreach($m as $mname)
            {
                        echo"$mname<br>";
            }
            $cp=get_class_vars('Myclass');
            echo"class variables are :<br>";
            foreach($cp as $cpname => $v)
            {
                        echo"$cpname : $v <br>";
            }

?>

3
#include<iostream>
using namespace std;

void swap(int &a, int&b) {
    int temp;

    temp = a;
    a = b;
    b = temp;
}


int main() {
    int a,b;

    cout << "Enter two numbers" << endl;

    cout << "Enter first number: ";
    cin >> a;
    cout << "Enter second number: ";
    cin >> b;

    cout << endl << "Original Numbers" << endl << "a = " << a << " & b = " << b << endl;

    swap(a, b);

    cout << endl << "After swap Numbers" << endl << "a = " << a << " & b = " << b << endl;

    return 0;
}
#include <stdio.h>
#include <stdlib.h>
#include <istream>
#include <conio.h>
#include <ctype.h>
#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{

    int num;
    ofstream f1("even.txt"),f2("odd.txt"); 


    if (argc == 1)
        printf("No command line arguments found.\n");

    else
    {
        for(int i = 1; i < argc; i++)
        {
            num = atoi(argv[i]);
            if(num%2==0)
            {
                f1<<num;
            }
            else
            {
                f2<<num;
            }
        }
    }
    return 0;
}
<?php
class Calculate
      {public $a;
public $b;
function __construct($a,$b){
$this->a=$a;
$this->b=$b;
}
public function add()
         {
          $c=$this->a+$this->b;
echo"Addition = $c<br>";
         }
public function subtract()
         {
          $c=$this->a-$this->b;
echo"Subtract = $c<br>";
         }
public function multiply()
         {
          $c=$this->a*$this->b;
echo"Multiplication = $c<br>";
         }
public function div()
         {
          $c=$this->a/$this->b;
echo"Division = $c";
         } }
//$x=$_GET['a'];
//$y=$_GET['b'];
$calc=new Calculate(4,3);
$calc->add();
$calc->subtract();
$calc->multiply();
$calc->div();?>
<CricketTeam>
<Team country="India">
<player>ROHIT SHARMA</player>
<runs>2850</runs>
<wicket>5</wicket>
</Team>

<Team country="England">
<player>Ben Stokes</player>
<runs>2650</runs>
<wicket>25</wicket>
</Team>
<Team country="Australia">
<player>Steve Smith</player>
<runs>7000</runs>
<wicket>20</wicket>
</Team>
<Team country="West Indies">
<player>DJ BRAVO</player>
<runs>9000</runs>
<wicket>225</wicket>
</Team>
<Team country="Bangladesh">
<player>Shakib-al-Hasan</player>
<runs>4190</runs>
<wicket>135</wicket>
</Team>
</CricketTeam>

4
#include<iostream>
using namespace std;

class WorkerInformation {
    char Worker_Name[50];
    int No_Of_Hours_Worked, Salary;

    public:
        void acccept() {
            cout << "Enter name of the worker: ";
            cin >> Worker_Name;

            cout << "Enter number of hours worked: ";
            cin >> No_Of_Hours_Worked;

           
        }

        void display() {
            cout << endl << "Worker details" << endl;
            cout << "Name: " << Worker_Name << endl;
            cout << "Salary: " << calSal(No_Of_Hours_Worked) << endl;
        }

        int calSal(int work_hrs, int pay_rate=100) {
            return (work_hrs*pay_rate);
        }
};


int main() {
    WorkerInformation w;

    w.acccept();
    w.display();
    return 0;
}
#include<iostream>
using namespace std;
const int m=50;

class emp
{
        public:
                int empcode;
                char empname[30];
                int salary;
        public:
                void get()
                {
                        cout<<"\n Enter Employee No.   :  ";
                        cin>>empcode;
                        cout<<"\n Enter Employee Name  :  ";
                        cin>>empname;
                        
                }
};
class fulltime:public emp
{
        public:
                float daily_wages;
                int no_of_days;
                
        public:
                void getdata()
                {
                        cout<<"\n Enter Daily Rate     :  ";
                        cin>>daily_wages;
                        cout<<"\n Enter No. of Days    :  ";
                        cin>>no_of_days;
                }
                void cal()
                {
                        salary=daily_wages*no_of_days;
                        cout<<"\n Salary               :  "<<salary;
                }
                void show()
                {
                        cout<<"\n ----------------------------------\n";
                        cout<<"\n Employee Number    :  "<<empcode;
                        cout<<"\n Employee Name      :  "<<empname;
                        cout<<"\n Salary             :  "<<salary;
                        cout<<"\n Status             :  Fulltime";
                        cout<<"\n ----------------------------------\n";
                }
};
class parttime:public emp
{
        public:
                int hourly_wages;
                int working_hours;
                
        public:
                void get1()
                {
                        cout<<"\n Enter Hourly Rate    :  ";
                        cin>>hourly_wages;
                        cout<<"\n Enter Working Hours  :  ";
                        cin>>working_hours;
}
void cal1()
{
                        salary=hourly_wages*working_hours;
                        cout<<"\n Salary               :  "<<salary<<endl;
                }
                void show1()
                {
                        cout<<"\n ----------------------------------\n";
                        cout<<"\n Employee No     :  "<<empcode;
                        cout<<"\n Employee Name   :  "<<empname;
                        cout<<"\n Salary          :  "<<salary;
                        cout<<"\n Status          :  Part time";
                        cout<<"\n ----------------------------------\n";
                }
};
int main()
{

        int const cnt=5;
        int var=0;
        int var1=0;
        fulltime f1[cnt];
        parttime p1[cnt];

        int x,i;
        do
        {
                cout<<"\n";
                cout<<"\n 1.Enter Record";
                cout<<"\n 2.Display Record";
                cout<<"\n 3.Search Record";
                cout<<"\n 4.Quit";
                cout<<"\n\n Enter Your Choice : ";
                cin>>x;
                switch(x)
                {
                        case 1:
                                int y;
                                cout<<"\n 1. Fulltime Employee";
                                cout<<"\n 2. Parttime Employee \n";
                                cout<<"\n Enter : ";
                                cin>>y;
                                switch(y)
                                {
                                        case 1:
                                                f1[var].get();
                                                f1[var].getdata();
                                                f1[var].cal();
                                                var++;
                                                break;
                                        case 2:
                                                p1[var1].get();
                                                p1[var1].get1();
                                                p1[var1].cal1();
                                                var1++;
                                                break;
                                }
                                break;
                        case 2:
                                for(i=0; i<var; i++)
                                {
                                        f1[i].show();
                                }
                                for(i=0; i<var1; i++)
                                {
                                        p1[i].show1();
                                }
                        break;
                        case 3:
                                int a;
                                cout<<"\n Enter Employee No. : ";
                                cin>>a;
                                for (int i=0; i<var; i++)
                                {
                                        if (f1[i].empcode==a)
                                        {
                                                f1[i].show();
                                        }
                                        if(p1[i].empcode==a)
                                        {
                                                p1[i].show1();
                                        }
                                }
                }

        } while(x!=4);
return 0;
}
<?php
class Employee
{
private $eid,$ename,$edept,$sal;
function __construct($a,$b,$c,$d)
{
$this->eid=$a;
$this->ename=$b;
$this->edept=$c;
$this->sal=$d;
}
public function getdata()
{
return $this->sal;
}
public function display()
{
echo $this->eid."
";
echo $this->ename."
";
echo $this->edept."
";
}
}
class Manager extends Employee
{
private $bonus;
public static $total1=0;
function __construct($a,$b,$c,$d,$e)
{
parent::__construct($a,$b,$c,$d);
$this->bonus=$e;
}
public function max($ob)
{
$sal=$this->getdata();
$total=$sal+$this->bonus;
if($total>self::$total1)
{
self::$total1=$total;
return $this;
}
else
{
return $ob;
}
}
public function display()
{
parent::display();
echo self::$total1;
}

}
$ob=new Manager(0,"ABC","",0,0);
$ob1=new Manager(1,"ramdas","computer",28000,2000);
$ob=$ob1->max($ob);
$ob2=new Manager(2,"ramdas1","computer",30000,2500);
$ob=$ob2->max($ob);
$ob3=new Manager(3,"ramdas2","computer",32000,3000);
$ob=$ob3->max($ob);
$ob4=new Manager(4,"ramdas","computer",28000,4000);
$ob=$ob4->max($ob);
$ob5=new Manager(5,"ramdas","computer",28000,5000);
$ob=$ob5->max($ob);
$ob->display();
?>
<?php
$d=new DOMDocument();
$d->load("slip4-p1-q2.xml");

$run=$d->getElementsByTagName('runs');
$wic=$d->getElementsByTagName('wickets');
$name=$d->getElementsByTagName('player');

foreach($name as $n)
{
            if($run>='12*00' && $wic>='50')
            echo "<br>".$n->textContent;
            else "not";        
}
?>

slip4-p1-q2.xml
<?xml version='1.0' encoding='UTF-8'?>
<cricketinfo>
            <cricket>
                        <player>abc</player>
                        <runs>1000</runs>
                        <wickets>50</wickets>
                        <noofnotout>10</noofnotout>
            </cricket>

            <cricket>
                        <player>def</player>
                        <runs>100</runs>
                        <wickets>40</wickets>
                        <noofnotout>10</noofnotout>
            </cricket>

            <cricket>
                        <player>pqr</player>
                        <runs>1020</runs>
                        <wickets>60</wickets>
                        <noofnotout>10</noofnotout>
            </cricket>

            <cricket>
                        <player>xyz</player>
                        <runs>9000</runs>
                        <wickets>90</wickets>
                        <noofnotout>40</noofnotout>
            </cricket>

            <cricket>
                        <player>lmn</player>
                        <runs>170</runs>
                        <wickets>80</wickets>
                        <noofnotout>8</noofnotout>
            </cricket>
</cricketinfo>

8
include <iostream>

using namespace std;
class Number{
    public:
        void display(){
            static int cnt=1;
            cout<<"\nDisplay function is called "<<cnt<<" times"<<endl;
            cnt++;
        }
};
int main()
{
    Number n1,n2;
    n1.display();
    n1.display();
    n2.display();
    n2.display();
    return 0;
}
#include<iostream>
#include<conio.h>
#include<string.h>

using namespace std;
class person
{
	public:
   int no,mob; 
   char name[10],city[10];
   void acc() // function overloading 
   {
   	cout<<"\nEnter person no : ";
      cin>>no;
      cout<<"\nEnter person name : ";
      cin>>name;
      cout<<"\nEnter person city : ";
      cin>>city;
      cout<<"\nEnter person mob no : ";
      cin>>mob;

   }
   void acc(char nme[]) // function overloading 
   {
   	if(strcmp(nme,name)==0)
      {
      cout<<"\nPerson name   : "<<name;
      cout<<"\nPerson mob no : "<<mob<<endl;
      }
   }
   void acc(int mno)  // function overloading 
   {
   	if(mno==mob)
      {
      cout<<"\nPerson name   : "<<name;
      cout<<"\nPerson mob no : "<<mob<<endl;
      }
   }
   void dis()
   {
      cout<<"\nPerson details"<<endl;
      cout<<"\nPerson no     : "<<no;
      cout<<"\nPerson name   : "<<name;
      cout<<"\nPerson city   : "<<city;
      cout<<"\nPerson mob no : "<<mob<<endl;
   }

};
int main()
{
   char nme[10];
   int mno,i,no,ch;// mno=mobile no , no=total person no , ch=choice
   person p[20];
   do{
   cout<<"\n1.Accept person details\n2.Display person details\n3.To search the mobile number of a given person\n4.To search the Person details of a given mobile number\n5.Exit\nEnter your choice :- ";
   cin>>ch;
   switch(ch)
   {
   case 1:cout<<"Enter how many Person Details you want to enter: ";
   		 cin>>no;
          
          for(i=0;i<no;i++)
   		{
	 			p[i].acc();
   		}
         break;
   case 2:for(i=0;i<no;i++)
   		 p[i].dis();
          break;
   case 3:cout<<"\nEnter person name search for mob no : ";
   		 cin>>nme;
          for(i=0;i<no;i++)
  			 p[i].acc(nme);
          break;
   case 4:cout<<"\nEnter mob no search for person name : ";
  			 cin>>mno;
  			 for(i=0;i<no;i++)
  			 p[i].acc(mno);
          break;
   }
   }while(ch!=5);

   return 0;
}
<HTML>
<BODY bgcolor=blue>
<FORM ACTION="slip8-p2-q1.php" METHOD="post">
<pre>
<h1>Circle:</h1>

        Radius: <input type=text name=a><BR>

<h1>
square:</h1>

        side: <input type=text name=b><BR>
<h1>
Rectangle:
</h1>
        length: <input type=text name=c><BR>

        Breadth: <input type=text name=d><BR>
<input type=submit value=submit> <input type="reset" value=cancel>
</pre>
</form>
</BODY>
</HTML>

slip8-p2-q1.php
<HTML>
<BODY>
<?PHP
$a=$_POST['a'];
$b=$_POST['b'];
$c=$_POST['c'];
$d=$_POST['d'];

interface one
{
        function area($c,$d);
}
class rect implements one
{
        function area($c,$d)
        {
                $area=$c*$d;
                echo"Area of rectangle......:".$area;
                echo"<br><BR>";
        }
}
class square extends rect
{
        function area($b,$f)
        {
                $area=$b*$f;
                echo"Area of Square.........:".$area;
                echo"<BR><br>";
        }
}
class circle
{
        function area($a)
        {
                $area=3.14*$a*$a;
                echo"Area of circle.........:".$area;
                echo"<br><BR>";
        }
}
$o=new rect();
$o->area($c,$d);
$s=new square();
$f=$b;
$s->area($b,$f);
$c=new circle();
$c->area($a);
echo "<br>";
?>
<a href="a4b1.html">come back</a><br>
</BODY>
</html>
<html>
<script type="text/javascript">
function display()
{
	name=f1.txt.value;
	var xmlhttp;
	if(window.XMLHttpRequest)
	{
		xmlhttp= new XMLHttpRequest();
	}
	else
	{
		xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
	}
        xmlhttp.open("GET", "slip8-p1-q2.php?txt="+ name,false);
        xmlhttp.send();
        document.getElementById('result').innerHTML=
        		xmlhttp.responseText;
}
</script>
<body>
	<form name="f1">
		Enter Employee name:
		<input type="text" name="txt" onKeyUp="display()"/><br>
	</form>
	 <div id='result'></div> 
	</body>
	</html>	

slip8-p1-q2.php
<?php

$d=new DOMDocument();
$d->load("slip8-p1-q2.xml");

$run=$d->getElementsByTagName('runs');
$wic=$d->getElementsByTagName('wickets');
$name=$d->getElementsByTagName('player');

foreach($name as $n)
{
            if($a='')
            echo "<br>".$n->textContent;
           else "not";        
}
?>

slip8-p1-q2.xml
<?xml version='1.0' encoding='UTF-8'?>
<cricketinfo>
            <cricket>
                        <player>abc</player>
                        <runs>1000</runs>
                        <wickets>50</wickets>
                        <noofnotout>10</noofnotout>
            </cricket>

            <cricket>
                        <player>def</player>
                        <runs>100</runs>
                        <wickets>40</wickets>
                        <noofnotout>10</noofnotout>
            </cricket>

            <cricket>
                        <player>pqr</player>
                        <runs>1020</runs>
                        <wickets>60</wickets>
                        <noofnotout>10</noofnotout>
            </cricket>

            <cricket>
                        <player>xyz</player>
                        <runs>9000</runs>
                        <wickets>90</wickets>
                        <noofnotout>40</noofnotout>
            </cricket>

            <cricket>
                        <player>lmn</player>
                        <runs>170</runs>
                        <wickets>80</wickets>
                        <noofnotout>8</noofnotout>
            </cricket>
</cricketinfo>


10
#include<iostream.h>

#include<conio.h>

#include<stdlib.h>

 class Account

{

public:

int Acc_no,Balance;

char Acc_type[30];

public:

Account()  {  cout << "Constructor" << endl; }

~Account() { cout << "Destructor" << endl; }

void get_data()

{

cout<<"\n Enter Acc_no.:";

cin>>Acc_no;

cout<<"\n Enter Acc_type :";

cin>>Acc_type;

cout<<"\n Enter Balance :";

cin>>Balance;                    

}

void display_data()

{

cout<<"\t"<<Acc_no<<"\t"<<"\t"<<Acc_type<<"\t"<<Balance;      

}

};

int main()

{

 clrscr();

int num;

 Account* a = new Account[4];

delete [] a; // Delete array

 cout<<"\n How many records u want?: ";

cin>>num;

 for(int i=0;i<num;i++)

{

a[i].get_data();

}

for(i=0;i<num;i++)

{

a[i].display_data();

}

return 0;

 }

 Slip 10 - B) Create a C++ class City with data members City_code, City_name, population. Write necessary member functions for the following: i, Accept details of n cities ii. Display details of n cities in ascending order of population. iii. Display details of a particular city. (Use Array of object and to display city information use manipulators.)
 Solution:
#include<iostream.h>

#include<conio.h>

#include<iomanip.h>

#include<stdlib.h>

#include<string.h>

 void searchcity();

 char n[10],c[10];

 class city

 {

public:

int population,city_code;

char name[40],e[10];

 void accept()

{

 cout<<"\n Enter name of city:";

cin>>name;

 cout<<"\n Enter name of city_code:";

cin>>city_code;

 cout<<"\n Enter the population of city:";

cin>>population;

}

void sort(city &r1,city &r2)

{

city rt;

if(r1.population>r2.population)

{

 rt=r1;

 r1=r2;

 r2=rt;

}

}

 void display()

{

cout<<"\n Name of City :"<<setw(15)<<name<<endl;

cout<<"\n Population :"<<setw(15)<<population<<endl;

cout<<"\n City Code:"<<setw(15)<<city_code<<endl;

}

 void searchcity()

{

if(strcmp(name,c)==0)

{

cout<<"\n name: "<<name<<"\n Population.: "<<population;

}

}

};

void main()

{

clrscr();

city t[30];

int num,ch,population;

char cont;

cout<<"\n 1.Accept & display ";

cout<<"\n 2.Ascending";

cout<<"\n 3.Search by city";

do

 {

cout<<"\n Enter your choice: ";

cin>>ch;

switch(ch)

{

case 1: cout<<"\n How many records you want to enter: ";

cin>>num;

for(int i=0;i<num;i++)

{

t[i].accept();

}

 for(i=0;i<num;i++)

{

t[i].display();

}

 break;

 case 2:

 for(i=0;i<num;i++)

{

for(int j=i+1;j<num;j++)

t[i].sort(t[i],t[j]);

t[i].display();

}

 break;

 case 3: cout<<"\n Enter city name: ";

cin>>c;                                  

for(i=0;i<num;i++)

{

t[i].searchcity();

}

break;

}

 cout<<"\n Do you want to continue: ";

cin>>cont;

}

 while(cont=='Y'||cont=='y');

getch();

}

<?php
class Myclass
{
            public $a;
            public $b=305;
            public $c='Akshay';
            function Myclass()
    {
                        //Myclass function
            }
            function myfun1()
    {
                        //functin
    }
            function myfun2()
    {
                        //functin
    }
}
            $class=get_declared_classes();
            foreach($class as $cname)
            {
                        echo"$cname<br>";
            }
            echo"<br>Class Methods are : <br>";
            $m=get_class_methods('Myclass');
            foreach($m as $mname)
            {
                        echo"$mname<br>";
            }
            $cp=get_class_vars('Myclass');
            echo"class variables are :<br>";
            foreach($cp as $cpname => $v)
            {
                        echo"$cpname : $v <br>";
            }

?>
<html>
<body>
<form method="POST" action="<?php echo $_SERVER['PHP_SELF']; ?>">
Select options:

<input type="radio" value="push" name="d1">Push</input>
<input type="radio" value="pop" name="d1">Pop</input>
<input type="radio" value="display" name="d1">Display</input>
<input type="submit">
</form>
<?php
echo "
Index ARRAY.......
";
$a = array(1,2,3,4,5,6,7);
print_r($a);
print"<br>";
if($_SERVER["REQUEST_METHOD"] == "POST")
{
$opt = $_POST['d1'];
if($opt == 'push')
{
array_push($a,11);
print_r($a);
}

else if($opt == 'pop')
{
array_pop($a);
print_r($a);
}
else if($opt == 'display')
{
//array_pop($a);
print_r($a);
}

}
?>

12
#include<iostream>
#include<conio.h>

using namespace std;
class date
{
 int dd,mm,yy;
 public: 
 date(int d,int m,int y)
 {
 dd=d;
 mm=m;
 yy=y;
 }
 void display()
 {
 cout<<"\nGiven date is\t";
 cout<<dd<<"-"<<mm<<"-"<<yy;
 cout<<"\nAfter formating date is\t";
 switch(mm)
 {
 case 1:
 cout<<"\n"<<dd<<"-Jan-"<<yy;
 break;
 case 2:
 cout<<"\n"<<dd<<"-Feb-"<<yy;
 break;
 case 3:
 cout<<"\n"<<dd<<"-Mar-"<<yy;
 break;
 case 4:
 cout<<"\n"<<dd<<"-Apr-"<<yy;
 break;
 case 5:
 cout<<"\n"<<dd<<"-May-"<<yy;
 break;
 case 6:
 cout<<"\n"<<dd<<"-Jun-"<<yy;
 break;
 case 7:
 cout<<"\n"<<dd<<"-Jul-"<<yy;
 break;
 case 8:
 cout<<"\n"<<dd<<"-Aug-"<<yy;
 break;
 case 9:
 cout<<"\n"<<dd<<"-Sep-"<<yy;
 break;
 case 10:
 cout<<"\n"<<dd<<"-Oct-"<<yy;
 break;
 case 11:
 cout<<"\n"<<dd<<"-Nov-"<<yy;
 break;
 case 12:
 cout<<"\n"<<dd<<"-Dec-"<<yy;
 break;
 default:
 cout<<"\nInvalid month"; 

 }
 }
};
int main()
{
 int m,dt,y;
 cout<<"\n Enter date : ";
 cin>>dt;
 cout<<"\n Enter month : ";
 cin>>m;
 cout<<"\n Enter year : ";
 cin>>y;
 date d(dt,m,y);
 d.display();
 return 0;
}
#include<iostream.h>

#include<conio.h>

class Weight

{

int kilogram,gram;

public:

void getdata()

{

cout<<"\n\nEnter the kilogram:\t";

cin>>kilogram;

cout<<"\nEnter the gram:\t";

cin>>gram;

}

void display()

{

cout<<"\nAddition of two distance:\t";

cout<<kilogram<<"."<<gram;

}

void display2()

{

cout<<kilogram<<"."<<gram;

}

Weight operator+=(Weight &d)

{

Weight t;

t.kilogram=d.kilogram+kilogram;

t.gram=d.gram+gram;

return t;

}

int operator==(Weight &d)

{

if(kilogram==d.kilogram  || gram==d.gram)

{

return 1;

}

else

{

return 0;

}

}

};

void main()

{

Weight c1,c2,c3,c4,c5;

clrscr();

c1.getdata();

c2.getdata();

c3=c1+=c2;

c3.display();

c4.getdata();

c5.getdata();

if(c4==c5)

{

cout<<"\n";

c4.display2();

c5.display2();

cout<<"\t Both are same\t";

}

else

{

cout<<"\n";

c5.display2();

c4.display2();

cout<<"\t Both are not same\t";

}

getch();

}
<html>
<body>
<?php
$fahr=$_POST['fahrenheit']
<form action="<?php echo $_SERVER['PHP_SELF']?>"method="POST">
fahrenheit temperature:
<input type="text" name="fahrenheit" value=if(isset(=$_POST['fahrenheit'])){echo $fahr}?>>
<input type ="submit">
</form>
<?php
$Celsius=($fahr-32)*5/9;
printf("%f:%f,$fahr,$Celsius);
?>
</body>
</html>

<html>
<head>
<style>
span
{
                font-size: 25px;
}
table
{
                color: blueviolet; ;
}
</style>

<script type="text/javascript" >
                function print()
                {
                                var ob=false;
                                ob=new XMLHttpRequest();
             
                                ob.open("GET","slip14_Q2.php?");//emailid="+eid);
                                ob.send();         
             
                                ob.onreadystatechange=function()
                                {
                                                if(ob.readyState==4 && ob.status==200)
                                                {
                                                                document.getElementById("i").innerHTML=ob.responseText;
                                                }
                                }
                }           
</script>
</head>

<body>
<center>
<h3>Display the contents of a contact.dat file </h3>
<br><input  type="button"  value=Print onclick="print()" >
<span id="i"></span>
</center>
</body>
</html>


PHP file :

<?php
                $fp = fopen('contact.dat','r');
                echo "<table border=1>";
                echo "<tr><th>Sr. No.</th><th>Name</th><th>Residence No.</th><th>Mob. no.</th><th>Relation</th></tr>";
             
while($row =  fscanf($fp,"%s %s %s %s %s"))
                {
                                echo "<tr>";
                                foreach($row as $r)
                                {
                                                echo "<td>$r</td>";                           
                                }                           
                                echo "</tr>";
                }
                                echo "</table>";
                fclose($fp);
?

14
#include<iostream.h>

#include<conio.h>

 inline float diameter(float r)

{

return(r /2);

}

inline float circlearea(float r)

{

return(3.14*r*r);

}

inline float circumference(float r)

{

return(3.14*2*r);

}

int main()

{

float radius;

clrscr();

 cout<<"\n\nEnter the radius of the circle:";

cin>>radius;

cout<<"\nDiameter of Circle:"<< diameter(radius);

cout<<"\nArea of Circle:"<< circlearea (radius);

cout<<"\nCircumference of Circle:"<< circumference(radius);

getch();

return 0;

 }
 <html>
<body>
<form method=post action="<?php echo $_SERVER['PHP_SELF'] ?>">
Enter String : <input type=text name=str1><br>
<input type=submit name=submit value =Reverse>
</form>
<?php
            if(isset($_POST['submit']))
    {
                        $str=$_POST['str1'];
                        $nstr=strrev($str);
                        echo"<br>".$nstr;
    }
?>
</body>

</html>

<html>
<head>
<script type="text/javascript">
function Addition()
{
var ob=false;
ob=new XMLHttpRequest();
var no1=document.getElementById("no1").value;
var no2=document.getElementById("no2").value;
ob.open("GET","Que25.php?num1="+no1+"&num2="+no2);
ob.send();
ob.onreadystatechange=function()
{
if(ob.readyState==4 && ob.status==200)
document.getElementById("add").innerHTML=ob.responseText;
}
}
</script>
</head>
<body>
Enter User Name :<input type=text id="no1">
Enter Password :<input type=text id="no2">
<input type=button name=submit value=add onClick="Addition()">
<span id="add"></span>
<body>
</html>

Php File-
<?php
$una=$_GET['num1'];
$ps=$_GET['num2'];
$sn="localhost";
$un="root";
$pas="";
$dbn="s17";
if((!empty($una)) && (!empty($ps)))
{
$con=mysqli_connect($sn,$un,$pas,$dbn);
$sql="select * from login where un='$una' and pass='$ps'";
$r=mysqli_query($con,$sql);
if (mysqli_num_rows($r) > 0)
{
echo "Login";
}
else
{
echo "Not";
}
}
else
{
echo "enter both Username& pass";
}
?>

17
#include<iostream>
#include<conio.h>
using namespace std;

class Student
{
	public:
		int roll;
		char name[10],std[10];
		void accept_s();
		void display_s();
};

void Student :: accept_s()
{

	cout<<"Enter the Roll No : ";
	cin>>roll;
	cout<<"Enter The Name of Student : ";
	cin>>name;
	cout<<"Enter the Class of Student : ";
	cin>>std;
}

void Student :: display_s()
{
	cout<<"Student Details are : \n";
	cout<<roll<<"\t"<<name<<"\t"<<std<<endl;
}

class Competition
{
	public:
		int cid;
		char cname[10];
		void accept_c();
		void display_c();
};

void Competition :: accept_c()
{

	cout<<"Enter the Competition ID : ";
	cin>>cid;
	cout<<"Enter The Name of Competition : ";
	cin>>cname;
}

void Competition :: display_c()
{
	cout<<"Competition Details are : \n";
	cout<<cid<<"\t"<<cname<<endl;
}

class StudComp : public Student , public Competition
{
	public:
		int rank;
		void accept_sc();
		void display_sc();
		friend void sort(StudComp,int);

};

void StudComp :: accept_sc()
{
	cout<<"Enter the Rank : ";
	cin>>rank;
}
void StudComp :: display_sc()
{
	cout<<"Rank : "<<rank<<endl;
}

void sort(StudComp *sc,int num)
{
	for(int i=0;i<num-1;i++)
	{
		for(int j=0;j<num-i-1;j++)
		{
			if(sc[j].rank>sc[j+1].rank)
			{
				int temp = sc[j].rank;
				sc[j].rank=sc[j+1].rank;
				sc[j+1].rank=temp;
				int tempr = sc[j].Student::roll;
				sc[j].Student::roll = sc[j+1].Student::roll;
				sc[j+1].Student::roll = tempr;
			 }
		 }
	 }
	 cout<<"Sorted Details : "<<endl;
	 for(int i=0;i<num;i++)
	 {
	   cout<<"Rank : "<<sc[i].rank<<" "<<"Roll NO : "<<sc[i].Student::roll<<"  "<<endl;
	 }

}
main()
{

		int num;
		cout<<"Enter the Number of Student : ";
		cin>>num;
		StudComp *sc = new StudComp[num];
		for(int i=0;i<num;i++)
		{
			sc[i].Student::accept_s();
			sc[i].Competition::accept_c();
			sc[i].StudComp::accept_sc();
			sc[i].Student::display_s();
			sc[i].Competition::display_c();
			sc[i].StudComp::display_sc();
		}
		sort(sc,num);


	
}
<html>
<body>
<table border="1">
<tr>
<th>PHP_SELF</th>
<th>SERVER_NAME</th>
<th>HTTP_HOST</th>
<th>SCRIPT_NAME</th>
</tr>
<tr>
<?php
echo "<td>" .$_SERVER['PHP_SELF'] ."</td>";
echo "<td>" .$_SERVER['SERVER_NAME'] ."</td>";
echo "<td>" .$_SERVER['HTTP_HOST'] ."</td>";
echo "<td>".$_SERVER['SCRIPT_NAME']."</td>";
echo $_SERVER['HTTP_REFERER'];
echo "<br>";
echo $_SERVER['HTTP_USER_AGENT'];
echo "<br>";

?>
</tr>
</table>
</body>
</html>

<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/css" href="university.css"?>
<Uni>
                <U_info>
                                <Uname>Pune University</Uname>
                                <City>Pune</City>
                                <Rank>First</Rank>
                </U_info>
                <U_info>
                                <Uname>Mumbai University</Uname>
                                <City>Mumbai</City>
                                <Rank>Third</Rank>
                </U_info>
                <U_info>
                                <Uname>Latur University</Uname>
                                <City>Latur</City>
                                <Rank>Fifth</Rank>
                </U_info>
</Uni>

CSS file : university.css
Uname
{
                color:black;
                font-family: copperplate Gothic Light;
                font-size: 16pt;
                font: bold;
}
City,Rank
{
                color:yellow;
                font-family:arial;
                font-size: 12pt;
                font: bold;
}

PHP file :

<?php
                $xml=simplexml_load_file("university.xml") or die("eror:cannot create object");
                echo "<table border=1 align=center>";
                echo "<tr><td>Univercity Name</td><td>City</td><td>Rank</td></tr>";
                foreach($xml->children() as $uni)
                {
                                echo "<tr><td>".$uni->Uname."</td>";
                                echo "<td>".$uni->City."</td>";
                                echo "<td>".$uni->Rank."</td></tr>";
                }
                echo "<table>";
?>

18
<html>
<?php
$n=$_GET["n"];
$n1=$_GET["n1"];
$a=$_GET["a"];

?>
<form action="<?php echo $_SERVER["PHP_SELF"]?>" method="GET">
ENTER distance IN  meter:<input type="number" name="n"><br>
ENTER distance IN  kilometer:<input type="number" name="n1"><br>
<input type="radio" name="a" value="1">Convert to meters
<input type="radio" name="a" value="2">Convert to kilometers<br>
<input type="submit" value="Ok">
<br>
<?PHP
switch($a)
{

case 1:$c=round($n1*1000);
  echo"Distance in  meters is $c";
       break;
case 2:$c=round($n/1000);
    echo"Distance IN Kilometers is $c"; 
    break;
}      
?>
</form>
</html>

HTML file-
<html>
<head>
<title>Create XML</title>
</head>
<form action=slip23.php.php method=get>
Enter Book Title<input type=text name=txtTitle>
Enter Publication<input type=text name=publ>
<input type=submit value="submit">
</form>
</html>

PHP File-
<?php
echo "Links data posted";
$ele=$_GET['txtTitle'];
$att=$_GET['publ'];
$xmltags="<?xml version=1.0?>";
$xmltags=$xmltags."<Bookstore>";
$xmltags=$xmltags."<Books>";
$xmltags=$xmltags."<PHP>";
$xmltags=$xmltags."<title>";
$xmltags=$xmltags.$ele;
$xmltags=$xmltags."</title>";
$xmltags=$xmltags."<publication>";
$xmltags=$xmltags.$att;
$xmltags=$xmltags."</attrib>";
$xmltags=$xmltags."</PHP>";
$xmltags=$xmltags."</Books>";
$xmltags=$xmltags."</Bookstore>";
if($fp=fopen("books.xml","w"))
{
if($wt=fwrite($fp,$xmltags))
{
echo "File created";
}
else
echo "Not write";
}
else
echo "Not opened";
?>

20
#include <iostream>
using namespace std;

class Number
{
    private:
       int i;
    public:
       Number() {  }
       Number(int num)
       {
       	    i=num;
	   }
       Number operator ++() 
        { 
              ++i;
		    return *this; 
        }
        Number operator ++(int )
        {
          	Number temp=*this;
          	i++;
          	return temp;
		}
       void Display() 
        { 
            cout << "i=" << i << endl; 
        
        }
};

int main()
{
    Number obj(5),obj1(5);

    cout<<"Original Number = "<<endl;
    obj.Display();
    ++obj; 
    cout<<"After pre-increment number is = "<<endl;
    obj.Display();
    obj1++;
    cout<<"After post-increment number is = "<<endl;
    obj1.Display();

    return 0;
}
include<iostream>
#include<conio.h>
#include<string.h>

using namespace std;

class inventory
{
    int mno;
    char mname[30]; 
    int stock;
    float price; 

    public :
    void accept()
    {
        cout<<"\n Enter model no :"; cin>>mno;
        cout<<"\n Enter model name : "; cin>>mname;
        cout<<"\n enter price : "; cin>>price;
        cout<<"\n Enter stock : "; cin>>stock;
    }
    void display()
    {
        cout<<"\n model no is : "<<mno<<"\n model name : "<<mname<<"\n price : "<<price<<"\n stock :"<<stock;
    }

    int sale(int no,int q)
    {
        if(mno==no)
        { 
            if(stock>=q)
            {
                stock  =stock-q; 
                cout<<"\n sale is done : "; 
                display();
                return 2;
            }   
            else
            {
                cout<<"\n purchse is requried .";
                //purchase(); 
                return 1;
            }
        }
        /*else
        {
            cout<<"Please enter correct model number\n";
        }*/

 	}

    void purchase(int no,int q)
    {
        if(no==mno)
        {
            stock=stock+q;
            cout<<"\n purchase is done..."; 
            display();
        }
    }
};

int main()
{
    inventory in[10];
    int qt,ans,no,i;

    cout<<"\n Enter no of models : "; 
    int n;
    cin>>n;

    for(int i=0;i<n;i++) 
    in[i].accept();
    cout<<"===================================";
    for(i=0;i<n;i++) 
    {
        in[i].display();
    }

    cout<<"\n Enter model number to be purchaes and quantity : "; 
    cin>>no;
    cin>>qt; 
    for(i=0;i<n;i++)
    {	
        ans=in[i].sale(no,qt) ;
        if(ans==1)
    {
        cout<<"\n Enter model to be purchaes and quantity : "; 
        cin>>no;
        cin>>qt; 
        for(i=0;i<n;i++)
        {	
            in[i].purchase(no,qt);
        }
    }
    }
    return 0;
}

<html>

<head>

<link rel="stylesheet" type="text/css" href="book.css">

</head>

<body>

<?php

$xml=simplexml_load_file('movie.xml')or die("cannot die");

?>

<center>

</b>CD details</b></center>

<table border="1">

<th>cdcode</th>

<th>mname</th>

<th>ryear</th>

<th>aname</th>

<?php

foreach($xml->category  as $a)

{

echo"<tr><td>".$a['code']."</td>";

echo"<td>".$a->mname."</td>";

echo"<td>".$a->ryear."</td>";

echo"<td>".$a->aname."</td></tr>";

}

?>

</table>

</body>

</html>


Movie.xml

<?xml version="1.0" ?>

<bookinfo>

<category code="classical">

<mname>Geet</mname>

<ryear>1974</ryear>

<aname>jitendra</aname>

</category>

<category code="action">

<mname>Pushpa</mname>

<ryear>2022</ryear>

<aname>Allu</aname>

</category>

</bookinfo>

21
#include<iostream>
#include<conio.h>
#include<iomanip> 
using namespace std;
class person
{
   char e_name[10],c_name[10]; 
   int sal, eid;
   public:
   void accept()
   {
   	cout<<"Enter employee id: ";
   	cin>>eid;
   	cout<<"Enter employee name: ";
      cin>>e_name;
      cout<<"Enter company name: ";
      cin>>c_name;
      cout<<"Enter salary: ";
      cin>>sal;
      
   }
   void disp()
   {
   		cout<<"Employee id:"<<eid;
      	cout<<"\nEmployee name: "<<e_name;
      	cout<<"\nCompany name "<<c_name;
      	cout.width(7);
      	cout.fill('*');
      	cout.right;
      	cout<<"\nEmployee Salary: "<<setw(7)<<sal;
   }
};
int main()
{
	int i;
   person *p; 
   p=new person[5];
   cout<<"Enter details of 5 person"<<endl;
   for(i=0; i<5; i++)
   {
   	 p[i].accept();
   }
   for(i=0; i<5; i++)
   {
   	 p[i].disp();
   }
   
   
   return(0);
}

#include<iostream>
#include<conio.h>

using namespace std;
class point
 
{
int x,y;
public:
void get()
{
cout<<"\nEnter 2-Dimensional points: ";
cin>>x>>y;
}
 
void disp()
{
cout<<x<<"\t"<<y<<"\t"<<endl;
}
 
point operator+(point &t)
{
point tp;
tp.x=x+t.x;
tp.y=y+t.y;
return tp;
}
void operator -()
{
x=-x;
y=-y;

disp();
}

void operator *()
{
int n;
cout<<"Enter value of n:\n";
cin>>n;

x=-x;
y=-y;


x=x*n;
y=y*n;

disp();
}
};



int main()
{
point p1,p2,p3;
int ch;
p1.get();
p2.get();
 
cout<<"\nFirst 2-Dimensional point: ";
p1.disp();
cout<<"\nSecond 2-Dimensional point: ";
p2.disp();

do{
    cout<<"1 Addition\n";
    cout<<"2 Negates coordinates of point p1\n";
    cout<<"3 Mltiplication of coordinates of point pl by constant ‘n’\n";
    cout<<"4 Exit\n";
    cin>>ch;
    switch(ch)
    {
    case 1: p3=p1+p2;
    cout<<"\nAdded point: ";
    p3.disp();
    break;
    
    case 2: cout<<"\n\nNegated co-ordinate of p1: ";
            -p1;
            break;
    
    case 3: *p1;
    break;
    case 4:exit(0);
    }
}while(ch!=4);


return 0;
}
<?xml version="1.0" encoding="utf-8"?>
<course>
<computerscience>
<studentname>samir Thorat </studentname>
<classname>SYBCA. </classname>
<percentage>60 </percennatage>
</computerscience>

<computerscience>
<studentname>sunil kamble </studentname>
<classname>SYBCA. </classname>
<percentage>55 </percennatage>
</computerscience>
<computerscience>
<studentname>anil kamble </studentname>
<classname>SYBCA. </classname>
<percentage>60 </percennatage>
</computerscience>

<computerscience>
<studentname>asha kamble </studentname>
<classname>SYBCA. </classname>
<percentage>65 </percennatage>
</computerscience>

<computerscience>
<studentname>madhuri </studentname>
<classname>SYBCA. </classname>
<percentage>70 </percennatage>
</computerscience>
</course>

25
include <istream>
#include <conio.h>
#include <fstream>
#include <stdlib.h>
#include <ctype.h>
#include <iostream>

using namespace std;

int main()
{
    char fname[20];
    ifstream fin;
    ofstream fc, fu, fl, fd;
    cout << "\n Enter file name : ";
    cin >> fname;
    fin.open(fname, ios::in);
    fc.open("extra.txt", ios::out);
    fu.open("upper.txt", ios::out);
    fl.open("lower.txt", ios::out);
    fd.open("digit1.txt", ios::out);
    if (fin.fail())
    {
        cout << "File does not exists. ";
        exit(1);
    }
    char ch;
    while (!fin.eof())
    {
        ch = fin.get();
        if (islower(ch))
        {
            fl.put(ch);
            
        }
        else if (isupper(ch))
        {
            fu.put(ch);
            
        }
        else if (isdigit(ch))
        {
            fd.put(ch);
        }
        else if ((ch>31 && ch<48)||(ch>57 && ch<65)||(ch>122 && ch<127))
        {
            fc.put(ch);
        }
    }
    cout << "Task Completed....";
    return 0;
}

<?xml version="1.0" encoding="utf-8"?>
<Vehicle>
<Type = Two Wheeler>
<Vehicler Name >honda </Vehicle Name >
<Company>hero </Company>
<Color>black </Color>
<Average>60 Kmpl </Average>
</Type>

<Type = Three Wheeler>
<Vehicler Name >Auto rickshaws </Vehicle Name >
<Company>Bajaj Autorickshaw </Company>
<Color>yellow </Color>
<Average>50kmpl </Average>
</Type>

<Type = four Wheeler>
<Vehicler Name >maruti </Vehicle Name >
<Company>tata </Company>
<Color>white </Color>
<Average>60kmpl</Average>
</Type>
</Vehicle>

<HTML>
<BODY>
<FORM method=POST action="<?php echo $_SERVER['PHP_SELF'] ?>">
<b><h3>Perform operations on the TEACHER Table</b><BR>
<INPUT type=radio name="choice" value="1">Create<BR>
<INPUT type=radio name="choice" value="2">Insert<BR>
<INPUT type=radio name="choice" value="3">Update<BR>
<INPUT type=radio name="choice" value="4">Delete<BR>
<INPUT type=submit name=submit value="Operation Perform"><BR>
</FORM>
<?php
$hn="localhost";
$db="Teach";
$un="root";
$psw="";
$link=mysqli_connect($hn,$un,$psw,$db);
if(isset($_POST['submit']))
{
    $ch=$_POST['choice'];
            if($ch=='1')
    {
                        if(!$link)
                        {
                                    die('connection faild:'.mysql_error());
                        }
                                                $sql="create table teacher(tid int,tname varchar(10),addr varchar(20),sub varchar(10))";
                        if(mysqli_query($link,$sql))
                        {
                                                echo"Table created Successfully";
                        }
                        else
                        {
                                    echo"Unable to perform";
                        }
            }
    if($ch=='2')
    {
                        if(!$link)
                        {
                                    die('connection faild:'.mysql_error());
                        }
                                               
                                    $sql="insert into teacher values('102','Prof.Bhilare','Malegaon','PHP')";
                        if(mysqli_query($link,$sql))
                        {
                                    echo"Row inserted Successfully";
                        }
                        else
                        {
                                    echo"Unable to perform";
                        }
            }
            if($ch=='3')
            {
                        if(!$link)
                        {
                                    die('connection faild:'.mysql_error());
                        }
                                               
                                    $sql="update teacher SET addr='Baramati' where tid='101'";
                        if(mysqli_query($link,$sql))
                        {
                                    echo"Record Updated Successfully";
                        }
                        else
                        {
                                    echo"Unable to perform";
                        }
            }
    if($ch=='4')
    {
                        if(!$link)
                        {
                                    die('connection faild:'.mysql_error());
                        }
                                    $sql="delete from teacher where tid='101'";
                        if(mysqli_query($link,$sql))
                        {
                                    echo"Record Deleted Successfully";
                        }
                        else
                        {
                                    echo"Unable to perform";
                        }
    }
}
mysqli_close($link);
?>
</BODY>

</HTML>

27
include<iostream>
#include<conio.h>

using namespace std;

class College
{
	private:
	int id, year;
	char name[20],uname[20];
	public:
	College()
	{
	}
	friend ostream & operator << (ostream &out, const College &c);
	friend istream & operator >> (istream &in, College &c);
};

ostream & operator << (ostream &out, const College &c)
{
	out<<c.id<<"\t"<<c.name<<"\t"<<c.year<<"\t"<<c.uname<<endl;
	return out;
}

istream & operator >> (istream &in, College &c)
{
	cout << "Enter College ID : ";
	in >> c.id;
	cout << "\nEnter College Name : ";
	in >> c.name;
	cout<<"\nEnter Year of Establishment : ";
	in>>c.year;
	cout<<"\nEnter University Name : ";
	in>>c.uname;
	return in;
}

int main()
{
	
	College c1;
	cin>>c1;
	cout<<"\nThe College details are : "<<endl;
	cout<<c1;
	
}

include<conio.h>
#include<iostream>

using namespace std;
class train
{
   protected:
   int tno;
   char name[10];
   public:
   void accept()
   {
	cout<<"\nEnter train no: ";
	cin>>tno;
	cout<<"\nEnter train name: ";
	cin>>name;
   }
};

class route: public train
{
   public:
   int rid;
   char s[10],d[10];
   void acc()
   {
      cout<<"\nEnter train id: ";
      cin>>rid;
      cout<<"\nEnter train source: ";
      cin>>s;
      cout<<"\nEnter destination: ";
      cin>>d;
   }
};

class reser: public route
{
   public:
   int  nos,fare,dd,mm,yyyy;
   char clas[10];
   void ac()
   {
      cout<<"\nEnter no of seats: ";
      cin>>nos;
      cout<<"\nEnter train class: ";
      cin>>clas;
      cout<<"\nEnter date(dd mm yyyy): ";
      cin>>dd>>mm>>yyyy;
   }
   void dis()
   {

      cout<<"\nTrain no\t\t:\t"<<tno;
      cout<<"\nTrain name\t\t:\t"<<name;
      cout<<"\nTrain id\t\t:\t"<<rid;
      cout<<"\nTrain source\t\t:\t"<<s;
      cout<<"\nTrain destination\t: \t"<<d;
      cout<<"\nNo of seats\t\t:\t"<<nos;
      cout<<"\nTrain class\t\t:\t"<<clas;
      cout<<"\nTrain date\t\t:\t"<<dd<<"/"<<mm<<"/"<<yyyy<<"\n";
   }
};
int main()
{
  
   int i,s;
   reser r[20];
   cout<<"Enter how many details you want to enter: ";
   cin>>s;
   for(i=0;i<s;i++)
   {
	r[i].accept();
	r[i].acc();
	r[i].ac();
   }
   for(i=0;i<s;i++)
   {
	r[i].dis();
   }

}

<html>
<head>
<script type="text/javascript">

  function Addition()
  {
              var ob;
              ob=new XMLHttpRequest();
 
              var no1=document.getElementById("no1").value;
              //var no2=document.getElementById("no2").value;
 
              ob.open("GET","SLIP27-p2-q1..php?num1="+no1,false);
              ob.send();       
 
             // ob.onreadystatechange=function()
             // {
                          //if(ob.readyState==4 && ob.status==200)
                          document.getElementById("add").innerHTML=ob.responseText;             
                          // }          
  }
 
</script>
</head>

<body>

Enter first no :<input type=text name=no1 id="no1"><br>
<!-- Enter second no :<input type=text name=no2 id="no2"><br>
 --><input type=button name=submit value=add onClick="Addition()"><br>
<span id="add"></span>

<body>
</html>
PHP File:
<?php
  $n1=$_GET['num1'];
  
//echo"error";
$m=1;
if(!empty($n1))
  {           
  	          for($i=1;$i<=$n1;$i++)
  	          {
                  $m=$i*$m;

  	          }
              
  }
        echo "Factorial = $m";
?>

Html File:
<html>
<script type="text/javascript">
function display()
{
	name=f1.txt.value;
	var xmlhttp;
	if(window.XMLHttpRequest)
	{
		xmlhttp= new XMLHttpRequest();
	}
	else
	{
		xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
	}
        xmlhttp.open("GET","slip27-p3-q2.php?txt="+ name,false);
        xmlhttp.send();
        document.getElementById('result').innerHTML=
        		xmlhttp.responseText;
}
</script>
<body>
	<form name="f1">
		Enter Book name:
		<input type="text" name="txt" onKeyUp="display()"/><br>
	</form>
	 <div id='result'></div> 
	</body>
	</html>	

PHP File:
<?php
$msearch=$_GET['txt'];
$xml=simplexml_load_file("slip27-p2-q2.xml");
echo $xml->getName()."<br>";
$hint="";
$len=strlen($msearch!=="");
if($msearch !=="")
{
	foreach($xml->children() as $movie)
	{
		//if(strstr($movie->MovieName,substr($msearch,0,$len)))
		if(strcmp($msearch,$movie->Title)==0)
		
		{
			$hint=" Book Name: $movie->Title <br>
			        Book Author: $movie->Author <br>
			        Year: $movie->Year<br>";
		}
	}
}
 echo $hint===""?"no suggestion":$hint;
 ?>


XML File:

<?xml version="1.0"?>
<BOOKS>
<BOOK>
<Title>OS</Title>
<Author>Nirali</Author>
<Year>2016</Year>
<Price>250</Price>
</BOOK>
<BOOK>
<Title>Advance PHP</Title>
<Author>M.K</Author>
<Year>2020</Year>
<Price>300</Price>
</BOOK>
<BOOK>
<Title>C++</Title>
<Author>Nirali</Author>
<Year>2020</Year>
<Price>350</Price>
</BOOK>
</BOOKS>
