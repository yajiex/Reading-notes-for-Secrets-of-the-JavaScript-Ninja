# Chapter 7: Wrangling regular expressions
* `[abc]`: signify that we want to match any of the characters `'a'`, `'b'`, or `'c'`. Note that even though this expression spans five characters, it matches only a single character in the candidate string.
* `[^abc]`: any character but `'a'`, `'b'`, or `'c'`
* `[a-m]`: all characters from `'a'` though `'m'` inclusive (and lexicographically) are included in the set.
* The caret character (`^`), when used as the first character of the regex, anchors the match at the beginning of the string
* The dollar sign (`$`) signifies that the pattern must appear at the end of the string
