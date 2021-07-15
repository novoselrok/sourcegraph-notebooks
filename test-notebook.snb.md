Sourcegraph lets you search code across repositories, supporting three kinds of search patterns: literal patterns, regular expression patterns, and structural patterns. In this article, we’ll take a look at regular expressions patterns and how to use them in Sourcegraph.

Regular expressions, often shortened as regex, help you find code that matches a pattern (including classes of characters like letters, numbers and whitespace), and can restrict the results to anchors like the start of a line, the end of a line, or word boundary.

# Finding a pattern

Regular expressions are useful when you're looking for any strings that match a particular pattern. A common pattern in CSS is the RGB hex color code, like #6495ED (cornflower blue) or #663399 (Rebecca purple).

To match RGB hex color codes, we can write a regular expression that has three parts:

- A hash symbol (#)
- A character class for hexadecimal characters: [0-9a-f]
- A repetition operator, indicating that we're looking for 6 characters that match the above character class: {6}

Combining these parts into one regular expression, we can use this pattern in a Sourcegraph search. To make the results more relevant, we can add the lang:css filter so that we target only CSS files.

```sourcegraph
#[0-9a-f]{6} lang:css patterntype:regexp
```

# Finding a set of function calls

One use case for regular expression search is when you are trying to find examples of file system function calls. You may be interested in functions that read or write files: readFile and writeFile. While you could search for them individually, it can be useful to perform one search that includes results for both functions.

readFile and writeFile have a pattern in common: they both end in File. We can write a regular expression that expresses this pattern like so:

```sourcegraph
(read|write)File patterntype:regexp
```
