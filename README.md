
Slip 1: Write the HTML code for generating the form as shown below. Apply the internal CSS to following form to change the font size of the heading to 6pt and change the color to red and alsochange the background color to yellow.

<html>

Project Management

Project Name

Assigned to

Me Pasion

Start Date

2

n

End Date

Priority

High Average Low

Description

<head>

<title>slip 1</title>

<style>

body{background-color: yellow;} table (background-color: turquoise;}

h3 {font-size: 6pt; color:red;}

</style>

</head>

<body>

<center>

<h3> Project Management </h3>

<table border="3" height="200px" width="400px">

<form name=frmlogin><br>

<tr><td>Enter Project Name:</td><td><input type=text name=t1

placeholder=projectname><br><br></td></tr> <

tr><td>Assignned to:</td><td><select name="Names" id="nm" form="frmlogin">

<option value="ross">Ross Geller</option>

<option value="chuck">Chuck Bass</option> <option value="rachel">Rachel Green </option>

<option value="dan">Dan James</option>

</select></td></tr>
<tr><td>Start Date:</td><td><input type="date"></td></tr>

<tr><td>End Date:</td><td><input type="date"> </td></tr>

<tr><td>Priority:</td><br>

<td><input type=radio name=ck value="high">High<br>

<input type=radio name=ck value="avg">Average <br>

<input type=radio name=ck value="low">Low</td></tr>

<tr><td>Description:</td><td><input type=text name="dt"

value="description"></td></tr>

<tr><td><input type=submit value ="submit"></td>

<td><input type=reset value ="clear"></td></tr>

</table>

</center>

</body>

</html>


Slip 2: Create HTML5 page with following specifications

i) Title should be about your City

ii) Color the background by Pink color.

iii) Place your city name at the top of page in large text and in blue color.

iv) Add names of the landmarks in your city, each in different color, style and font

v) Add any image at the bottom (Use inline CSS to format the web page)

Solution:

<html>

<head>

<title>PUNE</title>

<body style="background-color:Pink;">

<h3 style="font-size: 100px; color:blue;"> PUNE</h3>

<ul>

<li style="color:brown; font-style: italic;">Dagadu Seth Ganpati Temple</li>

<li style="color:red; font-style: oblique;">Saras Baug Temple</li> <li style="color:purple; font-style: italic;">Phoenix Market City Pune</li>

</ul>

<img src="https://mittalbuilders.com/wp-content/uploads/2020/12/Reasons-to- settle-down-in-Pune.png" width="200" height="200" align="bottom">
</body>

</head>

</html>



Slip 3:

Write a program using html with following CSS specifications-

1 The background colour of the company name should be in green.

ii

The text colour of the company name should be red The heading should be large-with font "comic sans ms"

IV. The description of the company should be displayed in blue color in a paragraph.

<html>

<head>

<title>Accenture</title></head>

<body style="background-color:#4CB817">

<h3 style="font-size:60px; color:red; font-style:Comic Sans MS"> Accenture</h3>

<p style=" color:blue; font-size:25px">Accenture plc is an Irish-American professional services company based in Dublin,

specializing in information technology (IT) services and consulting.<br>

As of 2022, Accenture is considered

the largest consulting firm in the world by number of employees.<br>

Accenture is a $61.6-billion-in-annual-revenue technology and consulting company incorporated in Dublin, Ireland.

Led by Chair & CEO Julie Sweet, who prior to her promotion in 2019 served as CEO of Accentures business in North America,

the Fortune Global 500 information technology services company has supplemented its growth

through high-profile acquisitions like that of ad agency Droga5. With 721,000 people worldwide</p>

</html>



Slip 4:
Write a HTML code, which generate the following output

<html>

<body>

<table border = 1>

<caption>list of book </caption> <tr>

<td rowspan=2>item no </td>

<td rowspan=2>Item name </td>

<td colspan=2> price

<>

<td>Rs </td>

<td>paise</td>

</td>

</tr>

</tr>

<>

<td>1</td>

<td>programming in python </td>

