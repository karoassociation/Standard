# 1.5 Comments

<code-block src="definitions.txt" include-lines="28-31" />

Comments are elements that are allowed almost everywhere in the code (not while in identifier or in a string). These
elements annotate a certain action. The compiler/interpreter ignores all comments.

<warning>
For simplicity the definitions file does not indicate where comments are allowed in the document.
</warning>

## 1.5.1 Line comments

A line comment starts with two forward slashes and lasts until the end of the line. Their content can be anything
except the null character.

## 1.5.2 Block comments

Block comments are encapsulated by `/*` and `*/`. Their content can be anything except the null character or the
sequence `*/`.