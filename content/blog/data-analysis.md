+++
title="Data analysis"
date=2023-09-22
draft=true
+++

- How data is generated
- different formats, types, and structures of data
- data analysis for bias and credibility
- clean data
- databases, spreadsheets, SQL
- data organization
- data protection

Determining what data to collect:

"What's causing increased traffic in your city"

- How will data be collected?
- Choose data sources (first party (own resources), second party data (collected directly from audience and sold), third party data (collected from other sources and then sold))

all data should be inspected for accuracy and trustworthiness.

- Decide what data to use to solve your business problem
- How much data to collect: make reasonable decisions about sample size
- Time frame: decide how long you will need to collect the data; if you need immediate answers, you would need to use historical data.

Quantitative, qualitative data

discrete data: countable
continuous data: decimal places
nominal: no sequence (quantitative)
ordinal: has sequence
internal data: data living within a company's systems.

Structured data: structured thinking... having framework for the data makes it awesome. stored in rows and columns

tables, spreadsheet, relational database.

Unstructured: emails, photos, etc. data lakes, no sql.

Data model: used for organizing data elements and their relationships.
Enter, query, analyze data whenever needed. Structured data can be directly applied to most visual representations of data.

Spreadsheets, databases.


data modelling -- creating diagrams that visually represent how data is organize and structured.

- conceptual: high-level view of the data structure and how it interacts across an organization
- logical: technical details of database like relationships, attributes, entities.
- physical: how a database operates, with all entities and attrributes used.

https://www.1keydata.com/datawarehousing/data-modeling-levels.html

Data type: specific data attribute that tells you what the data is.

Spreadsheet: number, text or string, boolean


Common pattern: strings are not used in calculations but can represent everything else.

Arranged in tables: tabular data has very simple structure. Rows-> records; columns-> fields.

Wide data: every data subject has a single row with multiple columns to hold the values of various attributes of the subject.

Easy to compare between different records.


Long data format: each record represents a time point per subject, so each subject will have data in multiple rows.

Data transformation: changing data's format, structure, values.

Adding, copying, replicating data; deleting fields or records; standardizing names of variables, renaming, moving, combining columns in database; joining one set of data with another; saving a file in a different format.


Why? 

Organization -- easier to use
Compatibility -- between systems
Migration
Merging
Enhancement
Comparison


Wide data preferred: creating tables and charts with a few variables about each subject, comparing straightforward line graphs.

Long data preferred: storing a lot of variables about each subject; performing advanced statistical analysis or graphing.

## Analyze for bias and credibility

Bias: preference in favor of or against a person, thing (subconscious, conscious)

Data bias: error that systematically skews answers in a certain direction.

Analysts must think about bias and fairness.

Sampling bias: when sample isn't representative of population as a whole. Choose random samples.

Unbiased sampling: sample that is representative of the population surveyed.

Bias in data: observer bias, interpretation bias, confirmation bias

observer bias: tendency for different people to observe things differently. (experimental bias)

- Interpretation bias: a tendency to interpret ambiguous situations in a positive or negative way.

Confirmation bias: tendency to search for or interpret information that affirms a particular view.

## Good data sources

- Reliable: accurate, trustworthy, and complete
- Original: validate it with the original source
- Comprehensive: has all the data necessary for you to make a decision
- Current: usefulness of data decreases as time passes
- Cited: citing a source for credibility

Vetted public data sets

Reliability evaluation: inaccurate or biased.
Original: cannot find original source of the data.

Ethics: well-founded standards of right and wrong
Data ethics: how data is collected, shared, and used 

- GDPR

Governing collection principles:

- Ownership: people own data (raw data)
- Transaction transparency: all data-processing activities should be completely explainable
- Consent: individual's rights to know explicitly how their data will be used and why it is being used
- Currency: people should know when financial transactions resulting from the use of their personal data
- Privacy: protection from unauthorized data access; freedom from inappropriate data use; right to inspect, update, correct data; ability to give consent to use our data; legal right to access data
- Openness: Free access, usage and sharing of data

Data anonymization: personally identifiable information can be used to track down a person's identity, so PII is eliminating that kind of information while maintaining the otherwise usefulness of the data.

Common anonymized data:

- telephone numbers, names, license plate/social security numbers, ip addresses, medical records, email addresses, photographs, account numbers.

Open data: 