<td>500</td><td>50</td>

</tr> <tr>

<td>2</td>

<td>programming in java </td>

<td>345</td><td>00</td>

</tr>

</body>

</html>


Slip7 Design HTML 5 Page Using CSS Which Displays the following Navigation Bar

Home

Java

HTML

CSS

<html>

<head>

<title>Navigation Bar</title>

<style>

display:inline,

li

</style>

</head>

<body style="font-size:40px">

<ul>
<li><a href="HOME.asp" style="color: white; background-

color grey;">HOME</a></li>

<li> <a href="JAVA.asp" style="color:blue; background- color:#D3D3D3;">Java</a></li>

<li><a href="HTML.asp" style="color:blue; background-

color:#D3D3D3;">HTML</a></li>

<li><a href="CSS.asp" style="color:blue; background-

color:#D3D3D3;">CSS</a></li>

</ul>

</body>

</html>



Slip8: Design an HTML form to accept two strings from the user. Write a PHP script for

thefollowing.

a. Find whether the small string appears at the start of the large string

b. Find the position of the small string in the big string

c. Compare both the string for first n characters, also the comparison should not be case sensitive.

HTML FILE

<html>

<body>

<form action="slip 8.php" method="get">

enter first string:<input type="text" name="str1"><br> enter second string: <input type="text" name="str2"><br>

<input type="submit" value="submit">

</form>

</body>

</html>

PHP FILE

<?php $a=$_GET["str1"];

$b=$ GET["str2"];

//Slen1=strlen($a);

//Slen2=strlen($b);

echo "Length Slenl $len2";

$pos=strpos($a,$b); if($pos=0)

else

echo"the small string appears at the start of the large string<br>";

echo"small string does not appear at the start of the large string<br>";
} $pos=strpos($a,$b);

echo "the small string appears at $pos position<br>";

if(strcasecmp($a,$b)=0)

echo "Both Strings are equal<br>";

