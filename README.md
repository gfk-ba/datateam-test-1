# Mini database assessment.

## Context

You are given a data file representing information gathered using an online questionnaire. This data can vary in size, from a few records to millions of records, and from a few attributes to many thousands of attributes (columns). You may assume the *raw* data will fit in memory. We want to perform some simple analyses on this data. The speed of the analyses is the *main* focus of this assignment.

## Requirements


### Functional

Your implementation should be capable of the following:
-   Read an input file (format defined later) and parse the data.
-   Perform analyses on the data (details given below).
-   Display or export the results of the analyses.

### Constraints

-   Your import should be linear in the number of data points.

### Submission

-   You must attach a small document with a concise explanation of your design decisions and any short cuts you take in your implementation.
-   Your code has to be written in C++. It should compile with GCC and/or CLang. You must add a description on how to build and execute the program.
-   You are allowed to use *open source* libraries.

### Extensibility 

-   It should be easy to add new data types other than integer and string. 
-   It should also be easy to extend the set of analyses.

### Analyses

All the analyses are aggregations of a single attribute, grouped by another attribute. For example, we want to select the **average movie\_score grouped by age**. Your solution should support the following aggregations:
-   Average
-   Minimum
-   Maximum

The aggregations only operate on integer attributes, the grouping may be on any type of attribute. Aggregations on attributes that are not of integer type should produce an error message.

You do *not* know the analyses at the moment you are importing the data. The queries can change at any time, so do not assume they are static.

#### Aggregation syntax

It is left to the implementer to decide how aggregrations are supplied to the program. For example, the syntax might look like this:

    AVG <aggregation attribute> <grouping attribute>
    MIN <aggregation attribute> <grouping attribute>
    MAX <aggregation attribute> <grouping attribute>

### Input format

The data is supplied using the following format:
-   Each line describes a record, a newline ('\n') character indicates the end of a line.
-   The first line gives the name of each attribute.
-   The second line gives the type of each attribute.
-   The number and type of the attributes can differ with each input file.
-   The values on each line are separated by a single space character.
-   Only integer and string attributes are currently supported.

You may assume the following about the input:

-   The input is valid and uses the format described above.
-   String attributes will never contain a space.
-   Each line will have the same number of attributes (no missing values).

Example input with four attributes:

    first_name age movie_name score
    string integer string integer
    tim 26 inception 8
    tim 26 pulp_fiction 8
    tamas 44 inception 7
    tamas 44 pulp_fiction 4
    dave 0 inception 8
    dave 0 ender's_game 8

Example input with two attributes:

    age income
    integer integer
    15 8000
    20 16000
    25 30000
    30 41230

### Output format

The output format is left to the implementer. You may choose to output to standard out in some readable format or you could export the results to a CSV file.
Example analyses output:

    AVG score GROUPED BY movie_name
    inception      8
    pulp fiction   6
    ender's game   8
    
    MIN age GROUPED BY movie_name
    inception      0
    pulp fiction   26
    ender's game   0

