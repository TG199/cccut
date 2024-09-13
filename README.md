# cccut - A simple Unix Cut Tool

**cccut** is a simple implementation of the Unix `cut` command that allows users to extract specific fields from a file. This tool supports specifying delimiters, selecting multiple fields, and working with standard input for flexible data extraction and processing.

## Features
1. Extract fields from tab-separated files.
2. Support for custom delimiters using the `-d` option.
3. Select specific fields or multiple fields using the `-f` option.
4. Support reading from standard input or a file.
5. Chain with other Unix commands using pipes for data processing.

## Requirements
- Python 3.8

## Installation
Clone the repository to your local machine:
```bash
git clone https://github.com/TG199/cccut.git
cd cccut
```
Make sure the script is executable:
```bash
chmod +x cccut.py
```
## Usage
### Step1: Extract the second field from a tab-separated file
By default, the tool extracts the second field (column) from a tab-separated file:
```bash
./cccut.py -f2 sample.tsv
```
Example output:
```
f1
1
6
11
16
21
```
### Step 2: Use a custom delimiter
Use the -d option to specify a different delimiter. For example, with a comma-separated file:
```bash
./cccut.py -f1 -d, fourchords.csv | head -n5
```
Example output:
```bash
Song title
"10000 Reasons (Bless the Lord)"
"20 Good Reasons"
"Adore You"
"Africa"
```
If no delimiter is provided, the default is a tab (\t).
### Step 3: Select multiple fields
Use the -f option to specify a list of fields to be printed. You can provide a comma or whitespace-separated list of fields:
```bash
./cccut.py -f1,2 sample.tsv
```
Example output:
```bash
f0      f1
0       1
5       6
10      11
15      16
20      21
```
### Step 4: Read from standard input
You can provide - or omit the filename to read from the standard input:
```bash
tail -n5 fourchords.csv | ./cccut.py -d, -f"1 2"
```
Example output:
```bash
"Young Volcanoes",Fall Out Boy
"You Found Me",The Fray
"You'll Think Of Me",Keith Urban
"You're Not Sorry",Taylor Swift
"Zombie",The Cranberries
```
### Step 5: Combine with other Unix commands
The tool can be combined with other Unix commands to create a data pipeline. For example, to count the number of unique artists in a dataset:
```bash
./cccut.py -f2 -d, fourchords.csv | uniq | wc -l
```
## Examples
1. Extract the first and second fields from a comma-separated file:
```bash
./cccut.py -f1,2 -d, file.csv
```
2. Read from standard input and extract fields:
```bash
cat file.tsv | ./cccut.py -f1,2
```
3. Use with pipes to process the output further:
```bash
./cccut.py -f2 -d, file.csv | sort | uniq | wc -l
```

## Contribution
Feel free to open an issue or submit a pull request to improve the tool.

## Inspiration
This project was inspired by a coding challenge by [John Crickett](https://x.com/johncrickett). Follow him on Twitter for more coding challenges and inspiration.