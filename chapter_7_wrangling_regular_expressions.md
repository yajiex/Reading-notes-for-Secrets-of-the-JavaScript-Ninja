# Chapter 7: Wrangling regular expressions
* `[abc]`: signify that we want to match any of the characters `'a'`, `'b'`, or `'c'`. Note that even though this expression spans five characters, it matches only a single character in the candidate string.
* `[^abc]`: any character but `'a'`, `'b'`, or `'c'`
* `[a-m]`: all characters from `'a'` though `'m'` inclusive (and lexicographically) are included in the set.
* The caret character (`^`), when used as the first character of the regex, anchors the match at the beginning of the string
* The dollar sign (`$`) signifies that the pattern must appear at the end of the string
* Repeated occurrences as follows, any of these repetition operators can be greedy or nongreedy. By default, they're greedy they will consume all the possible characters that comprise a match. Annotating the operator with a `?` character (an overload of the `?` operator), as in `a+?`, makes the operation nongreedy: it will consume only enough characters to make a match. For example, if we were matching against the string `aaa`, the regular expression `/a+/` would match all three a characters, whereas the nongreedy expression `/a+?/` would match only one a character, because a single a character is all that's needed to satisfy the `a+` term.
  1. We can specify that a character is optional (in other words, can appear either once or not at all) by following it with `?`. For example, `/t?est/` matches both `test` and `est`.
  2. If we want a character to appear one or many times, we use `+`, as in `/t+est/`, which matches `test`, `ttest`, and `tttest`, but not `est`.
  3. If we want the character to appear zero or many times, `*` is used, as in `/t*est/`, which matches `test`, `ttest`, `tttest`, and `est`.
  4. We can specify a fixed number of repetitions with the number of allowed repetitions between braces. For example, `/a{4}/` indicates a match on four consecutive `a` characters.
  5. We can also specify a range for the repetition count by specifying the range with a comma separator. For example, `/a{4,10}/` matches any string of four through ten consecutive `a` characters.
  6. The second value in a range can be omitted (but leaving the comma) to indicate an open-ended range. The regex `/a{4,}/` matches any string of four or more consecutive `a` characters.
* 