else if(strcasecmp($a,$b)>(0)

echo "first string bigger<br>";

else

echo "second string is bigger<br>";

?>




Slip9: Write a PHP script for the following: Design a form having a text box and a drop down listcontaining any 3 separators(eg. #,,%, @, or comma) accept a strings from the user and also aseparator.

a. Split the string into separate words using the given separator.

b. Replace all the occurrences of separator in the given string with some other separator.

c Find the last word in the given string

HTML FILE

<html>

<body>

<form action="slip_9.php" method="get">

Enter a string: <input type="text" name="str1"><br>

choose a label

<select name="sep" id="sep">

<option value="#">#</option> <option value="!">!</option>

<option value="@">@</option>

</select><br>

<input type="radio" name="op" value="a">Split The String Using The Seperator<br>

<input type="radio" name="op" value="b">Replace The Occurences Of The

Seperator With Another Seperator<br>

<input type="radio" name="op" value="c">Find The Last Word Of The String<br>

<input type="submit" value="submit">
</form> 
</body>
</html>
PHP FILE <?php $str=$_GET['str1']; $sep=$_GET['sep']; $op=$_GET['op'];
//echo "$str $sep Sop";

switch($op)
{

case 'a' $m-explode($sep,$str), foreach(Sm as $a){

echo "$a<br>";

}

break;

case 'b'

$cnt-substr_count($str, $sep);

$n=str_replace($sep,"!",$str, $cnt);

echo "After changing separators<br>";

echo $n;

break;

case 'c' Sar-explode(" ".$str),

$cnt=count($ar);

echo "This is the last word: " Sar[$cnt-1];

break;
}
?>




Slip10: Write a script to accept two integers (Use html form having 2 textboxes). Write a PHP script to,

a. Find mod of the two numbers.

b. Find the power of first number raised to the second

c. Find the sum of first n numbers (considering first number as n)

d. Find the factorial of second number

(Write a separate function for each of the above operations.)

HTML FILE

<html>

<head>

<title>Assignment 3 Q1</title>

</head>

<form action="slip10.php" value="GET">

<body>

Enter Two Numbers<br>

<input type="text" name="n1"><br><br>

<input type="text" name="n2"><br><br>
Select An Operation<br>
<input type="radio" name="op" value="mod">Mod Of The Two Numbers<br><br>
<input type="radio" name="op" value="power">Power Of The First Number Raised To The Second<br><br>

<input type="radio" name="op" value="sum">The Sum Of First n Numbers<br><br> <input type="radio" name="op" value="fact">Factorial Of The Second

Number<br><br>

<input type="submit" value="Submit">

</form>

</body>

</html>

PHP FILE

<?php

$n1=$_GET["nl"];

$n2-$ GET["n2"]. $op=$_GET["op"]; function mod($n1,$n2)

{

$n3=0; if(\$ n * 2! = 0 ) $n3=$n1%$n2, return $13
}
function power($n1,$n2)
{
$ n * 3 = 1 or( Si = 1 ;Si:=\$n2;Si++) Sn3-Si Sn1; return $n3:
}
function sum($n1)
{
$ n * 3 = 0;

for( Si = 1 ,\$i<=\$n1,Si++)
{
$n3=$n3+$1; 
}
return $n3;
}
function fact($n2) yr( S_{1} = 1 ;S 1 <=\$n2;S 1 ++)
{
$ n * 3 = 1 ,
{
$n3-$n3*$i;
}
return $n3;
}
switch($op)
{
case "mod": $result=mod($n1,$n2),

echo "Mod of $n1 and Sn2 is Sresult."; break;

case "power" $result-power($n1,$n2),

echo "$n1 raised to $n2 is $result.";

break; case "sum": $

result=sum($n1);

echo "Sum of first $n1 number is $result":

break;

case "fact" $result-fact($n2);

echo"Factorial of Sn2 is $result.": break;
}
?>




Slip12: Write a PHP script for the following Design a form to accept two numbers from the user Give options to choose the arithmetic operation (use radio buttons) Display the result on the nextform. (Use the concept of function and default parameters. Use 'include' construct or require statement)

PHP FILE

?php $x-S POST['1'], $y=$_POST['2']. Sop-$ POST['op'],

function add($x=4,$y=2) { $result=$x+$y; echo"adition is $result", function sub($x=4.$y=2) 1 $result=$x-Sy; echo"subtraction is Sresult"; switch (Sop) 1 case"1": add($x,Sy), break case"2" sub($x,$v), break; 
}
?>
HTML FILE

<html>

<body>

<form action="slip 12in.php" method="POST">

first number

<input type=text name=s2><br>

second number

<input type=text name=s1><br>

chose opration from below<br>

addition

<input type radio value="1" name=op> <br>

subtraction

<input type radio value="2"name=op> <br>

<input type=submit value="submit"><br>

</body>

</html>

PHP FILE <?php

include'slip12.php;
?>



Slip13: Write a PHP script to create a chess board using CSS on table cells.

<html>

<head>

<head><title>NRC ChessBoard</title>

<style>

clrl

{

}

clr2

{

}

table

{

background-color:black;

background-color:white;

width: 100%;

height: 100%;

}

</style>

<?php

echo"<table border=1>";

for($i=1;$i<=8;$i++)

{

echo"<tr>";

if($i%2==0)

{

for($j=1;$j<=8;$j++)

{

if($j%2==1)

echo"<td class=clr2></td>";

echo"<td class=clr1></td>";

else

}

}

else

{

for($j=0;$j<8;$j++)

{

if($j%2==0)

echo"<td class=clr1></td>";
else
echo"<td class=clr2></td>";
}
} echo "</tr>";

} echo"</table>";

?>

</html>




Slip15: Design a form to accept string from the user and perform the following operations

a. To select first 5 words from the string

b. Convert the given string to lowercase and then to Title case

c. Pad the given string with "*" from left and right both the sides.

d. Remove the leading whitespaces from the given string

e. Find the reverse of given string

HTML FILE

<html>

<body>

<form action="Slip15.php" method=get>

Enter a String<input type=text name=t1><br>

<input type=radio name=op value=1>Select 5 words<br>

<input type=radio name=op value=2>LowerCase<br>

<input type=radio name=op value=3>Padding<br>

<input type=radio name=op value=4>Remove Spaces<br>
<input type=radio name=op value=5>Reverse<br><br>

</form>

<input type=submit value=submit>

</body>

</html>

PHP FILE
<?php

$str=$_GET['t1']; $ch=$_GET['op']; if($ch=1)

{ $ar=explode("",$str,6); foreach($ar as $a) echo "$a<br>".

}

else if($ch=2)

{

$str=strtolower($str);

echo $str;

$str=ucwords($str);

echo "<br>$str";

}

else if($ch==3)

{ $str=str_pad($str,20,"*",STR_PAD_BOTH); echo $str;

}

else if($ch=4)

{ $str=trim($str); echo $str;

}

else if($ch=5)

{ $str=strrev($str); echo $str;

}

?>


Slip16: Write a PHP script for the following: Design a form to accept the marks of 5 different subjects of a student, having serial number, subject name & marks out of 100.

Display theresult in the tabular format which will have total, percentage and grade. Use only 3 text boxes. (Use array of form parameters)

HTML FILE

<html>

<head>

<title> marksheet </title>

</head>

<body>

<form name = "string" action = "slip16.php" method="get">

student id <input type = "text" name = "v1"/></br></br>

Subject name<input type = "text" name = "v2"/></br></br>

subject marks<input type = "text" name = "v3"/></br></br>

<button type="submit"> display marklist </button>

</form>

</body>

</html>

PHP FILE

<?php

$a=$_GET['v1'];

$b =$_GET['v2'];

$c =$_GET['v3'];

$sum=0;

echo "<h1> <center>Marksheet</center></h1>";

echo "<h3><center>student id: $a</h3><br>";

$d=explode(",",$b);

$e=explode(",",$c);

echo "<center><table border=2 width=50%>";

for($i=0;$i<=4;$i++)

{

echo "<tr>

<td>$d[$i]</td> <td>$e[$i]</td>

</tr>";

$sum=$e[$i]+$sum;

}

$result-$sum/5;

echo "<tr><td>Total marks </td><td>$sum</td>";

echo"<tr><td>Percentage</td><td>$result</td></tr>";

echo "</center>"

?>


Slip17: Write a PHP script to sort the following associative array:

array("Sagar"=>"31","Vicky"=>"41","Leena"=>"39","Ramesh"=>"40") in

a) ascending order sort by Value

b) ascending order sort by Key

