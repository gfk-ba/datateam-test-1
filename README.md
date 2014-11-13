# Mini database assessment.

## Context

You are given a data file representing information gathered using an online questionnaire. This data can vary in size, from a few records to millions of records (but assume it will generally fit in memory). We want to perform some simple analyses on this data. While the speed of importing the data is not critical, the performance of the analyses is.   

## Requirements

Your implementation should be capable of the following:
-   Read an input file (format defined later) and parse the data.
-   Perform several analyses on the data. The analyses are supplied using a simple syntax.
-   Display or export the results of the analyses.

You should also attach a small document with a concise explanation of your design decisions and any short cuts you take in your implementation.

Your code has to be written in C++. It should compile with GCC and/or CLang. It should compile on GNU/Linux. You need to add a description on how to build and execute the program.

### Analyses

All the analyses are aggregations of a single attribute, grouped by another attribute. For example, we want to select the **average movie\_score grouped by age**. Your solution should support the following aggregations:
-   Average (rounds to the nearest integer)
-   Minimum
-   Maximum

The aggregations only operate on integer attributes, the grouping may be on any type of attribute. Aggregations on attributes that are not of integer type should produce an error message.

#### Aggregation syntax

It is left to the implementer to decide how aggregrations are supplied to the program. The program should parse the following syntax:

    AVG <aggregation attribute> <grouping attribute>
    MIN <aggregation attribute> <grouping attribute>
    MAX <aggregation attribute> <grouping attribute>

### Input format

The data is supplied using the following format:
-   Each line describes a record, a newline ('\n') character indicates the end of a line.
-   The first line gives the name of each attribute.
-   The second line gives the types of each attribute.
-   The number and type of the attributes can differ with each input file.
-   The values on each line are separated by a single space character.
-   Only integer and string attributes are currently supported (but it should be easy within your design to add more attribute types).

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
    pulp fiction   62
    ender's game   0