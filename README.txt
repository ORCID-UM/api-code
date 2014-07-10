Attached are the two files used to obtain ORCID iDs using the curl command: 
(1) process-orcid-generic - this is the actual perl script that does the work
(2) xml - this is a template file used by process-orcid-generic.

Here is some documentation on these files, and attached are the two files.  

process-orcid-generic (executable script written in Perl):
This script issues commands to ORCID to generate iDs. You will find a summary of how it works at the top of the file, 
and there is a section called GLOBAL VARIABLES indicating where and how the user will have to setup some directories, access values to ORCID, 
and database connection parameters.

xml:
This file is a template used by process-orcid-generic.  You will have to change the following parameteres:

AFFILIATION_TYPE
DEPARTMENT
CITY
STATE
COUNTRY
ID_CODE
SOURCE

Also, make sure this file lives in the directory indicated in the GLOBAL VARIABLES section of process-orcid.

id file:
You will need to create a file containing names and emails for which you want ORCID iDs. This file should be tab 
delimited and of the format:

lastname<tab>firstname<tab>email<tab>other_email<tab><return>

You will identify the name and location of this file in process-orcid-generic

database:
You will have to create a database containing one table. In process-orcid-generic, you will configure the connection 
parameters to your database.


Here is the 'create' command for the table you will need:
CREATE TABLE orcidrecords
(
  date         varchar(100),
  lastname     varchar(250),
  firstname    varchar(250),  
  email        varchar(250),
  id           text
);

This table is used to keep track of the ORCID iDs created by the script.