c) descending order sorting by Value

d) descending order sorting by Key

<?php

$a = array("Sagar"=>"31","Vicky"=>"41","Leena"=>"39","Ramesh"=>"40"); echo "sorting in ascending order by value<br>";

asort($a);

print_r($a);

echo "sorting in ascending order by key<br>";

ksort($a);

print_r($a);

echo "sorting in decending order by value<br>";

arsort($a);

print_r($a);

echo "sorting in decending order by key<br>";

krsort($a);

print_r($a);

?>



Slip18: Write a menu driven program to perform the following operations on an associative array

a Reverse the order of each element's key-value pair.

b. Traverse the element in an array in random order

c. Convert the array elements into individual variables

d. Display the elements of an array along with key

HTML FILE

<html>

<head>

<title> String operations </title>

<body>

<form name = "String" action="s18_q1.php" method="get">

<h2> Select Operations</h2>

<input type = "radio" name="s" value=1>Reverse the order</br></br>

<input type = "radio" name="s" value=2>Traverse the element</br></br>

<input type="radio" name="s" value=3>Convert the array elements</br></br>

<input type="radio" name="s" value=4>Display the elements of an array along with

key.</br></br>

<input type=submit value=send>

</body>
</html>

PHP FILE

<?php

$a = array("a"=>1,"b"=>21,"c"=> 56);

switch($_GET['s'])