- availability and access: should be available in whole and downloadable.
- reuse and redistribution: should be provided with terms that allow reuse and redistributioin
- universal participation

Credible databases can be used more widely.

Data interoperability: ability of data systems and services to openly connect and share data.

## Databases

metadata: data about data. Reference guide providing context.

data analysis phases:

- ask
- prepare
- process
- analyse
- share
- act

Relational database: series of related tables that can be connected via their relationships.

If a field exists in both tables, they can be connected to each other.

Primary key: unique identifier for each record. Cannot be null or blank. ensure data in specific column is unique.
Foreign key: field within a table that is a primary key in another table. Column or group of columns in a relational database that provides a link between data in two tables.

Database normalization: organizing data into a relational database. 

Composite key: type of primary key constructed using multiple columns of a table.

Metadata: Interpret the contents of the data within the database.
Puts data into perspective.

Types: 

- descriptive, describes piece of data and can be used to identify it at a later point in time.
- structural metadat: how a piece of  data is organized and whether it is part of one, or more colelctions. Keeps track of relationships between two things.
- Adminsitrative metadata: technical source of a data source.

Advantages:

- creates single source of truth by keeping things consistent and uniform
- makes data more reliable by making sure its accurate, precise, relevant, and timely

Metadata repository: database specifically created to store metadata.
- Describe where metadata comes from, in a common structure, and make it easier and faster to bring together multiple sources for data analysis.
- Describe state and location of metadata
- Describe structures of the tables inside
- Describe how the data flows through the repository
- Keep track of who accesses the metadata and when

standardization of processes

## Metadata

metadata can be stored in a single, central location and give the company standardized information about all of its data.

data governance: formal management of the data assets a company has.

## Data sources

Internal: advantages: relevant, free

External: advantages: open data

IMporting data: IMPORTRANGE, IMPORTHTML, CSV.

Sorting, filtering: necessary to solve problems with large data.

Sorting: arranging data in specific order.

Freezing rows is useful


Isolating pieces of information :showing only data that meets a certain criteria
## SQL

BigQuery.
BigQuery SQL workspace.

## Organizing data

Best practices:

- naming conventions: meaningful, include project name information, date version numbers in filenames, etc.
- foldering
- archiving old files
- align naming and storage practices with your team
- develop metadata practices

Logical descriptive names for your files to make them easier to find and use.

## Security features

Data security - unauthorized access or corruption.
Access control features
Encryption: alters data using algorithm saved by key
Tokenization: replaces protected data elements with randomly generated data. Random data is then mapped to the original data.

Security < --- conflicts --> access to data

## Schemas

## Clean data

Data integrity: strong analysis depends on the data integrity.
Accuracy, completeness, consistency, and trustworthiness
Data replication: lacks integrity if there is lag
Data transfer: could be incorrect (incomplete data set)
Data manipulation: process of changing data

Data integrity often depends on using a common format.

- Data replication could compromise data integrity
- Data transfer could compromise data integrity
- Data manipulation could compromise data integrity

Data constraint
	

Definition
	

Examples

Data type
	

Values must be of a certain type: date, number, percentage, Boolean, etc.
	

If the data type is a date, a single number like 30 would fail the constraint and be invalid

Data range
	

Values must fall between predefined maximum and minimum values
	

If the data range is 10-20, a value of 30 would fail the constraint and be invalid

Mandatory
	

Values can’t be left blank or empty
	

If age is mandatory, that value must be filled in

Unique
	

Values can’t have a duplicate
	

Two people can’t have the same mobile phone number within the same service area

Regular expression (regex) patterns
	

Values must match a prescribed pattern
	

A phone number must match ###-###-#### (no other characters allowed)

Cross-field validation
	

Certain conditions for multiple fields must be satisfied
	

Values are percentages and values from multiple fields must add up to 100%

Primary-key
	

(Databases only) value must be unique per column
	

A database table can’t have two rows with the same primary key value. A primary key is an identifier in a database that references a column in which each value is unique. More information about primary and foreign keys is provided later in the program.

Set-membership
	

(Databases only) values for a column must come from a set of discrete values 
	

Value for a column must be set to Yes, No, or Not Applicable

Foreign-key
	

(Databases only) values for a column must be unique values coming from a column in another table
	

In a U.S. taxpayer database, the State column must be a valid state or territory with the set of acceptable values defined in a separate States table

