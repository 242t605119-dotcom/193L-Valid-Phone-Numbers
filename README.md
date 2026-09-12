# LeetCode 193 - Valid Phone Numbers

## Problem

Given a text file named `file.txt`, write a Bash script to print all valid phone numbers.

A valid phone number must follow one of these two formats:

```text
xxx-xxx-xxxx
```

or:

```text
(xxx) xxx-xxxx
```

where `x` represents a digit from `0` to `9`.

## Example

### Input

```text
987-123-4567
123 456 7890
(123) 456-7890
123-456-789
```

### Output

```text
987-123-4567
(123) 456-7890
```

Only the lines that exactly match one of the required formats are printed.

## Approach

This problem can be solved using the Linux `grep` command with a **regular expression**.

The command used is:

```bash
grep -E '^(\([0-9]{3}\) [0-9]{3}-[0-9]{4}|[0-9]{3}-[0-9]{3}-[0-9]{4})$' file.txt
```

The regular expression checks whether the complete line follows one of the two valid formats.

## Explanation

### `grep`

`grep` searches text for a specified pattern.

### `-E`

The `-E` option enables **Extended Regular Expressions**.

This makes it easier to use alternatives such as `|`.

### `^`

The `^` symbol represents the **beginning of the line**.

### `$`

The `$` symbol represents the **end of the line**.

Using both ensures that the entire line must match the required format.

### `[0-9]{3}`

This means exactly **three digits**.

For example:

```text
123
```

### `[0-9]{4}`

This means exactly **four digits**.

For example:

```text
4567
```

### `|`

The `|` symbol means **OR**.

Therefore, the expression accepts either:

```text
xxx-xxx-xxxx
```

OR:

```text
(xxx) xxx-xxxx
```

## Valid Format 1

```text
987-123-4567
```

Pattern:

```text
[0-9]{3}-[0-9]{3}-[0-9]{4}
```

## Valid Format 2

```text
(123) 456-7890
```

Pattern:

```text
\([0-9]{3}\) [0-9]{3}-[0-9]{4}
```

The parentheses are escaped using `\` because parentheses have special meaning in regular expressions.

## Complete Command

```bash
grep -E '^(\([0-9]{3}\) [0-9]{3}-[0-9]{4}|[0-9]{3}-[0-9]{3}-[0-9]{4})$' file.txt
```

## Key Concept

The main concept in this problem is **Regular Expressions (Regex)**.

Regex allows us to describe a specific text pattern and search for lines that match it.

The important pattern structure is:

```text
Beginning → required phone format → End
```

## Time Complexity

**O(n)** approximately, where `n` is the number of characters in the input file.

The file needs to be scanned to determine which lines match the pattern.

## Space Complexity

**O(1)** auxiliary space in the typical streaming model, apart from the memory used internally by the command.

## Difficulty

**Easy**

## Topics

* Shell
* Bash
* Linux Commands
* `grep`
* Regular Expressions
* Text Processing
* Pattern Matching

## What I Learned

This problem helped me understand how regular expressions can be used with Linux commands to validate text patterns.

I learned how `grep -E` can identify lines that follow a specific format.

The key idea is:

```text
grep + Regex → Find lines matching the required pattern
```

## Author

T.Nandhini
