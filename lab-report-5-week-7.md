Hello future student!

This post will be about vim.




For prompt 1, "Changing the name of the start parameter and its uses to base", the fastest method my group found was:
:%s/start/base/g <Enter>
followed by
:wq <Enter>
to write and quit.

:%s/start
is the command for substitute. As you are typing "/start", which searches for start, you will see the cursor moving around as the search is refined.

![:%s/start](./vim%201.png)


After this, the command is completed with /base (which means to replace with "base"). However, this command would only replace the first instance, so /g is used as well to make it a global replace.

![Replaced](./vim%202.png)

Finally, :wq is used to write and quit.




Editing directly took 44 seconds. Finding each of the terms was a bit of a hassle, even with find and replace, because I hadn't practiced using the tool before.


Vim commands took 28 seconds. There weren't any major noteworthy difficulties with this approach.





I'd prefer to use the manual method, because even though it's slower, it's more reliable, and there is no need to either look up or figure out a lengthy command that will only ever be used once or twice for a program. Additionally, it would almost certainly be faster for a single replace or a single insert, because there is less start-up time. There's no need to go to the remote server, use the vim command, do the replace, and then write and save with the normal method.

However, if there are a large number of terms to replace (or another task that is difficult to do manually), using vim to avoid the repetition would be very useful. Additionally, if there are a large number of tasks to be done all at once, vim is simply faster at that sort of stuff (especially tasks like doing copies and pastes, or replaces).







Hope this helped enough!



