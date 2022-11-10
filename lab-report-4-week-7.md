# Lab 4: vim & remote work

## I. Editing in vim
In `DocSearchServer.java`, change the name of the `start` parameter of `getFiles`, and all of its uses, to instead be called `base`.

`:` `1` `2` `,` `3` `0` `s` `/` `\` `<` `s` `t` `a` `r` `t` `\` `>` `/` `b` `a` `s` `e` `/` `g` `I` `<Enter>`

### (1). Potential problems
1. What we want to modify is the block scoped variable in the `getFiles` method, and direct replacement may modify other methods or global variable.
2. Direct replacement may modify part of the word, such as `int startedNum` will be changed to `int baseedNum`
3. `start` may not be a variable, such as it appears in a comment, in quotes, or as a method name of a class.

### (2). Line number
In order to solve the first problem, we need to limit the scope of replacement. In vim, `[a],[b]s` means to replace between lines `a` and `b`, including `a` `b`.

Then we need to display the line number in vim, we can enter `:set nu` in normal mode, or add set nu to `~/.virmc`. But the former is temporary, it will be invalid after exiting vim.

![]("src/yuhang_lab4_0.png")

### (3). Exact match
For the second question, when vim finds and replaces, if the string is enclosed in `\<\>`, it will match the complete word.

Examples:

![]("src/yuhang_lab4_1.png")

![]("src/yuhang_lab4_2.png")