{

case 1:

echo "Orginal Array is <br>";

print_r($a);

echo "reverse Array is <br>"; $c =array_reverse($a);

print_r($c);

break;

case 2:

echo "Orginal Array is <br>";

print_r($a);

echo "traversing Array is <br>"; foreach($a as $v)

echo "$v<br>";

break;

case 3:

echo " Original array is<br>";

print_r($a);

echo "elements into individual variables<br>"; $e=extract($a);

print_r($e);

break;

case 4:

Slip21: Create an array of 15 high temperatures, approximating t

month, then find the average high temp, the five warmest high ten

browser

echo " Original array is<br>"; print_r($a);

echo "key value pair is<br>"; foreach ($a as $k=>$v)

{

print_r("$k=>$v"); echo"<br>";

}

break;

default:

echo "Invalid choice!!";

}

?>



Slip21: Create an array of 15 high temperatures, approximating the weather for a spring month, then find the average high temp, the five warmest high temps Display the result on the browser.

<?php

$temp_array-range(31,45);

$tot temp = 0;

$count = count($temp_array);

echo "Total temp values are: ".$count;

foreach($temp_array as $temp) {

$tot_temp+= $temp;

} $avg_high_temp = $tot_temp/$count;

echo "<br> Average Temperature is: ".$avg_high_temp."

sort($temp_array);

echo "<br> List of five lowest temperatures:"; $res1= array_slice($temp_array 0,5);

foreach($res1 as $high_temp)

{ echo "<br> $high temp";

}

echo "<br> List of five highest temperatures:";

$res = array_slice($temp_array, 10);
foreach($res1 as $high_temp)
{ 
echo "<br> $high_temp";

}

?>




Slip24: Write a PHP program to read two file names from user and append content of first file intosecond file.

HTML FILE

<html lang="en">

<head>

<title>NRC File Handling</title>

</head>

<form action="slip24.php" method="get">

<body>

Enter File name to read <input type="text" name="fname1">

Enter File name to write <input type="text" name="fname2">

<input type="submit" value="Copy">

</form>

</body>

</html>

PHP FILE (create 2 text file pf your choice name and use same)

<?php

$fname1=$_GET['fnamel']; $fname2=$_GET['fname2']; $fp1=fopen($fname1,"r"); $fp2=fopen($fname2,"a");

$size-filesize($fname1);

$str fread($fp1,$size);
fwrite($fp2,$str, $size); echo "Append Successfull"; ?>



Slip25: Write a menu driven program to perform various file operations. Accept

filename from user

a) Display type of file.

b) Display last modification time of file

c) Display the size of file

d) Delete the file

HTML FILE

<html lang="en">

<head>

<title>Document</title>

</head>

<body>

<form action="slip25.php" method="get">

Enter File name to read <input type="text" name="fname1"><br>

<input type="radio" name="op" value="1">Display Type of File<br>

<input type="radio" name="op" value="2">Display Modification Time<br>

<input type="radio" name="op" value="3">Display File Size<br>

<input type="radio" name="op" value="4">Delete File<br>

<input type="submit" value="Copy">

</form>

</body>

</html>

PHP FILE

<?php

$fp=$_GET['fnamel'];

$op=$_GET['op'];

switch($op)

{

case 1:
echo basename($fp);

break;

case 2: $mtime=stat($fp);

echo Date("d/M/Y h:m:s",$mtime['mtime']);

break;

case 3: echo filesize($fp); break;

case 4: unlink($fp); echo "File deleted"; break;
}



Slip 26: Consider the following entities and their relationship. Doctor (doc_no, dname, address, city, area)

Hospital (hosp_no, hname, hcity)

Doctor-Hospital related with many-one relationship. Create a RDB in 3NF for above and

solve the following.

Using above database write a script in PHP to print the Doctor visiting to the Hospital in tabularformat. Accept Hospital name from user.

(Use your database)

Solution

Html file

<html>

<form action=slip26.php method=get>

Enter Hospital Name<input type=text name=t1><br>

<input type=submit value="Display Doctors">

</form>

</html>

PHP File

<?php

$con=pg_connect("host=localhost user=postgres password=nrc dbname=slip26"); $cn=$_GET['t1']; $rs=pg_query($con,"select * from doctor, hospital where hname='$cn' and hsno=hno");

