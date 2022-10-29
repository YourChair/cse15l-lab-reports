Hello future student!

This post will contain information on the grep command (Linux).


The three command-line options I chose have the following behaivior:


-c, --count
              Suppress normal output; instead print a count of matching
              lines for each input file.  With the -v, --invert-match
              option (see below), count non-matching lines.


-v, --invert-match
              Invert the sense of matching, to select non-matching
              lines.


-i, --ignore-case
              Ignore case distinctions in patterns and input data, so
              that characters that differ only in case match each other.



Here is this output for the man grep command:

![The output for man grep](./man%20grep.png)



And here is (part of) a normal output for the command:

![Normal grep command](./grep%20normal.png)

![Normal grep output](./grep%20normal%20output.png)


Here, the -c command is being used to instad output the number of lines that contain the letter e: very useful to avoid flooding your screen with output which still getting an idea for how much the inpiut appears.

![Grep with -c](./grep%20-c.png)



Once again, here is a grep command counting lines that contain this term. 173 lines would take up a lot of space in the console, and with especially large inputs, data may be lost off the top of the console when the line limit is reached. -c prevents this.

![-c chapter 1](./grep%20-c%20output%20chapter%201.png)


-c is great for when you don't care how the search term is being used, since it prints a much abbreviated output at the cost of losing the context for how the term appears. Here, a search for "air" highlights words like "midair", "airline", and "fairly". With out the -c, you can see the context behind each line's inclusion in the output, but with the -c, each match is reduced to a simple integer.

![chapter 5 normal output](./grep%20normal%20output%20chapter%205.png)
![chapter 5 output with -c](./grep%20-c%20output%20chapter%205.png)


-c is redundant for extremely short outputs, since these are already a few lines and the space saving is no longer worth the loss from abbreviation.

![chapter 10 normal and -c output](./grep%20normal%20and%20-c%20output%20chapter%2010.png)




This is the -v command, which "inverts" the result. If used alone, it will print all lines that do NOT contain the search term.

This is the output of searching a file using a relatively common (but not ubiquitous) search term (the letter p). All lines that did not contain the letter p were outputted (I did not include them all for brevity). Note that capital P (such as in "President") does not count, because grep is case-sensitive and the term was "p". This could be pretty useful if you were trying to find lines that didn't contain a character for some reason -- but I'm not sure why you'd need that.

![-v output chapter 10](./grep%20-v%20p%20output%20chapter%2010%201.png)
![-v output chapter 10](./grep%20-v%20p%20output%20chapter%2010%202.png)
![-v output chapter 10](./grep%20-v%20p%20output%20chapter%2010%203.png)



Here is a search with an extremely common search term (the letter e). Note that there are virtually no lines of text, only wall of newlines (most of which I have cut out). This is because the original document contained many newlines (not because -v is deleting lines that contained the term and leaving a newline in their stead) -- and newlines do not contain e. I could see a use for this as a newline/header finder - use a common search term so that all instances of actual text are removed, leaving only line feeds.

![-v output](./grep%20-v%20e%20output.png)
![-v output](./grep%20-v%20e%20output%202.png)
![-v output](./grep%20-v%20e%20output%203.png)
![-v output](./grep%20-v%20e%20output%204.png)
![-v output](./grep%20-v%20e%20output%205.png)


Here's another long output created by searching for lines not containing "th" (case-sensitive). Note that there are many "Th"s that are still there. I'm not sure why you'd need this function for this type of input, even. The output seems useless. (Even more useless is searching for a nonexistent term, like "qwerty", which will just print the entire file.)
![-v output chapter 1](./grep%20-v%20th%20chapter%201%201.png)
![-v output chapter 1](./grep%20-v%20th%20chapter%201%202.png)
![-v output chapter 1](./grep%20-v%20th%20chapter%201%203.png)
![-v output chapter 1](./grep%20-v%20th%20chapter%201%204.png)
![-v output chapter 1](./grep%20-v%20th%20chapter%201%205.png)
![-v output chapter 1](./grep%20-v%20th%20chapter%201%206.png)


This is the last function, -i, which removes case-sensitivity. A search for "iraq" found nothing without -i, but had result with -i.
![-i output](./grep%20-i%20iraq%20chapter%2010.png)


Since Bush and bush are both things you might see in a file, this search is able to find both (while the first searched only for lowercase bush and found nothing). This could certainly have its uses, but could also be a bad thing (what if we are talking about White House hedges for a gardening paper). However, it could be useful for when a word is in all caps or the like for emphasis.
![-i output](./grep%20-i%20%20bush%20chapter%2010.png)

A search for the same thing, except with a capital letter in the middle (to show the output is the same). This function could have been really useful with -v up above to exclude "Th" or "P" or "E" from the list as well (for a true newline finder, for example).
![-i output](./grep%20-i%20buSh%20chapter%2010.png)


And lastly, here is a combo output. -v and -c print out the number of lines that do NOT contain the search term. -i does its own thing (but it could be a game-changer for words that are both proper nouns and normal nouns (like the word bush), or for removing capitalized words at the start of sentences)


![combo output](./grep%20-c%20-v%20-i%20buSh%20chapter%2010.png)












Hope this helped!



