# BNF and Syntax Diagrams

## Introduction

Backus-Naur Form (BNF) is a formal notation used to describe the syntax (grammar) of programming languages and other formal languages. It provides a way to specify the rules that define valid structures in a language, such as how statements, expressions, and declarations are formed. BNF was developed by John Backus and Peter Naur in the 1960s for describing the syntax of ALGOL 60, and it remains a fundamental tool in compiler design and language specification.

Syntax diagrams, also known as railroad diagrams, are a graphical alternative to BNF for representing the same grammatical rules. They use visual elements like boxes, arrows, and loops to show the flow of valid language constructs.

Both BNF and syntax diagrams allow developers and compilers to understand and enforce the rules of a language, ensuring that programs are syntactically correct before execution.

## BNF Notation

Consider a simple language for arithmetic expressions involving addition and multiplication of numbers.

```
<expression> ::= <term> | <expression> + <term>
<term> ::= <factor> | <term> * <factor>
<factor> ::= <number> | ( <expression> )
<number> ::= <digit> | <number> <digit>
<digit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
```

This BNF defines:

- An `<expression>` can be a single `<term>` or an `<expression>` followed by `+` and another `<term>`.
- A `<term>` can be a single `<factor>` or a `<term>` followed by `*` and another `<factor>`.
- A `<factor>` can be a `<number>` or an `<expression>` enclosed in parentheses.
- A `<number>` is one or more `<digit>`s.
- A `<digit>` is any single digit from 0 to 9.

Using these rules, expressions like `3 + 4 * 5` or `(1 + 2) * 3` are valid, while `3 +` is not.

## Syntax Diagrams

Syntax diagrams provide a visual representation of the same grammatical rules. They are easier to read for some people and are commonly used in programming language manuals.

**Key Elements**

- **Boxes**: Represent terminals (keywords, symbols).
- **Arrows**: Show the flow of the diagram.
- **Circles/Ovals**: Represent non-terminals or optional elements.
- **Loops**: Indicate repetition.

### Example: Syntax Diagram for Arithmetic Expressions

![Syntax Diagram Example](https://upload.wikimedia.org/wikipedia/commons/f/ff/Syntax-diagram-example.png)