while($row=pg_fetch_array($rs))
{
echo "Id:$row[0]       Name:$row[1]       Address:$row[2]       City:$row[3]
Pin:$row[4]<br>";

}

?>



Slip27: Write a PHP program to read two file names from user and copy the content of first file into second file.

HTML FILE

<html lang="en">

<head>

<title>NRC File Handling</title>
</head>

<body>

<form action="slip27.php" method="get">

Enter File name to read <input type="text" name="fname1">

Enter File name to write <input type="text" name="fname2">

<input type="submit" value="Copy">

</form>

</body>

</html>

PHP FILE

<?php

$fname1=$_GET['fname1']; $fname2=$_GET['fname2'];

$fp1=fopen($fname1,"r"); $fp2=fopen($fname2,"w");

$size=filesize($fname1);

$str=fread($fp1,$size); fwrite($fp2,$str, $size); echo "Append Successfull";

?>




Slip28: Write a program to read a flat file "student.dat", calculate the percentage and display the data from file in tabular format. (Student.dat file contains rollno, name, OS, WT, DS, Python, Java, CN)

Student.dat file

rollno name OS WT DS Python Java CN

1 Abd 30 30

2

25 23

20 45

xyz 32 33 24 25

25 45

Vo

98

PHP FILE

<?php

$fp=fopen("student.dat","r");

$ar=fscanf($fp,"%s%s%s%s%s%s%s%s",$rl,$nm, $os,$wt,$ds,$py,$jv,$cn);
echo "<table border=1><tr><th>$rl</th><th>$nm</th><th>$os</th><th>$wt</th><th>$ds</th><t h>$py</th><th>$jv</th><th>$cn</th><th>Percentage</tr>";

while(($ar=fscanf($fp,"%s%s%d%d%d%d%d%d", $rl, $nm, $os,$wt,$ds,$py,$jv,$cn))!=f alse)

{ $total=$os+$wt+$ds+$py+$jv+$cn;

$per=$total/6;

echo
<tr><th>$rl</th><th>$nm</th><th>$os</th><th>$wt</th><th>$ds</th><th h><th>$jv</th><th>$cn</th><td>$per</td></tr>";

}

echo "</table>";

?>


Slip29:

Consider the following entities and their relationships

Event (eno, title, date)

Committee (cno, name, head, from_time,to_time, status) Event and Committee have many to many relationship. Write a php script to accept title of eventand modify status committee as working

HTML File

<html>

<form action=slip29.php method=get>

Enter Event Name:<input type=text name=t1><br>

<input type=submit value="Change Status">

</form>

</html>

PHP File

<?php
$con=pg_connect("host=localhost user=postgres password=nrc bname=practicals22"); //echo $con;

$en=$_GET['t1']; $ws='Working';

$x=pg_query($con,"update comm_mem set cstatus='$ws' from event_comm,event where comm_mem.cno=event_comm.cno and event_comm.eno=event.eno and etitle='$en");

if($x>0)

echo "Working status updated";

else

echo "Status not updated";

?>


Slip30:

Consider the following entities and their relationships

Student (Stud_id,name,class) Competition (c_no,c_name,type)

Relationship between student and competition is many-many with attribute rank and year Createa RDB in 3NF for the above and solve the following. Using above database write a script in PHPto accept a competition name from user and display information of student who has secured 1st rank in that competition.

HTML File

<html>

<form action=slip30.php method=get>

Enter Comp. Name<input type=text name=t1><br>

<input type=submit value="Display Ranker">

</form>

</html>

PHP File

<?php

$con=pg_connect("host=localhost user=postgres password=nrc dbname=slip30"); $cn=$_GET['t1'];
$rs=pg_query($con,"select * from student, competition,stud_comp where cname='$cn' and srank=1 and id=sid and competition.cno=stud_comp.cno");

while($row=pg_fetch_array($rs))

{

echo "$row[0] $row[1] $row[2]<br>";

}

?>







