# Markdown Starter Kit

## <a name="markdown"></a>Markdown

The [canonical guide](http://daringfireball.net/projects/markdown/), John Gruber's original documentation. 

Since we are System Administrators, we dabble in code and interact with GitHub. Therefore,mit stands to reason that we use [GitHub-flavored Markdown](https://help.github.com/articles/github-flavored-markdown/). That, and the functions it adds are pretty dope.


### Headers

```markdown
# This is an H1
## This is an H2
##### This is an H5
```


### Prose

Write things. Make two carrage returns for a new paragraph. 

Need a linebreak?  
Add two spaces after the first line. 


### Style

*Emphasis:*

	*Emphasis*

**Strong/Bold:**

	**Strong**

***Strong Emphasis:***

	***Strong Emphasis***

Strikethrough:

	~~Strikethrough~~


### Blockquotes

Give them some greater-than signs:

```markdown
> The quick brown fox
> jumped over the lazy
> dog.
```


Quote in a quote? Double-up on the greater-thans:

```markdown
> The quick brown fox
> jumped over the lazy
> dog.
>
>> The dog had earlier
>> claimed the fox could
>> never pull off such
>> a stunt.
>
> The dog was wrong. 
```


### Code

Wrap your line of code in back ticks:

	`/path/to/file.txt`

That's great for inline elements like paths or command names. Stylistically, if you are dealing with code snipets or commands, make them their own paragraph and indent with a tab:

	Install Homebrew:
	
		ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	
	Now go kick ass!


### Code Blocks

There are a couple of ways to create Code Blocks. 

You can use tabs as in the example above. 

You can wrap your code block in three backticks at the top and bottom:

```markdown
	```
	#!bin/bash
	
	cd path/to/directory/
	
	touch kill.sh
	
	chmod 755 kill.sh
	
	exit
	```
```

Any decent Markdown parser will add code highlighting. Just declare the language after the first set of backticks, no space in between. 

```markdown
	```bash
	cd path/to/directory/; touch kill.sh; chmod 755 kill.sh
	```
```


### Links

There are two styles of links: inline and reference. Inline-style are easy to write but leave a bunch of garbage in your prose. Reference-style improve readability but add steps to the writing process and require context changes while writing. 

**Inline:**

```markdown
[Daring Fireball](http://www.daringfireball.net)
```

**Reference:**

```markdown
[Daring Fireball][df]

[df]: (http://www.daringfireball.net)
```


### Unordered Lists

```markdown
* Red
* Blue
* Green
```

Or:

```markdown
+ Red
+ Blue
+ Green
```

Or:

```markdown
- Red
- Blue
- Green
```

Nested unordered lists just require a tab. 

```markdown
- Red
	- Purple
- Blue
	- Green
```


### Ordered Lists

```markdown
1. Red
2. Blue
3. Green
```

Nested Ordered List:

```markdown
1.1 Purple
1.2 Yellow
1.3 Orange
```


### Tables

Pipes and dashes. Place pipes to represent column seperators. Use hyphens to seperate the header from data. you can also place colons in the header seperator to define alignment for the column. Place a colon on the right for right-aligned, left for left-aligned and one on each side for center-aligned. 

```markdown
| Right | Center | Left |
|:---|:---:|---:|
| Name | phone | email |
```

Note: unless you are picky about how your source document looks, you do not need to match up pipes, as you see in the example above. As long as you have the pipe count right, you are golden. If you are crazy and have to have everything "just so" (like me), there are scripts to work that out. 


### Horizontal Rules

Add horizontal rule tags (\<hr />)  with three or more astricks. You can add spaces if you like the pretty. 

```markdown
***

*****
```




## Tools

[Markdown Service Tools](http://brettterpstra.com/projects/markdown-service-tools/)
[Quicker Markdown Linking with TextExpander](http://www.leancrew.com/all-this/2014/07/quicker-markdown-linking-with-textexpander/)

## Links

### Linking to Headers in a document 

Attention: As of October 2014, this solution does not work in `mdwiki`. 

Links to headers in a document can be done using the `name` tag. 

#### Create the name tag in the header

```markdown
## <a name="anchor"></a>Header
```

#### Create the link in your text
In this example, the [Markdown link](#markdown) will return you to the Markdown header at the top of this document. 

```markdown
[Header link](#anchor)
```