Accuracy
	

The degree to which the data conforms to the actual entity being measured or described
	

If values for zip codes are validated by street location, the accuracy of the data goes up.

Completeness
	

The degree to which the data contains all desired components or measures
	

If data for personal profiles required hair and eye color, and both are collected, the data is complete.

Consistency
	

The degree to which the data is repeatable from different points of entry or collection
	

If a customer has the same address in the sales and repair databases, the data is consistent.

## Dealing with data issues

1. No data: gather data on small scale to perform preliminary analysis, or perform analysis using proxy data from other datasets
2. Too little data: do the analysis using proxy data along with actual data, or adjust your analysis to align with the data you already have.
3. Wrong data (data with errors): if because requirements misunderstood, communicate requirements; identify errors and correct them at the source if possible; ignore wrong data and go ahead with analysis if sample size is still large enough and ignoring the data will not cause bias.

## Sample size

Using part of a population representative of the entire population.
Goal is to get enough info from small group to make predictions about the whole population.
Sampling bias: when a sample isn't representative of the populaton as a whole.
Using random sampling helps address all sorts of bias.

- Population: entire group you are interested in for your study
- Sample: subset of your population
- Margin of error: percentage difference between your sample's results and the population, statistically
- Confidence level: How confident you are in the survey results: 95% confidence means that if you were to run the same survey 100 times, you woudl get similar results 95 of those times.
- Confidence interval: range of possible values that the population's result would be at the confidence level of the study. Sample result +/- margin of error.
- Statistical significnace: determination of whether your result could be due to random chance or not.

Don't use a sample size less than 30. (Smallest sample size where average sample result starts to represent average result of population)

- Because of Central Limit Theorem. Regression analysis also prefers this.

Confidence level most commonly used is 95%, although 90% is acceptable.

- Higher confidence level: use larger sample size
- Decrease margin of error: larger sample size
- Greater statistical significance: larger sample size

## Statistical power

Probability of getting meaningful results from a test. Value out of 1. Percentage chance of getting meaningful results from a survey.
YOu need >80% statistical power to have significant results.

Public datasets can be proxy datasets as well.

## Margin of error

based on sample size, margin of error will tell us the deviation to the expected results of a nation-wide population.

- Population size
- Sample size
- Confidence interval

Maximum amount sample results are expected to differ from those of the actual population.

## Clean data

Dirty data: incomplete, incorrect, or irrelevant data 

- Duplicate data
- Outdated data
- Incomplete data
- Incorrect/inaccurate data
- Inconsistent data

Data engineers : transform data 
Data warehousing specialists: make sure data is available, secure, and backed up
Null: value does not exist in a dataset

Make a copy of your raw dataset before any modifications to.

- Remove duplicates
- Remove irrelevants
- Remove extra whitespace
- Fix misspelllings, punctuation, capitalization to standard formats
- Remove formatting

Cleaning data from multiple sources

Data merging: combining two or more datasets into a single data set
Compatibility: how well N datasets can work together

