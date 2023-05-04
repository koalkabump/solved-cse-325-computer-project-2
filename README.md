Download Link: https://assignmentchef.com/product/solved-cse-325-computer-project-2
<br>
<h1>Assignment Overview</h1>

<strong> </strong>

This assignment focuses on C shell programming in a Linux environment.  You will design and implement a set of C shell scripts which are used to produce reports about census data.




It is worth 30 points (3% of course grade) and must be completed no later than 11:59 PM on Thursday, 1/23.




<h1>Assignment Deliverables</h1>




The deliverables for this assignment are the following files:




<strong>proj02.script1 </strong>— the C shell script which produces Report #1<strong> proj02.script2 </strong>— the C shell script which produces Report #2<strong> proj02.script3 </strong>— the C shell script which produces Report #3<strong> proj02.script4 </strong>— the C shell script which produces Report #4




Be sure to use the specified file names and to submit your files for grading via the CSE Handin system before the project deadline.




<h1>Assignment Specifications</h1>




The following files are available on the CSE Linux system:




<strong>/user/cse325/Projects/project02.data </strong>

<strong>/user/cse325/Projects/project02.headers </strong>




The first file contains the list of cities and townships (census units) within each county in Michigan.  For each census unit, the file contains the total population recorded during the 2010 United States Census.  The first five lines of that file are shown below:




<strong>Matchwood township                   | Ontonagon      |         94 </strong>

<strong>Bois Blanc township                  | Mackinac       |         95 </strong>

<strong>Newark township                      | Gratiot        |       1093 </strong>

<strong>Vassar township                      | Tuscola        |       4093 </strong>

<strong>Westland city                        | Wayne          |      84094 </strong>




The second file contains column headers which are formatted for use with this data:




<strong>Census Unit                          | County         | Population </strong>

<strong>————————————-+—————-+———– </strong>




You will design and implement four C shell scripts which are capable of producing the reports described below.




You may use UNIX utility programs (such as “echo”, “cat” and “grep”) inside your C shell scripts to generate the reports, but you may NOT use an editor program to edit any of the reports.




All four C shell scripts will write their output to standard output.  You may use piping within your scripts to connect the output of one utility program to the input of another, but your scripts may not create any temporary files.




<ol>

 <li>The C shell script “proj02.script1” will produce a report about the census units within a specified county.</li>

</ol>




The report will include an appropriate title, the column headers described above, and all of the census units in a specified county.  The places in the county will be sorted by population (from lowest to highest); if more than one place in the county has the same population, the report will list those places alphabetically.




Your C shell script will assume that the second command-line token is an identifier for the specified county (for example, “Ingham” or “Saginaw”).




<ol start="2">

 <li>The C shell script “proj02.script2” will produce a series of reports about the census units in a list of specified counties.</li>

</ol>




Each report will include an appropriate title, the column headers described above, and all of the census units in a specified county.  The places in the county will be sorted by population (from lowest to highest); if more than one place in the county has the same population, the report will list those places alphabetically.  Individual reports will be separated by exactly two blank lines.




Your C shell script will assume that the second and each subsequent command-line token is an identifier for a specified county.




<ol start="3">

 <li>The C shell script “proj02.script3” will produce a report about the N census units with the largest population.</li>

</ol>




The report will include an appropriate title, the column headers described above, and the population for the top N census units (where N is a positive integer) from a subset of the places in Michigan, sorted by population (from highest to lowest).  If more than one place has the same population, the report will list those places alphabetically.




Your C shell script will accept two arguments: a positive integer number that specifies the value of N, and a

character string which specifies the subset of census units which should be included in the report.  This character string will be “A” (meaning that all places should be included), “C” (meaning that only places which are cities should be included), or “T” (meaning that only places which are townships should be included).




<ol start="4">

 <li>The C shell script “proj02.script4” will produce a report about the N census units with the largest population.</li>

</ol>




The report will be identical to Report #3 described above.  However, your C shell script which produces the report will include error checking.




If the user supplies an invalid number of arguments, your C shell script will display an appropriate error message.




If the user supplies an invalid value as the second token (an integer value which is not greater than zero), your C shell script will display an appropriate error message.




If the user supplies an invalid character string as the third token (something other than “C”, “T” or “A”), your C shell script will display an appropriate error message.




<h1>Assignment Notes</h1>




<ol>

 <li>The first line of each of your C shell scripts must be the line shown below (where the ‘#’ character is in the first column):</li>

</ol>




<strong>#!/bin/tcsh -f </strong>




<ol start="2">

 <li>You may not copy the files containing the data or the column headers into your account. Instead, use absolute pathnames to access the files stored under the “/user/cse325/Projects” directory.</li>

 <li>The following are examples of valid commands which use the shell scripts:</li>

</ol>




<strong>proj02.script1 Wayne </strong>

<strong>proj02.script2 “Grand Traverse” Gratiot Wexford proj02.script3 25 A proj02.script4 10 C </strong>




<ol start="4">

 <li>In a “foreach” control construct in a shell script, the “:q” modifier can be used to retain the quoting for an argument list. Here is a simple example:</li>

</ol>




<strong>&lt;129 arctic:~ &gt; cat showargs </strong>

<strong>#!/bin/tcsh -f </strong>

<strong> </strong>

<strong>foreach item ($argv[*]:q)   echo $item end </strong>

<strong> </strong>

<strong>&lt;130 arctic:~ &gt; showargs aaa bbb “ccc ddd” eee aaa bbb ccc ddd eee </strong>




<ol start="5">

 <li>Note that some cities appear more than once in the data file. For example:</li>

</ol>




<strong>East Lansing city                    | Clinton        |       1969 </strong>

<strong>East Lansing city                    | Ingham         |      46610 </strong>




Multiple entries indicate that parts of the city are located in more than one county.  For the purposes of this assignment, you may treat each entry in the data file as a unique record (you don’t need to combine multiple entries for a given city).


