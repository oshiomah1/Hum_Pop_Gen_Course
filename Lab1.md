---
output:
  html_document: default
  pdf_document: default
editor_options: 
  markdown: 
    wrap: 72
---

## ANT157L Problem Set 1: Allelic and genotypic frequencies with application to SNP array data

Name:

```         
Write your name here
```

**Due Date: Friday, October 13th \@ 5pm**

### Goals:

At the end of this exercise, you should be able to: - Record allele
frequencies from dbSNP and plink - Understand how SNP array data are
formatted - Perform simple Bash command line executions - Identifying
missing genotypes / individuals with high missing data - Use
Hardy-Weinberg to remove problematic genotypes from a SNP array dataset

## Task 1. Manipulate SNP array data using PLINK

PLINK is a piece of software that allows users to perform various data
manipulation and analyses on genome-wide SNP data. Today we are going to
focus on the former.

A very useful online manual is available for PLINK here:
<http://zzz.bwh.harvard.edu/plink/dataman.shtml> and/or
<https://www.cog-genomics.org/plink/1.9/general_usage>

#### Log on to the Genome Center cluster.

```         
ssh yourUserName@tadpole.genomecenter.ucdavis.edu
```

Then navigate to our ant157 folder and into your `/students/yourname`
directory

You will be using PLINK software. In order to use this, you need to load
the software module:

```         
module load plink/1.90p
```

The command module load will load different types of software installed
on the Genome Center cluster. You need to do this when starting each
session.

### Question 1 [3 pts]

Use `head` to explore the first line of the `Ethiopians_chr1.fam` file
and the `Ethiopians_chr1.bim` file in the
`/share/ant157/data/Ethiopians/` directory.

What is the population and individual ID of the first individual in the
Ethiopians_chr1.fam file?

```         
(Type your answer here)
```

What is the physical position of the fifth SNP in the .bim file?

```         
(Type your answer here)
```

PLINK files can get very large, containing genotype information for
hundreds of thousands of individuals at millions of SNPs, so we do not
want to have to use `less` to view and manipulate the data. Instead we can
use PLINK to read the file and tell us something about the structure of
our data like so:

```         
plink --bfile /share/ant157/data/Ethiopians/Ethiopians_chr1 --freq
```

The `--bfile` argument informs PLINK what dataset to look for, in this
case the path to `Ethiopians_chr1` (it will automatically look for `.bed`, `.bim`
and `.fam` endings of the dataset in that folder). Running this command will print a
summary of the contents of the input dataset to screen. It also prints a
summary of the output dataset if any manipulations are performed (in
this case, we used the `--freq` flag to calculate allele frequencies).
But ALWAYS make sure you are only working in your own directory, and NOT
the data directory.

You can either copy the datafile to your own folder or continue to
simply call the dataset from the /data/ folder.

### Question 2 [1 pt]

Write down the command to copy the data files to your own folder.

```         
(Type your answer here)
```

### Question 3.1 [3 pt]

After running the PLINK command above in Q1, look at the plink.log file.
How many SNPs, males and females are in the `Ethiopians_chr1` dataset?

```         
(Type your answer here)
```

### Question 3.2 [3 pt]

I want us to update the binary file for missing sex information

Identify the individuals who are missing sex information. [**Hint**:
look at the files in your directory] 


Do you remember what binary file to look at?

```         
(Type your answer here)
```
what column is sex in this file (and all files like this?)

```         
(Type your answer here)
```

We can use the following commands

```         
awk '$5 == 0' Ethiopians_chr1.fam

```


Use plink to update the
`.fam`file and replace the missing sex with "2". List your commands and
explain.

The format to do this will be: 

plink --bfile original_dataset --update-sex sex_update.txt --make-bed --out updated_dataset

you have to replace original dataset with the actual file name and updated_dataset with the file you want to name the new file


you also have to create the sex_update.txt

sex_update.txt will be a 3-column file of the format <family ID> <individual ID>  <new sex>

To create this first select the two columns 

```         
awk '$5 == 0 {print $1, $2}' Ethiopians_chr1.fam > missing_sex.txt
```

Next, from mising_sex.txt we will add a 2 to the third column. 

What does 2 mean?

 ```         
(Type your answer here)
```

Now lets run this
```         
awk '{print $1, $2, 2}' missing_sex.txt > sex_update.txt
```

okay how can we now finally update sex

 ```         
(Type your answer here)
```
