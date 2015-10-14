# TopicModeling_Mallet


#Not Enough Memory

Depending on how large your files are, you might get an error that says you do not have enough memory. 
To address this issue, you can do one of the following:

1. Outside of the Terminal

Go to the folder ~/Downloads/mallet-2.0.7/bin/

Drag the "mallet" file into into a text editor. I recommend Sublime.
(If is it a PC, you will use mallet.bat)

Now, we can change our memory. The default is:

MEMORY=1g  

What you change the number to depends on your machine. One recommendation is 
to set it to 1g fewer than ram/memory on your machine. You can check your memory
by going to the Apple on the top left of your computer and choosing "About This Mac."
Look at "Memory."  In my case, my machine has 8GB. I will change to MEMORY=7g.

2. Inside the Terminal

Go to the directory mallet2.0.7/bin/

Type 
```
pico mallet
```
Go to MEMORY=1g and change the number according to your machine. 

What you change the number to depends on your machine. One recommendation is 
to set it to 1g fewer than ram/memory on your machine. You can check your memory
by going to the Apple on the top left of your computer and choosing "About This Mac."
Look at "Memory."  In my case, my machine has 8GB. I will change to MEMORY=7g.

One you are done, type Ctrl X. Type "Y" to save. 
Control X to save and exit.


# Adjust Stopwords 

Mallet has a default stop list it uses. In many cases though, we want to 
adjust the stop list according to our needs. For example, if I'm working with American
Quarterly, I might want to stoplist "American" and "Quarterly."

The stopword lists are available in: mallet-2.0.7/stoplists/
You can override the default list on Mallet using one of these lists 
or a custom list of your choosing.  How do we do this?

In our tutorial on google docs, we are using the following code for our data:

```
bin/mallet import-dir --input AQ/ --output texts.mallet 
--token-regex '\p{L}[\p{L}\p{P}]*\p{L}' --keep-sequence --remove-stopwords
```

We need to replace

```
--remove-stopwords
```
with

```
--stoplist-file stoplists/NAMEOFFILE.txt

````

so not it is

```
bin/mallet import-dir --input AQ/ --output texts.mallet 
--token-regex '\p{L}[\p{L}\p{P}]*\p{L}' --keep-sequence --stoplist-file stoplists/NAMEOFFILE.txt
```

Let's look at an example.

In my case, I want to use the english stopword list 
in mallet-2.0.7/stoplists/en.txt.  You can go into the Mallet folder on
your computer and see it. Accoringly, when I go to run process the text, I will use:

```
--stoplist-file stoplists/en.txt
```

The code I run in my terminal will be:

```
bin/mallet import-dir --input AQ/ --output texts.mallet 
--token-regex '\p{L}[\p{L}\p{P}]*\p{L}' --keep-sequence --stoplist-file stoplists/en.txt
```

Let's say I name it laurencustomstoplist.txt. Then I will use:

```
--stoplist-file stoplists/laurencustomstoplist.txt
```

```
bin/mallet import-dir --input AQ/ --output texts.mallet 
--token-regex '\p{L}[\p{L}\p{P}]*\p{L}' --keep-sequence --stoplist-file stoplists/laurencustomstoplist.txt
```