- Do I have all the data I need?
- Does the data I need exist within these datasets?
- Do the datasets need to be cleaned, or are they ready for me to use?
- Are they cleaned to the same standard?

    Not checking for spelling errors: Misspellings can be as simple as typing or input errors. Most of the time the wrong spelling or common grammatical errors can be detected, but it gets harder with things like names or addresses. For example, if you are working with a spreadsheet table of customer data, you might come across a customer named “John” whose name has been input incorrectly as “Jon” in some places. The spreadsheet’s spellcheck probably won’t flag this, so if you don’t double-check for spelling errors and catch this, your analysis will have mistakes in it. 

    Forgetting to document errors: Documenting your errors can be a big time saver, as it helps you avoid those errors in the future by showing you how you resolved them. For example, you might find an error in a formula in your spreadsheet. You discover that some of the dates in one of your columns haven’t been formatted correctly. If you make a note of this fix, you can reference it the next time your formula is broken, and get a head start on troubleshooting. Documenting your errors also helps you keep track of changes in your work, so that you can backtrack if a fix didn’t work. 

    Not checking for misfielded values: A misfielded value happens when the values are entered into the wrong field. These values might still be formatted correctly, which makes them harder to catch if you aren’t careful. For example, you might have a dataset with columns for cities and countries. These are the same type of data, so they are easy to mix up. But if you were trying to find all of the instances of Spain in the country column, and Spain had mistakenly been entered into the city column, you would miss key data points. Making sure your data has been entered correctly is key to accurate, complete analysis. 

    Overlooking missing values: Missing values in your dataset can create errors and give you inaccurate conclusions. For example, if you were trying to get the total number of sales from the last three months, but a week of transactions were missing, your calculations would be inaccurate.  As a best practice, try to keep your data as clean as possible by maintaining completeness and consistency.

    Only looking at a subset of the data: It is important to think about all of the relevant data when you are cleaning. This helps make sure you understand the whole story the data is telling, and that you are paying attention to all possible errors. For example, if you are working with data about bird migration patterns from different sources, but you only clean one source, you might not realize that some of the data is being repeated. This will cause problems in your analysis later on. If you want to avoid common errors like duplicates, each field of your data requires equal attention.

    Losing track of business objectives: When you are cleaning data, you might make new and interesting discoveries about your dataset-- but you don’t want those discoveries to distract you from the task at hand. For example, if you were working with weather data to find the average number of rainy days in your city, you might notice some interesting patterns about snowfall, too. That is really interesting, but it isn’t related to the question you are trying to answer right now. Being curious is great! But try not to let it distract you from the task at hand.  

    Not fixing the source of the error: Fixing the error itself is important. But if that error is actually part of a bigger problem, you need to find the source of the issue. Otherwise, you will have to keep fixing that same error over and over again. For example, imagine you have a team spreadsheet that tracks everyone’s progress. The table keeps breaking because different people are entering different values. You can keep fixing all of these problems one by one, or you can set up your table to streamline data entry so everyone is on the same page. Addressing the source of the errors in your data will save you a lot of time in the long run. 

    Not analyzing the system prior to data cleaning: If we want to clean our data and avoid future errors, we need to understand the root cause of your dirty data. Imagine you are an auto mechanic. You would find the cause of the problem before you started fixing the car, right? The same goes for data. First, you figure out where the errors come from. Maybe it is from a data entry error, not setting up a spell check, lack of formats, or from duplicates. Then, once you understand where bad data comes from, you can control it and keep your data clean.

    Not backing up your data prior to data cleaning: It is always good to be proactive and create your data backup before you start your data clean-up. If your program crashes, or if your changes cause a problem in your dataset, you can always go back to the saved version and restore it. The simple procedure of backing up your data can save you hours of work-- and most importantly, a headache. 

    Not accounting for data cleaning in your deadlines/process: All good things take time, and that includes data cleaning. It is important to keep that in mind when going through your process and looking at your deadlines. When you set aside time for data cleaning, it helps you get a more accurate estimate for ETAs for stakeholders, and can help you know when to request an adjusted ETA.

## Data cleaning

- Conditional formatting can help
- Highlight potential incorrect dirty data
- Remove duplicates
- Text string: is a group of characters within a cell. Important characteristic: length
	- Substring: smaller subset of a text string
- Split function by delimiter
- Useful functions
	- COUNTIF: count if any data in cells is outside an expected range
	- LEN: length of a text string
	- LEFT, RIGHT: set of characters to the left or right of a delimiter
	- CONCATENATE: joins together the items
	- TRIM

## Pivot tables

Sort, reorganize, group, count, total or average data stored in your database.
Can give a quick, clutter-free view of your data.

## Data mapping

Matching fields from one dataset to another

First step: identifying what data needs to be moved (tables and fields within)
Then define the desired format for the data once it reaches its destination.

Schema: way of describing how something is organized
consistent naming conventions. 

## SQL datacleaning

Structured query language to work with databases.
Relational database: series of tables that can be connected to form relationships.

Widely used SQL queries:

```sql
SELECT
	name,
	city
FROM
	customer_data.customer_address
```

```sql
INSERT INTO customer_data.customer_address
	(customer_id, address, city, state, zipcode, country)
VALUES
	(2645, '333 SQL Road', 'Jackson', 'MI', 49202, 'US')
```

```sql
UPDATE customer_data.customer_address
SET address = '123 New Address'
WHERE customer_id = 2645
```

```sql
CREATE TABLE IF NOT EXISTS
```

```sql
DROP TABLE IF EXISTS
```

### Cleaning string variables

remove duplicates

```sql
SELECT
	DISTINCT customer_id
FROM
	customer_data.customer_address
```

