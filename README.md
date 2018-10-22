# AHRQ
Angency for Healthcare Research and Quality(AHRQ) Safety Culture Analysis 

Title SQL SAS Code;

libname SQLTEST odbc dsn = '_____' schema = 'dbo';

PROC SQL;
 SELECT * FROM _____;
 QUIT;

DATA work._____;
  SET _____;
  

/****************************** STEP 1: CALCULATING COMPOSITE SCORES FOR ALL YEARS *****************************/


/* AHRQ has questions that are negatively worded. The following turns all 
negatively worded AHRQ questions into positively worded variables. The "_r" stands for reversed */

a05_r = 6 - a05;
a07_r = 6 - a07;
a08_r = 6 - a08;
a10_r = 6 - a10;
a12_r = 6 - a12;
a14_r = 6 - a14;
a16_r = 6 - a16;
a17_r = 6 - a17;
b03_r = 6 - b03;
b04_r = 6 - b04;
c06_r = 6 - c06;
f02_r = 6 - f02;
f03_r = 6 - f03;
f05_r = 6 - f05;
f06_r = 6 - f06;
f07_r = 6 - f07;
f09_r = 6 - f09;
f11_r = 6 - f11;
run;

/* Next we create the composite scores using all the positively worded variables. Any analysis done on the AHRQ data 
is done on the 12 standard composite scores, according to the "Hospital survey on 
patient safety culture: items and composites" */

/* change the below to the 'mean' function */

DATA work._____;
  SET work._____;

Teamwork_within_units = (a01 + a03 + a04 + a11) / 4;
Supervisor_manager_expectations = (b01 + b02 + b03_r + b04_r) / 4;
Organization_learning = (a06 + a09 + a13) / 3;
Management_support = (f01 + f08 + f09_r) / 3;
Overall_perceptions = (a15 + a18 + a10_r + a17_r) / 4;
Feedback_and_communication = (c01 + c03 + c05) / 3;
Communication_openness = (c02 + c04 + c06_r) / 3;
Frequency_of_events_reported = (d01 + d02 + d03) / 3;
Teamwork_across_units = (f04 + f10 + f02_r + f06_r) / 4;
Staffing = (a02 + a05_r + a07_r + a14_r) /4;
Handoffs_and_transitions = (f03_r + f05_r + f07_r + f11_r) / 4;
Nonpunitive_response_to_errors = (a08_r + a12_r + a16_r) / 3;
run;



proc gchart data=_____;
vbar a01;
run;


proc means data=_____;
run;


/******** STEP 2: STANDARDIZING THE SPELLING OF EACH USER'S RESPONSE, THEN CREATING THE LOCATION COLUMN ********/





DATA work._____;
  SET work._____;

if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Site = '_____' or Site = '_____' then Site = '_____';
if Site = '_____' or Site = '_____' or Site = '_____' then Site = '_____';
if Site = '_____' or Site = '_____' then Site = '_____';
if Site = '_____' then Site = '_____';
if Site = '_____' or Site = '_____' then Site = '_____';
if Site = '_____' then Site = '_____';
if Site = '_____' then Site = '_____';
if Site = '_____' then Site = '_____';

if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';
if Unit = '_____' then Unit = '_____';

/* Creating the location column, which is used for analysis */
location = Unit; 

if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";
else if Unit = "" and Site = "_____" then location = "_____";

if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "_____" and Site = "_____" then location = "_____";


if Unit = "_____" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "Other" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";
else if Unit = "Other" and Site = "_____" then location = "_____";


if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
If Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' then location = '_____';
if Unit = '_____' AND Area = '_____' then location = '_____';
if Unit = '_____' AND Area = '_____' then location = '_____';
if Unit = 'Other' and Area = '_____' then location = '_____';
if Unit = 'Other' and Area = '_____' then location = '_____';
if Unit = '[unknown]' then location = 'Other';
if Unit = '[unknown]' and Area = '_____' then location = '_____';
if Unit = '[unknown]' AND Area = '_____' then location = '_____';
run;




/******************* STEP 3: CALCULATING AHRQ AVEGRAGE COMPOSITE SCORES FOR EACH LOCATION **********************/



/* Calculate the average composite scores for each location
ie if there are 200 rows with location = _____, then all 200 scores for each composite is averaged to get 
avg composite scores per lcoation, into one single row. Then a table is outputted, consistign of the list 
of locations and their respective scores*/
/*
DATA work._____;
  SET work._____;*/

