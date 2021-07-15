Sourcegraph code search is a search engine that allows you to search code in your own repositories as well as across public open source code. It supports three kinds of search patterns: literal patterns, regular expression patterns, and structural patterns. In this article, we’ll explore literal search patterns and how to use them.

Performing a literal search is useful when you know the exact string that you’re looking for in a code base, like a particular function or variable name. You can find all occurrences of the name across multiple repositories by using your query as a literal pattern. It’s also useful for finding textual content — like error messages or comments — in the code.

By default, all search queries on Sourcegraph are treated as literal patterns. We’ll discuss a few use cases to find useful results with Sourcegraph.

# Finding function calls and definitions

As a developer, there are many times you may need to learn a new codebase: you may need to understand how best to use a new package, may need to be onboarded into an existing project, or may want to learn best practices from tried and tested software. A productive way to become familiar with a codebase is through selecting a function and understanding how it’s used throughout the code and in what contexts.

For example, if you’re learning how the Linux kernel works, one of the topics that you may want to understand is how Linux uses linked lists. Because linked lists are used throughout the Linux kernel and in driver code, they are a foundational starting point to familiarize yourself with the codebase.

The linked list data structure in Linux is called list_head. We can find all instances of the list_head structure by searching for it directly:

```sourcegraph
list_head
```

As you review the results, you may notice that there are some common functions that are frequently used together with linked lists. One of these functions is list_add_tail. To explore further and find all instances of list_add_tail, we can start a new search for that specific function:

```sourcegraph
list_add_tail
```
