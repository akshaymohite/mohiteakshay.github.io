---
layout: post
title:  "How to fix no newline at end of file warning"
date:   2017-02-10 18:28:51 +0530
categories: github
---

If you have come across **No newline at end of file** warning on Github, then this post is for you.
The warning says that file does not have a new line at the end.
This depends on how your editor handles new lines on save.
There are settings / preferences to fix this warning which will be discussed in this post.

### Warning

As shown in the image given below, the warning says "No newline at end of file"

![Alt text](https://monosnap.com/file/AHRgMF6XniEU0x7xB2Dad8rnvtnOIB.png)


### Fix

We will discuss the fix for Sublime Text and Rubymine users.

#### Sublime Text 2

##### Step 1. Open the Preferences

Hit `Command + ,` to open the preferences on Rubymine.

##### Step 2. Add configuration option

You'll need to edit the preferences of Sublime Text 2 to add the new option.
The option key and value is as follows,

![Alt text](https://monosnap.com/file/TbOQFAF4g6OmrVlOzZG8k6VidUpAIz.png)

{% highlight bash %}
"ensure_newline_at_eof_on_save": true,
{% endhighlight %}

The configuration option name is self explanatory. It will ensure new line at
the end of file on save. Thus, anytime you hit save on the file you are editing,
it will automatically add newline at the end of file.


#### Rubymine

##### 1. Open the preferences

Hit `Command + ,` to open the preferences on Rubymine.

##### 2. Search for newline

![Alt text](https://monosnap.com/file/YACbdL6M6lDn709ccnpvHKg2QTb6gd.png)

Search for "new line", you will see an option with checkbox saying,
"Ensure line feed at file end on Save".
Check this option to have newline at the end of file on save.
