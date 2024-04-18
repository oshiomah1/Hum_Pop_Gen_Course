
# Basic Unix Commands Tutorial

Welcome to the introductory Unix commands tutorial! This guide will cover some fundamental commands that are essential for navigating and manipulating files in a Unix-like environment.

## Navigating the Filesystem
First we must ssh into the tadpole HPCC. Do you remember how? Tip: Make sure you save your password somewhere i

```bash
ssh username@tadpole.genomecenter.ucdavis.edu
```

### `pwd`
Print the working directory. This command shows you where you currently are in the file system.

```bash
pwd
```
What do you see? 

### `cd`
Change directory. This command allows you to move between directories.

```bash
cd /path/to/directory
```
We want to navigate to the course page. Do you remember it? It's pasted below; just like your password you should always rememmber how to navigate to your course page

```bash
cd /share/ant157/
```
Now let's say I want to go back up a directory. I can run;

```bash
cd ..
```
Here `..` means go one level up

Let's navigate back to the course page. Run:

```bash
cd /share/ant157/
```

We are back to the course page. If we wanted to go two levels up we could run

```bash
cd ../..
```
Run the command above. We can see that we just separate the `..` by a `/`. 

## Question 1: How can I go three levels up? I want you to travel 3 levels up now!

```bash
Answer:
```

### Now lets go back to the course page. Use the `cd' command to navigate to the course directory `cd /share/ant157/`

### `ls`
List directory contents. This command shows you the files and directories in your current directory.

```bash
ls
```
## Question 2: What do you see when you run the `ls` command in the course directory?

```bash
Answer:
```
## Now you must navigate into your personal student directory. Remember that last week we all created a folder named after ourselves in the `students` folder. Let's navigate there!

## Question 3a: What line of code do you need to navigate into your student directory from the course page?

```bash
Answer:
```

Now run ` cd ~ ` on your terminal to navigate to the root directory. From the root directory you must navigate back to your student directory again.

## Question 3b: What line of code do you need to navigate into your student directory from the root directory? (It must be just one line of code !")

```bash
Answer: 
```
### Now that we've had some fun with directory navigation, let's do some file manipulation.

If you aren't already in your personal student folder, navigate there.

## Manipulating Files and Directories

### `mkdir`
Make directories. This command allows you to create new directories.

```bash
mkdir new_directory
```
If you wanted to make multiple directories at once you can run  ```mkdir new_directory1 new_directory2```

## Question 4: What line of code do you need to make 3 directories, one called `orange`, one called `grape`, one called `apple` ? (It must be just one line of code !)

```bash
Answer: 
```
## Question 5: How can you check if you created these fruity folders?

```bash
Answer:

```
in your word document also attach screenshot of your command line after you run your command

### `touch`
This commmand creates a new empty file. 

```bash
touch new_file
```
Navigate to the `orange` directory and then run `touch orange_file_1.txt`. Ensure to use `ls` to check that this worked. Now navigate one level up (This should take you back to your personal student directory) 

## Question 6: How can you navigate one level up?

```bash
Answer: 
```
Now from this folder we can create another file in the orange directory. In your command line please run `touch orange/orange_file_2.txt`. What do you notice here? 
instead of navigating into the orange folder and then creating a new file, we could
How do we know if it worked? One way is to run `cd orange` and then run `ls` . Alternatively we can use one line and run `ls orange`

## Navigate back one level up your personal student directory if you aren't there already. Now let's create a new file called pear_file.txt. Please run `touch pear/pear_file.txt`

What happens when you do that?

## Question 7: Please paste the error message below

```bash
error message:  
```
### if we truly want to create a pear_file.txt in the pear folder. We first have to create the pear folder! There are two ways we could do this. 
#### Option A `mkdir -p pear/pear_file.txt` 
#### Option B  run `mkdir pear` then `cd pear` then `touch pear_file.txt`


## Question 8: In 3 or more sentences, compare and contrast options A and B shown above. You will have to research what the `-p` flag is doing when used with -mkdir
#### You can use this link to help you https://www.geeksforgeeks.org/mkdir-command-in-linux-with-examples/

```bash
Answer:  
```

### `nano`
This command opens the nano text editor. It can be used to create and edit files. Navigate to the `grape` directory you created earlier. 
Run 

