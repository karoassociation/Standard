# 3.7 Strings

A string is a representation of characters which are enclosed by double quotes (`"`) or single quotes (`'`).

## 3.7.1 String escape sequences

In a string literal escape sequences can be specified to insert certain special characters. These sequences are initialized by a backslash (`\`) and a sequence of other characters specified in the following table:

| Escape sequence characters | Gets replaced by the Unicode codepoint (in hexadecimal) |
|----------------------------|---------------------------------------------------------|
| `0`                        | `0000`                                                  |
| `\`                        | `005C`                                                  |
| `a`                        | `0007`                                                  |
| `b`                        | `0008`                                                  |
| `e`                        | `001B`                                                  |
| `f`                        | `001C`                                                  |
| `n`                        | `000A`                                                  |
| `r`                        | `000D`                                                  |
| `t`                        | `0009`                                                  |
| `v`                        | `000B`                                                  |

In addition, you can use the `\u` escape sequence followed by a 4-digit hexadecimal number (uppercase) to insert the corresponding Unicode character. 