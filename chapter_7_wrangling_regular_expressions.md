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
* Predefined character class and character terms:
  - `\t` => Horizontal tab
  - `\b` => Backspace
  - `\v` => Vertical tab
  - `\f` => Form feed
  - `\r` => Carriage return
  - `\n` => Newline
  - `\cA : \cZ` => Control characters
  - `\x0000 : \xFFFF` => Unicode hexadecimal
  - `\x00 : \xFF` => ASCII hexadecimal
  - `.` => Any character, except for newline (\n)
  - `\d` => Any decimal digit; equivalent to [0-9]
  - `\D` => Any character but a decimal digit; equivalent to [^0-9]
  - `\w` => Any alphanumeric character including underscore; equivalent to `[A-Za-z0-9_]`
  - `\W` => Any character but alphanumeric and underscore characters; equivalent to `[^A-Za-z0-9_]`
  - `\s` => Any whitespace character (space, tab, form feed, and so on)
  - `\S` => Any character but a whitespace character
  - `\b` => A word boundary
  - `\B` => Not a word boundary (inside a word)
* `/(ab)+/` matches one or more consecutive occurrences of the substring `ab`
* Back Reference: An example could be `/^([dtn])a\1/`, which matches a string that starts with any of the `d`, `t`, or `n` characters, followed by an `a`, followed by whatever character matched the first capture. This latter point is important! This isn't the same as `/[dtn] a[dtn]/`. The character following the `a` can't be any of `d`, or `t`, or `n`, but must be whichever one of those triggered the match for the first character. As such, which character the `\1` will match can't be known until evaluation time.
* `/<(\w+)>(.+)<\/\1>/` => matching XML-type markup elements.
* Compiling a regex once and storing it in a variable for later reference can be an important optimization.
* Each regex has a unique object representation: every time a regular expression is created (and thus compiled), a new regular expression object is created. This is unlike other primitive types (like string, number, and so on) because the result will always be unique.
* The array returned by match always includes the entire match in the first index, and then each subsequent capture following.
* Using a local regular expression (one without the global flag) with the String object's `match()` methods returns an array containing the entire matched string, along with any matched captures in the operation. But when we supply a global regular expression (one with the `g` flag included), `match()` returns something rather different. It's still an array of results, but in the case of a global regular expression, which matches all possibilities in the candidate string rather than just the first match, the array returned contains the global matches; captures within each match aren't returned in this case.
* `exec()` can be repeatedly called against a regular expression, causing it to return the next matched set of information every time it's called.