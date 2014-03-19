---
layout: post
author: laura
title: Pipes Assignment
date: 2014-03-19
---

Here are the pipes and filters exercises.

##1. Explain why -n has this effect.
sort - treates as strings
sort -n treats as numbers


##2. What is the difference between:  wc -l < mydata.dat and wc -l mydata.dat
I did this on our 'lengths' file. 

```
wc < lengths
7  14 110   #the output, and we don't see 'lengths'

```


```
wc lengths
7  14 110 lengths  #the output

```

The top case is reading the data from the file itself, not from the standard output. 
	||
	\/
The first case is getting the data from the file itself and thus does not need to refer to itself (lengths), hence it only gives the contents. But the second case is a command upon the shell to get information about the file, hence the output is written on the screen with the full data: the number of wc plus the file name it did the command on.

Question: wc < cubane.pdb, what would happen if we worte this as wc > cubane.pdb? Would it overwrite the data or just input the word count into a new line?
Ok I did it but didn't see any difference. Did it do something?
Answer - overwrote data, now there is nothing nothing nothing in my cubane.pdb file! :(


##3. Why do you think uniq only removes adjacent duplicated lines? (Hint: think about very large data sets.) What other command could you combine with it in a pipe to remove all duplicated lines? 

Because it is looking at words next to each other, not as a whole, at the same time. In order to get rid of the duplicates, we can sort the list first, that way they are next to each other, then do the uniq command. 

To make this work, we would need to use the sort command, pipe, then uniq


##4. What text passes through each of the pipes and the final redirect in the pipeline below?

Used the ethane.pdb:

```
cat ethane.pdb | head -5 | tail -3 | sort -r > final.txt

```

The last 3 lines of ethane.pdb are listed in reverse order, listing from the top-down.


##5. What other command(s) could be added to this in a pipeline to find out what animals the file contains (without any duplicates in their names)?

```
$ cut -d , -f 2 animals.txt

```

We need the sort | uniq | find

```
cut -d , -f 2 animals.txt | sort | uniq

```
