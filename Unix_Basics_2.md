
# Data Wrangling in Unix

This tutorial will help you master essential Unix commands for data wrangling. We will focus on `grep`, `awk`, and using pipes to manipulate data effectively. 

## Exercise 0: Getting Started and Review of Unix Basics 1

First you must make a directory called `Unix_Basics_2` using `mkdir`. Next, ensure you have the plink binary Ethiopian files in your `Unix_Basics_2`.  These files are located
in the `/share/ant157/unix_test_data` folder. Please use the `cp` command to copy the `.fam` `.bim` and `.bed` files into your folder. 

### Question 1: How would you copy these files into your folder?
```bash
Type answer here
```

### Wildcards

Instead of copying these files one by one you can also use a wildcard, `*`, to copy files. Run `cp /share/ant157/unix_test_data/Ethiopians* .`. What do you notice? 

### Question 2: What do you notice in your folder when you use a wildcard to copy the files? 
```bash
Type answer here
```

## Exercise 1: Using `grep` to Filter Data

**Objective:** Extract all lines containing the allele "G" from `Ethiopians_chr1.bim`.

```bash
grep 'G' Ethiopians_chr1.bim
```

This command searches for the letter "G" and prints lines where it appears.

## Exercise 2: Introduction to `awk`

**Objective:** Use `awk` to print the RSID and alleles from `Ethiopians_chr1.bim`.

```bash
awk '{print $2, $5, $6}' Ethiopians_chr1.bim
```

This command uses `awk` to select the second (RSID), fifth (allele 1), and sixth (allele 2) fields.

## Exercise 3: Combining `grep` and `awk` with Pipes

**Objective:** Find all lines with the allele "A" and print their RSID and position.

```bash
grep 'A' Ethiopians_chr1.bim | awk '{print $2, $4}'
```

This combines `grep` to filter and `awk` to display specific columns.

## Exercise 4: Using `awk` for Complex Data Extraction

**Objective:** List individuals from the `Ethiopians_chr1.fam` file with a phenotype value of -9.

```bash
awk '$5 == -9 {print $1, $2}' Ethiopians_chr1.fam
```

This uses `awk` to check the fifth field for -9 and prints the first two fields (family and individual IDs).

## Exercise 5: Writing Results to a File

**Objective:** Extract and save all individuals with a phenotype value of 2 to a new file.

```bash
awk '$5 == 2 {print $0}' Ethiopians_chr1.fam > phenotype_2.fam
```

This command filters and redirects the output to `phenotype_2.fam`.

Remember to experiment with variations of these commands to deepen your understanding of Unix data wrangling tools.
```