%let year1 = _____;
%let year2 = _____;
%let year3 = _____;
%let year4 = _____;  	* add "%let _____ = '__current year__'" to include the most recent data year;
%let output = _____;

%macro averages;

%do i = 1 %to 4;

proc means data= _____ nway;  *insert merged dataset here;
class location;
var Teamwork_within_units Supervisor_manager_expectations Organization_learning Management_support Overall_perceptions Feedback_and_communication Communication_openness
Frequency_of_events_reported Teamwork_across_units Staffing Handoffs_and_transitions Nonpunitive_response_to_errors;
Where year = "&&year&i";
output out=&output.&&year&i;
run;

/*The proc means function outputs the following under the _STAT_ column: 
number of observations (N), mean, standard deviation, minimum, and maximum, but WE ONLY WANT 
THE MEAN ROW. 1 ROW PER LOCATION. Delete the extra rows of info that were ouputted with the proc means.
DROP the STAT and TYPE columns.

/*RENAME _FREQ_ TO 'NUM OF RESPONSES'. WE DO NOT WANT TO CONFUSE WITH NUMBER OF RISQ EVENTS.
/*RENAME THE COMPOSITE VARIABLES TO BE CLEAR OF WHAT THEY ARE NOW. */

data &output.&&year&i (DROP= _STAT_ _TYPE_);
set &output.&&year&i ;
if _stat_ = "STD" or _stat_ = "N" or _stat_ = "MIN" or _stat_ = "MAX" then delete;
rename _FREQ_ = Num_of_Responses;
rename 
     Teamwork_within_units = AVG_Teamwork_within_units
     Supervisor_manager_expectations = AVG_Supervisor_Expectations
     Organization_learning = AVG_Organization_learning
     Management_support = AVG_Management_support
     Overall_perceptions = AVG_Overall_perceptions
     Feedback_and_communication = AVG_Feedback_and_communication
     Communication_openness = AVG_Communication_openness
     Frequency_of_events_reported = AVG_Frequency_of_events
     Teamwork_across_units = AVG_Teamwork_across_units
     Staffing = AVG_Staffing
     Handoffs_and_transitions = AVG_Handoffs_and_transitions
     Nonpunitive_response_to_errors = AVG_Nonpunitive_response ;

run;


/*SORT THE DATA TO MATCH THE ORDER OF THE RISQ DATASET*/
proc sort data=&output.&&year&i;
by Location;
run;

%end;

%mend;
%averages;

/* There has now been _____ tables generated (_____) which will be used for analysing
AHRQ data V.S _____ or _____ data */





/******************** STEP 4: ALTERING _____ DATA STRUCTURE TO MATCH AHRQ'S DATA STRUCTURE *******************/




/* The following code alters the _____ data structure so that it matches the same data structure formate as the 
AHRQ data. This allow for statiscial analysis comparing the RISQ data that corresponds to the year of AHRQ data */



DATA ______;
  SET ______;

/*Delete NULL and make columns for each severity level*/
If _____ = '_____' then delete;
if _____ = '_____' then _____ = 1; else _____ = 0;
if _____ = '_____' then _____ = 1; else _____ = 0;
if _____ = '_____' then _____ = 1; else _____ = 0;
if _____ = '_____' then _____ = 1; else _____ = 0;
if _____ = '_____' then _____ = 1; else _____ = 0;
run;


data _____;
set _____;

/* Making a 'location' column that matches the contents of the AHRQ 'location' column. Using the 'site', 'department', and 'program' columns from _____ */

Location = site;

if location = '_____' then location = 'Other';

if site = '_____' and program = '_____' then location = '_____';

if site = '_____' and program = '_____' then location = '_____';

if site = '_____' and department = '_____' or department = '_____' 
	or department = '_____' then location = '_____U';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';          
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';

if site = '_____' and department = '_____' or department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';

if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';

if site = '_____' and department = '_____' then location = '_____';
if site = '_____' and department = '_____' then location = '_____';

if site = '_____' and program = '_____' then location = '_____';
if site = '' and program = '' then location = '';

if site = '_____' then location = '_____';

if site = '_____' or site = '_____' or site = '_____' or site = '_____' or site = '_____' 
		or site = '_____' or site = '_____' or site = '_____' or site = '_____'
		then location = 'Other';

if site = '_____' and program = '_____' then location = '_____';

/* '_____' and '_____' were not sent to 'other' because AHRQ years besides 2018 include these as locations */
run;


/* At this point the RISQ data has a 'location' column that matches the format of the AHRQ data. 
Statistical analysis can now be applied to the data sets */


