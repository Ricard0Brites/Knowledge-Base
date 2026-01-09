---
# Operator Precedence (Selected)

| Precedence | Operators                                           | Notes                        |
|------------|----------------------------------------------------|-------------------------------|
| 1          | `::`                                               | Scope resolution             |
| 2          | `++`, `--` (prefix), `*`, `&`, `sizeof`           | Unary operators              |
| 3          | `*`, `/`, `%`                                     | Multiplicative               |
| 4          | `+`, `-`                                          | Additive                     |
| 5          | `<<`, `>>`                                        | Shift                         |
| 6          | `<` ,`>` ,`<=` ,`>=`                              | Relational                   |
| 7          | `==`, `!=`                                        | Equality                      |
| 8          | `&`                                               | Bitwise AND                  |
| 9          | `^`                                               | Bitwise XOR                  |
| 10         | `~`                                              | Bitwise NOT (unary)          |
| 11         | `&&`                                              | Logical AND                  |
| 12         | `||`                                            | Logical OR                   |
| 13         | `?:`                                              | Conditional (ternary)        |
| 14         | `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `&=`, `|=`, `^=`, `<<=` ,`>>=` | Assignment operators |
| 15         | `,`                                               | Comma operator               |