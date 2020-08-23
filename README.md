Step-by-step process:

- Import CSV file
- Copy original dataframe

OVERALL DATAFRAME EVALUATION
- Examine data for potential issues (look at head, dataframe size, column names)

•	remove leading and trailing whitespaces from column names
•	remove all instances of ':' in column names
•	the column 'Fatal (Y/N)' should be renamed to 'Fatal'
•	replace all whitespaces with '_'
•	replace all instances of '.' with '_'

- Check data types 
('Age' could be changed to int64, and 'Date' could be changed to datetime64. Will investigate this further when looking at each column individually.)

- Look at null values in columns

- Look at null values as a percentage of column
•	remove columns with more than 50% null values
(‘Age’ & Species’ columns have a high number of null values in comparison to the rest of the dataframe, investigate further when looking at each column individually.)

- Look for columns with low variance

INDIVIDUAL COLUMN EVALUATION
Case_Number
- Check if all values are unique
- There are 16 values that are duplicated
Future improvements: look into duplicate values, are they actually duplicate cases? Remove all ‘.’ so that case numbers don’t look too much like a date, have it so that all case numbers have a letter at the end so that all case numbers are in the same format.

Date
•	remove ‘Reported’ on all instances where this is a prefix to the date
•	remove all leading whitespaces
Future improvements: make sure all dates are in the same format (some have a 2 digit year, some have a 4 digit year/some only have a year, some don’t have a day of the month), do something with super old records with inaccurate dates (perhaps delete them?)

Year
•	drop this column as it’s redundant with the presence of the ‘Date’ column

Type
- Look at unique values and group them by count
•	merge ‘Boat’ and ‘Boating’
Future improvements: look into what ‘Invalid’ means as is unclear

Country
- Look at null values and see if they can be replaced by country names based on info in ‘Area’ & ‘Location’ columns
Future improvements: change null values based on info in ‘Area’ & ‘Location’ columns, perhaps change the column so that it isn’t all in uppercase

Area
- Look at unique values and group them by count
Future improvments: appears to be a mix of states, seas and other. Could definitely be tidied up and improved somehow!

Location
- Look at unique values and group them by count
Future improvements: is this category required, could potentially be dropped?

Activity
- Look at unique values and group them by count
Future improvements: could potentially group activities together into categories (eg. anything containing the word 'fishing' anything containg the word 'diving', etc.)?

Name
- Look at unique values and group them by count
Contains an awful lot of values that aren't names, which probably makes this column useless. However, before deleting it, should double check that the 'Sex' column for those with name of 'male', 'female', 'boy', etc., isn't null.
- Looked at instances where ‘Sex’ is null, but ‘Name’ is male
•	created a list for the condition, but couldn’t work out how to replace ‘null’ with ‘M’
Future improvements: use other values in ‘Name’ column such as ‘female’, ‘boy’ to replace ‘null’ values in the ‘Sex’ column – delete the ‘Name’ column once completed.

Sex
- Look at unique values and group them by count
•	remove all trailing whitespaces
- Look further into other non-‘M’ or ‘F’ values
•	replace error values so that all that remains is ‘M’, ‘F’ or null

Age
I wanted to change the data type of this column to ‘int64’, but wasn’t able to do this because of a “cannot convert float NaN to integer” error message. I also thought about binning the ages into categories, but also struggled to make that work.
Future improvements: convert data type to ‘int64’, split into age categories?

Species
Far to my many different values in this column. One way to clean it up would be to remove any measurements and group them into categories such as 'Tiger Shark', 'Bull Shark', 'Dogfish Shark', etc. If you wanted to keep measurements, could have that info in a separate column.
Future improvements: group into categories, add ‘measurement’ column?

Fatal
- Look at unique values and group them by count
•	remove leading and trailing whitespaces
- Look further into other non-‘Y’ or ‘N’ or ‘UNKNOWN’ values
•	replace error values so that all that remains is ‘Y’, ‘N’, ‘UNKNOWN’ or null

Investigator or Source
A messy column, but unsure how to tidy it up. Could possibly delete it, as I’d assume this info is included in the PDF or href links?

PDF


Href & Href Formula
Whilst these columns aren’t exactly identical, they appear to be largely the same, so would consider deleting one of them.

Case Number 1 & Case Number 2
Whilst these columns aren’t exactly identical to each other or to the ‘Case Number’ column, they appear to be largely the same, so would consider deleting both of them.