```sql
SELECT
	country
FROM
	customer_data.customer_address
WHERE
	LENGTH(country) > 2
```

Substring function: SUBSTR
Trim: TRIM()

CAST function:

```sql
SELECT
	CAST(purchase_price AS FLOAT64)
FROM
	customer_data.customer_purchase
ORDER BY
	CAST(purchase_price AS FLOAT64) DESC
```

Typecasting to make sure prices, etc. are numbers

CONCAT
COALESCE

## Verifying and reporting results

Verification: confirm that data cleaning was well-executed and reliable.

Rechcking, manual cleanups, and taking moment to sit back and think of project original purpose.

Reports: super effective way to show team you are being transparent about the data cleaning: tell stakeholders you are accountable

Changelog with versions.

Taking a problem-first approach is essential at all stages of any project.

Correct the most common problems

Make sure you identified the most common problems and corrected them, including:

    Sources of errors: Did you use the right tools and functions to find the source of the errors in your dataset?

    Null data: Did you search for NULLs using conditional formatting and filters?

    Misspelled words: Did you locate all misspellings?

    Mistyped numbers: Did you double-check that your numeric data has been entered correctly?

    Extra spaces and characters: Did you remove any extra spaces or characters using the TRIM function?

    Duplicates: Did you remove duplicates in spreadsheets using the Remove Duplicates function or DISTINCT in SQL?

    Mismatched data types: Did you check that numeric, date, and string data are typecast correctly?

    Messy (inconsistent) strings: Did you make sure that all of your strings are consistent and meaningful?

    Messy (inconsistent) date formats: Did you format the dates consistently throughout your dataset?

    Misleading variable labels (columns): Did you name your columns meaningfully?

    Truncated data: Did you check for truncated or missing data that needs correction?

    Business Logic: Did you check that the data makes sense given your knowledge of the business? 

Review the goal of your project

Once you have finished these data cleaning tasks, it is a good idea to review the goal of your project and confirm that your data is still aligned with that goal. This is a continuous process that you will do throughout your project-- but here are three steps you can keep in mind while thinking about this: 

    Confirm the business problem 

    Confirm the goal of the project

    Verify that data can solve the problem and is aligned to the goal 

### Documentation

- Recover from errors in data-cleaning
- Create new cleaned data set; don't modify original raw data
- Determine quality
- Inform other users of changes

Use a changelog: version history

Specify what you did and why when you commit a query in SQL.

IMPORTRANGE
QUERY
FILTER

SQL CASE statement.

### Writing a good resume

PAR: Problem, Action, Result

1. Structured Query Language (SQL): SQL is considered a basic skill that is pivotal to any entry-level data analyst position. SQL helps you communicate with databases, and more specifically, it is designed to help you retrieve information from databases. Every month, thousands of data analyst jobs posted require SQL, and knowing how to use SQL remains one of the most common job functions of a data analyst. 

2. Spreadsheets: Although SQL is popular, 62% of companies still prefer to use spreadsheets for their data insights. When getting your first job as a data analyst, the first version of your database might be in spreadsheet form, which is still a powerful tool for reporting or even presenting data sets. So, it is important for you to be familiar with using spreadsheets for your data insights.

3. Data visualization tools: Data visualization tools help to simplify complex data and enable the data to be visually understood. After gathering and analyzing data, data analysts are tasked with presenting their findings and making that information simple to grasp. Common tools that are used in data analysis include Tableau, Microstrategy, Data Studio, Looker, Datarama, Microsoft Power BI, and many more. Among these, Tableau is best known for its ease of use, so it is a must-have for beginner data analysts. Also, studies show that data analysis jobs requiring Tableau are expected to grow about 34.9% over the next decade.

4. R or Python programming: Since only less than a third of entry-level data analyst positions require knowledge of Python or R, you don’t need to be proficient in programming languages as an entry-level data analyst. But, R or Python are great additions to have as you become more advanced in your career. 

1. Presentation skills

Although gathering and analyzing data is a big part of the job, presenting your findings in a clear and simple way is just as important. You will want to structure your findings in a way that allows your audience to know exactly what conclusions they are supposed to draw. 

2. Collaboration 

As a data analyst, you will be asked to work with lots of teams and stakeholders—sometimes internal or external—and your ability to share ideas, insights, and criticisms will be crucial. It is important that you and your team—which might consist of engineers and researchers—do your best to get the job done. 

