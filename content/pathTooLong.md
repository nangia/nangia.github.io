--- 
title: 'Deleting Windows 7 directory containing files with too long path names'
date: '2013-09-02 20:22:00+05:30'
lastmod: '2024-07-25T14:19:38+05:30'
slug: "deleting-windows-files-with-too-long-path-len"
summary: "A python program is described which can be used to delete a directory containing files whose names are too long on Windows 7."
categories:
    - Programming
tags:
    - python
---

Problem
-------
The laptop that my employer has provided me has a program installed for upkeep of the laptop. So it keeps auto-updating appropriate patches, newly requested software etc. to my laptop. However, I have noticed a problem with this program. This software downloads
stuff from company servers and then creates directories in c:\ with lot of contents on the hard disk and then forgets to delete them. Over a period of time, this consumes
lot of disk space (I have counted hundreds of MBs once). I moved all such directories files to one directory c:\junk and then tried to delete this directory.
But, I could not delete this directory as I got this error: "Destination Path Too Long". Looked into the directories and found that they had **really long** files names. I googled around 
and it seems that the [official solution from Microsoft](http://support.microsoft.com/kb/320081) is to rename the files to smaller names. It's strange that Microsoft allows
one to create such long named files but not easily delete them. Anyway, since they were consuming so much disk space, I decided to write this python (2.7) utility to rename files inside this directory to shorter names. Then I manually delete the directory c:\junk. 

Solution
--------

{{< highlight python >}}
from collections import deque

import os
import os.path

directoryToBeDeleted = "c:\\junk"
fqueue = deque([ directoryToBeDeleted ])

while fqueue.__len__() != 0:
	count = 0
	afile = fqueue.popleft()
	for f in os.listdir(afile):
		source = afile + "\\" + f
		target = afile + "\\" + hex(count)[2:]
		print "Renaming %s to %s" % (source, target)
		os.rename(source, target)
		count += 1
		if not os.path.isfile(target):
			fqueue.append(target)

# Now manually delete the contents of the junk directory
{{< /highlight >}}



Description
-----------

All this program does is a basic [Breadth First Search](http://en.wikipedia.org/wiki/Breadth-first_search). *fqueue* in this program is a double ended queue. Initially, at the start of the loop, the queue has just the original directory that we want to delete. In every *while* iteration, the program takes off one file or directory name from the left of the queue and then
renames all the files and directories within this directory starting 0. To keep the numbers short, I used a hexadecimal numbering scheme. If sub-directories are found in this directory, they are added to the right of the double ended queue for the next *while* iteration.

While I found this program adequate for my needs, one could potentially rename the files using a [base 36 numbering scheme](
http://stackoverflow.com/questions/1181919/python-base-36-encoding) to make for even shorter filenames. That might be helpful in case there are large number of files
in the directories.

I left the last step of deleting the directory as manual - because, I did not want to make a mistake. This is a dangerous script. And that's the reason, I chose not to send in the directory to be deleted via command line arguments. It then becomes too easy to make a mistake. Beware!

I later heard of a program called robocopy which apparently can do this deletion easily. But, I don't have an easy way to install a new program on my employer provided laptop (has to be blessed by our IT department). So I guess, for me this is the way to go!
