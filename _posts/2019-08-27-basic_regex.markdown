---
layout: post
title:      "Basic RegEx "
date:       2019-08-28 01:51:06 +0000
permalink:  basic_regex
---

This blog will display the general rules of RegEx. 
There are some notations may different among different progamming languages. please refer to that particular languages for the details.
## Why I would like to write about this topic?
I have seen so many applications/shell commands that need to use RegEx to produce the needed information. However, I know that I still can use other way to get the needed infomration. In bottom of my mind, sooner or later, if I would like to have clean codes in some area, (for example, validate the email address, phone number, IP address... etc.) RegEx would be a better choices to make the code lean and clean. 
The last section (Bonus section) of my first week curriculum is RegEx. This is a good oppertunity for me to dive deep into this topic, and make myself be familiar with it. I know I will be benifit from it in the near future.
I also like to use this blog to track how I learn this, what the issues that I encountered, and etc...
## What is RegEx? What is pos and con to use RegEx?
RegEx stands for "Regular Expression". 
## How to form a pattern? (any good practice that can be followed?)
* Match Literal String
  1. exact match => this is limitted to only one pattern
   Search a word in a string, paragraph, aritical, etc... this is the basic idea behind RegEx. 
   Explicitly to spell out the searched key word surrounded by //. 
	 Note: the case of searched key impack the search result. 
	 
  2. with Different Possibilities => this can be used to search for multiple patterns using the alternation or OR orperator : |
  3. Ignore the serached keyword case by using flag - i flag 
      Note: the flag(s) is appended //
			note: you can append multiple flags after //. For example /search_key_word/ig
  4. wild card 
      - . (dot or period) => use this wild card to match all the characters
  5. Match single character with multiple possibilities by using **character classes**  => this allow you to define a group of characters you wish to match by placing them inside square brackes ([])
      Note: inside the character classes, you can use hyphen (-) to define a range of characters to match, and includes both ends
6. Match single characters not speicifed by using **negated character sets** => place (^) after the opening square bracket and before the characters you do not want to match
7. Match characters that occur one or more times  => use + to check it

* flag:
   - i : ignore the case of the searched keyword
   - g : for global search meaning it will match all occurrences in the RegEx
## Is the same pattern can be used by all programming languages to generate the same results?



RegEx cheat sheet => please follow the following link:
![](https://www.rexegg.com/regex-quickstart.htmlhttp://)