3. Communication

Data analysts must communicate effectively to obtain the data that they need. It is also important that you are able to work and clearly communicate with teams and business leaders in a language that they understand. 

4. Research 

As a data analyst, even if you have all of the data at your disposal, you still need to analyze it and draw crucial insights from it. To analyze the data and draw conclusions, you will need to conduct research to stay in-line with industry trends. 

5. Problem-solving skills 

Problem-solving is a big part of a data analyst’s job, and you will encounter times when there are errors in databases, code, or even the capturing of data. You will have to adapt and think outside the box to find alternative solutions to these problems.

6. Adaptability 

In the ever-changing world of data, you have to be adaptable and flexible. As a data analyst, you will be working across multiple teams with different levels of needs and knowledge, which requires you to adjust to different teams, knowledge levels, and stakeholders.  

7. Attention to detail 

A single line of incorrect code can throw everything off, so paying attention to detail is critical for a data analyst. When it comes to understanding and reporting findings, it helps if you focus on the details that matter to your audience. 
Adding soft skills to your resume

Here are a few ways that you can add soft skills to your resume:

    Analyze your previous work experience and find opportunities to insert a soft skill. For example, if you worked in a restaurant, you could emphasize your communication and adaptability skills that you utilized to effectively function during peak hours. 

    Call attention to your problem-solving, presentation, research, and communication skills in previous projects or relevant coursework.

    Add a mix of soft and professional skills in the skills or summary section of your resume.

## Sorting functions

ORDER BY clause 

```sql
SELECT *
FROM `movie_data.movies`
WHERE Genre = "Comedy"
AND Revenue > 300000000
ORDER BY Release_Date DESC
```

Default: ascending order; descending is using DESC

## Data formatting

Important to double check all your data is in the right format before you begin your analysis.

CONVERT function is useful.

Data validation: spreadsheet feature
Allows you to control what can and can't be entered into a spreadsheet
Dropdown that allows you to choose only from a set of choices.
Conditional formatting: spreadsheet feature that changes formatting of cells based on values from the spreadsheet. Can be used with data validation feature to make custom tools for spreadsheet.

Concatenation in SQL:

```sql
SELECT
	usertype,
	CONCAT(start_station_name, " to ", end_station_name) AS route,
	COUNT(*) as num_trips,
	ROUND(AVG(CAST(tripduration as int64)/60).2) AS duration
FROM
	`bigquery-public-data.new_york_citibike_trips`
GROUP BY
	start_station_name, end_station_name, usertype
ORDER BY
	num_trips DESC

```


Manipulating strings in SQL

Knowing how to convert and manipulate your data for an accurate analysis is an important part of a data analyst’s job. In this reading, you will learn about different SQL functions and their usage, especially regarding string combinations. 

A string is a set of characters that helps to declare the texts in programming languages such as SQL. SQL string functions are used to obtain various information about the characters, or in this case, manipulate them. One such function, CONCAT, is commonly used. Review the table below to learn more about the CONCAT function and its variations.

Function
	

Usage
	

Example

CONCAT
	

A function that adds strings together to create new text strings that can be used as unique keys
	

CONCAT (‘Google’, ‘.com’);

CONCAT_WS
	

A function that adds two or more strings together with a separator
	

CONCAT_WS (‘ . ’, ‘www’, ‘google’, ‘com’)

*The separator (being the period) gets input before and after Google when you run the SQL function

CONCAT with +
	

Adds two or more strings together using the + operator
	

‘Google’ + ‘.com’
CONCAT at work

When adding two strings together such as ‘Data’ and ‘analysis’, it will be input like this: 

    SELECT CONCAT (‘Data’, ‘analysis’);

The result will be:

    Dataanalysis


Sometimes, depending on the strings, you will need to add a space character, so your function should actually be:

    SELECT CONCAT (‘Data’, ‘  ‘, ‘analysis’);

And the result will be:

    Data analysis


The same rule applies when combining three strings together. For example,

    SELECT CONCAT (‘Data’,’ ‘, ‘analysis’, ‘ ‘, ‘is’, ‘ ‘, ‘awesome!’);

And the result will be

    Data analysis is awesome!

Practice makes perfect