```bash
nano grape_file_1.txt
```
What do you see? I want you to type `grapes are yummy!`. To exit nano press CTRL + X on your keyboard. Then your screen will say `Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?` type Y (meaning Yes). Then you'll see `File Name to Write: grape_file_1.txt` then tap Enter/return on your keyboard

### `less` `more` `cat`

These are all different ways of viewing files. An example usage is `less filename.txt`
## Question 9a:  use `less`, `more` and  `cat` separately to view `grape_file_1.txt`. What do you see? Do you notice a difference? If your screen lags or freezes type `Q` on your keyboard to escape

```bash
Answer:
```
## Question 9b:  I want you to research the differences between `less`, `more` and `cat` and in a few sentences describe your findings

```bash
Answer:
```

### `head` and `tail`
You can use head `head` and `tail` to view the first 10 lines and last 10 lines of files respectively. An example usage is `tail filename.txt`

#### Now lets create a new text file called `numbers.txt` . Use nano to create this file.

Copy and paste the following text in numbers.txt 
```
one
two
three
four
five
six
seven
eight
nine
ten
```
## Question 10a:  Do you notice a difference between using `head` and `tail` on `numbers.txt`
```bash
Answer:
```

## Now use nano to edit numbers.txt by adding "eleven" and "twelve" to the bottom of the text file

## Question 10b:  Now do you notice a difference between using  `head` and  `tail` on `numbers.txt` ? what's the difference?

```bash
Answer: 
```

### `cp`

We can use cp to copy. One usage of this would be to make a duplicate of `numbers.txt` called `backup_numbers.txt`

```bash
cp numbers.txt backup_numbers.txt

```
We can also use:  


```bash
cp /share/ant157/students/yourname/grape/numbers.txt /share/ant157/students/yourname/grape/backup_numbers.txt
```
Note: You can't just copy-paste the line below into your terminal; what do you have to change?
or

```bash
cp numbers.txt /share/ant157/students/yourname/grape/backup_numbers.txt
```

or

```bash
cp /share/ant157/students/yourname/grape/numbers.txt backup_numbers.txt
```

since we are already in the the grape folder you don't need to write the "full" (`absolute`) path and can just use the file name (`relative path`) instead. A generalization of this syntax is

```bash
cp /path/to/source/file /path/to/destination/file
```

If you are already in the directory where you want the file to copied to, and you're copyin a file from a different directory you can replace `/path/to/destination/file` with a `.` . A `.` means current path

```bash
cp /path/to/source/file .
```

### In addition, we can also use `cp` to copy numbers.txt from the grape directory into the orange directory. Remember the syntax is : 

```bash
cp /path/to/source/file /path/to/destination/file
```

## Question 11a. What is the code you would use to copy numbers.txt from the grapes folder to the orange folder? Assume your current directory is the grapes folder

```bash

```

## Question 11b. What is another way you could copy numbers.txt from the grapes folder to the orange folder? Assume your current directory is the orange folder.
### Hint: You can use a `.`

```bash

```

### `mv`

#### We can use `mv` to move or rename files. I want you to read this https://www.geeksforgeeks.org/mv-command-linux-examples/ 
#### Then navigate to the `apple` directory
#### Use `touch` to create a file called `apple_types.txt`
#### Then use `mv` to rename `apple_types.txt` to `apple_breeds.txt`

### `rm`
This command is used to delete files or directories. Be very careful! Once you delete a file in the command line it is gone FOREVER. Don't be afraid in this situation though, we aren't working with super important files

```bash
rm file_to_remove
```
navigate to the grape folder and practice using rm on all the files in this folder. then run `cd ..` to go up a folder and use `rm` to remove the orange folder. What happens? we can't use `rm` on a folder we have to use the syntax below:

```bash
rm -r directory_to_remove
```
### Now remove all the fruity directories. I would advice you to go back to the top of the page and repeat this tutorial at least one more time


## Final task 
#### I want you to tie all the knowledge you learnt today. Navigate to your personal student directory and create 2 folders called `Cancer` and `Favorite_Things`. Replicate the file structure of the images below, using nano to create the `.txt` files. Each .txt file will be a list of 3-5 that you curate yourself or use the internet. Ask Oshiomah to clarify if you have questions. Now have fun!


![Description or title of image 1](pic1.png)



![Description or title of image 2](pic2.png)






```