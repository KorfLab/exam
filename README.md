The KorfLab Bioinformatics Exam
===============================

The Korf Lab performs bioinformatics experiments in a Linux command-line
environment. In order for you to contribute to our scientific mission, you must
have some experience in the following technologies:

+ Linux - we do everything in Linux/Unix
+ GitHub - where all of our code is maintained
+ Markdown - how documents are formatted
+ Conda - how external software gets installed (usually)
+ Python - the default programming language, but not the only one
+ FASTA, FASTQ - standard sequence formats
+ GFF, BED, SAM - standard annotation and alignment formats
+ TSV, CSV, JSON, YAML - standard interchange formats

This exam is designed to assess your current knowledge and skills. If you find
yourself pulling answers from the Internet instead of your brain, you need more
practice. Practice means repetition. Repetition means doing things over and
over until they become automatic (like every other skill in life).

After passing the exam, you will be listed in the `DEVELOPERS.md` document and
receive an official "KorfLab Bioinformatics Developer Certificate".

Assumptions
-----------

This exam assumes that you have a computer connected to the Internet with a
Linux CLI and have some experience with `git`, `python3`, and `conda`. For
training in Linux, GitHub, and Python, you are encouraged to study the latest
MCB185 repository and scour the Internet.

Rules
-----

Even though it's a good idea to collaborate with others any time you perform
experiments or write code, this exam is meant to assess your personal skills
and knowledge. Here are the rules of this game.

+ You may not get help from anyone
+ You may not import any modules that require installation
+ You may look things up on the internet, but not copy-paste anything
+ You may not use AI to do your coding or assit it
+ You may download files, but not source code


Part 1: Setup
-------------

Create a GitHub repository called `korflab_exam` and invite `iankorf` as a
collaborator.


Part 2: Data Files
------------------

This task is designed to test your ability to work with text files of genomic
data using typical Linux CLI tools like `grep` and `sort`.

Clone this repo `https://github.com/iankorf/E.coli` to get some data files for
the tasks ahead.

1. According to the `*.faa` file, how many proteins does it encode?
2. According to the `*.gbff` file, how many coding sequences are there?
3. Reconcile the differences between the previous 2 questions.
4. How many `tRNA` features are found in the `*.gff` file?
5. How many of each type of features are there in the `*.gff` file?

Provide your answers in a document in your repo. Include the command lines and
their outputs.


Part 3: Bioinformatics Programs
-------------------------------

This task is designed to test your ability to install and run a program that
may be unfamiliar to you.

For this task, your goal is to find the proteins in the E. coli proteome that
are similar to E. coli protein NP_414608.1.

Using `conda`, install `blast-legacy` from the `bioconda` channel. Then format
the blast database with `formatdb` and search it with `blastall -p blastp`. To
get the similar proteins, set the E-value to 1e-5. You may also like to use
tabular output to make it easier to get the matching protein names. Find these
options in the usage statment (of course).

Document this task in a text file that shows the command lines and the output.


Part 4: Python Programming
--------------------------

Each program below will be graded on the following criteria:

1. Beautiful - is the code simple, clear, and visually appealing?
2. Robust - does the code handle unexpected values?
3. Friendly - is the program easy to use?
4. Correct - does the program solve the problem as stated?
5. Efficient - does the program waste memory or time?

### FASTA Parser

Write a function that provides a way to read FASTA files. Put it in a module
and import it for the remaining tasks.

### Entropy Filter

This task is designed to test your ability to make a simple sliding window
algorithm that works like a standard Linux CLI program.

Write an entropy filter for DNA sequences.

Requirements:

+ Input is a FASTA file (e.g. E.coli genome)
+ Output is a FASTA file with low-entropy regions masked with Ns
+ Must support multi-FASTA files
+ There must be options and default parameters for
	+ window size (default 11)
	+ entropy threshold (default 1.4 bits)
+ There is an option for soft masking (lowercase instead of Ns)

An example output for the E. coli genome is shown below.

```
>NC_000913.3 Escherichia coli str. K-12 substr. MG1655, complete genome
AGcttttcattctGACTGCAACGGGCAATATGTCTCTGTGTggattaaaaaaagagtgTC
TGATAGCAGCTTCTGAACTGGTTACCTGCCGTGagtaaattaaaattttattgaCTTAGG
TCACtaaatactttaaCCAATATAGGCATAGCGCACAGacagataaaaattacaGAGTac
acaacatccaTGAAACGCATTAGCACCACCATtaccaccaccatcaccaTTACCACAGGT
AACggtgcgggctgACGCGTACAGgaaacacagaaaaaagccCGCACCTGACAGTGCggg
ctttttttttcgaCCAAAGGTAACGAGGTAACAACCATGCGAGTGTTGAAGTTCGGCGGT
ACATCAGTGGCAAATGCAGAACGTTTTCTGCGTGTTGCCGATATTCTGGAAAGCAATGCC
AggcaggggcaggtggCCAccgtcctctctgcccccgccaaaatcaccaaccacctGGTG
GCGATgattgaaaaaaccattaGCGGCCAGGATGCTTTACCCAATATCAGCGATGCCGAA
...
```

### K-mer Locations

This task is designed to test your ability to solve problems creatively.

Write a program that reports the locations of k-mers in a FASTA file of DNA.

+ Input is a FASTA file (just one sequence) and a value for k
+ Output is a table of k-mers and their **positions** in the sequence
+ There is an option to count both strands (use negative coordinates)

Given a FASTA file like this:

```
>seq
AAAAACGT
```

The k-mer locations for k=3 are the following (using 1-based coordinates)

```
AAA 1 2 3
AAC 4
ACG 5
CGT 6
```

### Kozak Concensus

This task is designed to test your ability to parse complex text data into a
tidy data structure.

Write a program that creates a PWM of the Kozak concensus for the E. coli
genome.

+ The input file is `*.gbff` format
+ The output format is JSON

### Overlapping Features

This task is designed to test your ability to write an algorithm that balances
speed, memory usage, and complexity.

Write a program that reports features in file1 that overlap features in file2.

+ Input files may be GFF or BED
+ Output format is up to you


Part 5: Meet with Ian
---------------------

Schedule an appointment to meet with Ian to determine if you passed and what
level of pass you achieved. You don't need to perform every task perfectly in
order to pass the exam. You may take the exam more than once to turn a fail
into a pass or to increase the level of pass.

+ Bronze - you passed, but there are a few problems
+ Silver - you passed, but there are some things that could be done better
+ Gold - you passed, and everything is very good