W3 Schools is an excellent resource for interactive SQL learning, and the following links will guide you through transforming your data using SQL:

    SQL functions

    : This is a comprehensive list of functions to get you started. Click on each function, where you will learn about the definition, usage, examples, and even be able to create and run your own query for practice. Try it out for yourself!   

    SQL Keywords

    : This is a helpful SQL keywords reference to bookmark as you increase your knowledge of SQL. This list of keywords are reserved words that you will use as your need to perform different operations in the database grows.

    While this reading went through the basics of each of these functions, there is still more to learn, and you can even combine your own strings.

    Practice using CONCAT

*Practice using CONCAT WS

Practice using CONCAT with +

Pro tip: The functions presented in the resources above may be applied in slightly different ways depending on the database that you are using (e.g. mySQL versus SQL Server). But, the general description provided for each function will prepare you to customize how you use these functions as needed. 

LIMIT 80 for the first 80 records.

## Data aggregation

process of gathering data from multiple sources to combine it into a single, summarized collection.

For spreadsheets: use VLOOKUP, function searching for a certain value in a column to return a corresponding piece of information.

`=vlookup(A2, 'Employee Rates'!$A$2:$B$5,2,FALSE)`

 Two common reasons to use VLOOKUP are:

    Populating data in a spreadsheet 

    Merging data from one spreadsheet with data in another  

## JOINS

SQL clause used to combine rows from two or more tables based on a related column.

INNER JOIN: only rows in BOTH table 1 and 2
LEFT JOIN: all rows from table 1 and ONLY MATCHING ROWS in table 2
RIGHT JOIN: all rows from table 2 and ONLY MATCHING ROWS from table 1
FULL OUTER JOIN: all rows from table 1 and all rows from table 2

```
SELECT 
	employees.name AS employee_name,
	employees.role AS employee_role,
	departments.name AS department_name
FROM 
	employee_data.employees
INNER JOIN
	employee_data.departments ON
	employees.department_id = departments.department_id
```

Aliases are used in SQL queries to create temporary names for a column or table. Aliases make referencing tables and columns in your SQL queries much simpler when you have table or column names that are too long or complex to make use of in queries.

```
SELECT column
FROM table_name AS alias_name;
```

COUNT - count total number of numerical values in SQL.
COUNT DISTINCT - only returns distinct values in specified range.
Answer questions about "how many"

```
SELECT
	COUNT(DISTINCT warehouse.state) as num_states
FROM
	warehouse_orders.Orders orders
JOIN
	warehouse_orders.warehouse warehouse ON orders.warehouse_id = warehouse.warehouse_id
GROUP BY
	warehouse.state
```

## Subqueries

Query nested in larger query.

Statement containing query: Outer query; subquery also called INNER QUERY

```sql
SELECT
	station_id,
	num_bikes_available,
	(SELECT
		AVG(num_bikes_available)
	FROM bigquery-public-data.new_york.citibike_stations) AS avg_num_bikes_available
FROM
	bigquery-public-data.new_york.citibike_stations
```

Using subqueries to aggregate data.

HAVING - add a filter to your query instead of the underlying table that can be only used with aggregate functions
CASE - return records with your conditions by allowing you to include if/then statements in your query

You will find that, within the first SELECT clause is another SELECT clause. The second SELECT clause marks the start of the subquery in this statement. There are many different ways in which you can make use of subqueries, and resources referenced will provide additional guidance as you learn. But first, let’s recap the subquery rules. 

There are a few rules that subqueries must follow:

    Subqueries must be enclosed within parentheses

    A subquery can have only one column specified in the SELECT clause. But if you want a subquery to compare multiple columns, those columns must be selected in the main query.

    Subqueries that return more than one row can only be used with multiple value operators, such as the IN operator which allows you to specify multiple values in a WHERE clause.

    A subquery can’t be nested in a SET command. The SET command is used with UPDATE to specify which columns (and values) are to be updated in a table.

## Data calculations

- SUM, AVERAGE, MIN, MAX, COUNTIF, SUMIF, adds numeric data using one condition

SUMIFS for multiple conditions

- SUMPRODUCT: adds and multiplies

### Pivot tables

View data in multiple ways to find insights and trends.
Can help with calculations.l

Calculated field - new field within a pivot table that carries out calculations based on values of other fields.

SQL operators: percent symbol (reminder when one number is divided by another.)

## Temp SQL tables

## ask prepare process analyze share and act

## R programming language




