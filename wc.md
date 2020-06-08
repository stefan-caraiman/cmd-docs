# wc

**Word Count**, count lines, words or letters in a file.

# Basic Usage

## count the lines in a file

`wc -l lines.txt`

or to show only the number of lines you can run:

`cat lines.txt | wc -l`

## count the words in a file

`wc -w words.txt`

## count the characters in a file

`wc -m file.txt`


## To count files and directories showed by `ls`:

`ls -l | wc -l`


# Interview questions:

**Question:** How do you count how many lines a file has in Linux?

**Answer:** You run the command `wc -l` and give it a file to count the number of lines.
