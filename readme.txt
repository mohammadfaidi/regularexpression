Regular Expression in Python with Examples | Set 1

Module Regular Expressions(RE) specifies a set of strings(pattern) that matches it.
To understand the RE analogy, MetaCharacters are useful, important and will be used in functions of module re.
There are a total of 14 metacharacters and will be discussed as they follow into functions:

\   Used to drop the special meaning of character
    following it (discussed below)
[]  Represent a character class
^   Matches the beginning
$   Matches the end
.   Matches any character except newline
?   Matches zero or one occurrence.
|   Means OR (Matches with any of the characters
    separated by it.
*   Any number of occurrences (including 0 occurrences)
+   One or more occurrences
{}  Indicate number of occurrences of a preceding RE 
    to match.
()  Enclose a group of REs

    Function compile()
    Regular expressions are compiled into pattern objects, which have methods for various operations such as searching for pattern matches or performing string substitutions.
    filter_none

    edit

    play_arrow

    brightness_4
    # Module Regular Expression is imported using _import_(). 
    import re 
      
    # compile() creates regular expression character class [a-e], 
    # which is equivalent to [abcde]. 
    # class [abcde] will match with string with 'a', 'b', 'c', 'd', 'e'. 
    p = re.compile('[a-e]') 
      
    # findall() searches for the Regular Expression and return a list upon finding 
    print(p.findall("Aye, said Mr. Gibenson Stark")) 

    Output:


    ['e', 'a', 'd', 'b', 'e', 'a']

    Understanding the Output:
    First occurrence is ‘e’ in “Aye” and not ‘A’, as it being Case Sensitive.
    Next Occurrence is ‘a’ in “said”, then ‘d’ in “said”, followed by ‘b’ and ‘e’ in “Gibenson”, the Last ‘a’ matches with “Stark”.


    Metacharacter backslash ‘\’ has a very important role as it signals various sequences. If the backslash is to be used without its special meaning as metacharacter, use’\\’

    \d   Matches any decimal digit, this is equivalent
         to the set class [0-9].
    \D   Matches any non-digit character.
    \s   Matches any whitespace character.
    \S   Matches any non-whitespace character
    \w   Matches any alphanumeric character, this is
         equivalent to the class [a-zA-Z0-9_].
    \W   Matches any non-alphanumeric character. 

    Set class [\s,.] will match any whitespace character, ‘,’, or,’.’ .
    filter_none

    edit

    play_arrow

    brightness_4
    import re 
      
    # \d is equivalent to [0-9]. 
    p = re.compile('\d') 
    print(p.findall("I went to him at 11 A.M. on 4th July 1886")) 
      
    # \d+ will match a group on [0-9], group of one or greater size 
    p = re.compile('\d+') 
    print(p.findall("I went to him at 11 A.M. on 4th July 1886")) 

    Output:

    ['1', '1', '4', '1', '8', '8', '6']
    ['11', '4', '1886']

    filter_none

    edit

    play_arrow

    brightness_4
    import re 
      
    # \w is equivalent to [a-zA-Z0-9_]. 
    p = re.compile('\w') 
    print(p.findall("He said * in some_lang.")) 
      
    # \w+ matches to group of alphanumeric character. 
    p = re.compile('\w+') 
    print(p.findall("I went to him at 11 A.M., he said * in some_language.")) 
      
    # \W matches to non alphanumeric characters. 
    p = re.compile('\W') 
    print(p.findall("he said * in some_language.")) 

    Output:

    ['H', 'e', 's', 'a', 'i', 'd', 'i', 'n', 's', 'o', 'm', 'e', '_', 'l', 'a', 'n', 'g']
    ['I', 'went', 'to', 'him', 'at', '11', 'A', 'M', 'he', 'said', 'in', 'some_language']
    [' ', ' ', '', '', '*', ' ', ' ', '.']

    filter_none

    edit

    play_arrow

    brightness_4
    import re 
      
    # '*' replaces the no. of occurrence of a character. 
    p = re.compile('ab*') 
    print(p.findall("ababbaabbb")) 

    Output:

    ['ab', 'abb', 'a', 'abbb']

    Understanding the Output:
    Our RE is ab*, which ‘a’ accompanied by any no. of ‘b’s, starting from 0.
    Output ‘ab’, is valid because of singe ‘a’ accompanied by single ‘b’.
    Output ‘abb’, is valid because of singe ‘a’ accompanied by 2 ‘b’.
    Output ‘a’, is valid because of singe ‘a’ accompanied by 0 ‘b’.
    Output ‘abbb’, is valid because of singe ‘a’ accompanied by 3 ‘b’.
    Function split()
    Split string by the occurrences of a character or a pattern, upon finding that pattern, the remaining characters from the string are returned as part of the resulting list.
    Syntax :

     re.split(pattern, string, maxsplit=0, flags=0)

    The First parameter, pattern denotes the regular expression, string is the given string in which pattern will be searched for and in which splitting occurs, maxsplit if not provided is considered to be zero ‘0’, and if any nonzero value is provided, then at most that many splits occurs. If maxsplit = 1, then the string will split once only, resulting in a list of length 2. The flags are very useful and can help to shorten code, they are not necessary parameters, eg: flags = re.IGNORECASE, In this split, case will be ignored.
    filter_none

    edit

    play_arrow

    brightness_4
    from re import split 
      
    # '\W+' denotes Non-Alphanumeric Characters or group of characters 
    # Upon finding ',' or whitespace ' ', the split(), splits the string from that point 
    print(split('\W+', 'Words, words , Words')) 
    print(split('\W+', "Word's words Words")) 
      
    # Here ':', ' ' ,',' are not AlphaNumeric thus, the point where splitting occurs 
    print(split('\W+', 'On 12th Jan 2016, at 11:02 AM')) 
      
    # '\d+' denotes Numeric Characters or group of characters 
    # Splitting occurs at '12', '2016', '11', '02' only 
    print(split('\d+', 'On 12th Jan 2016, at 11:02 AM'))