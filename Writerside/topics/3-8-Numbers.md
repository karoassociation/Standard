# 3.8 Numbers

<code-block lang="BNF" src="definitions.bnf" include-lines="24,26,40,41" />

Numbers are statement elements consisting of digits. Karo knows 4 different types of numbers: Hexadecimal number, binary number, integers and decimal numbers.
All numbers can start with a minus symbol (`-`) which indicates that the following number is negative.

## 3.8.1 Integer number

An integer number uses base 10 as the number system. That means the digits `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8` and `9` are allowed. This statement element always produces a `sl.types::number` element.

## 3.8.2 Decimal number

A decimal number is an integer that has a dot symbol (`.`) followed by a decimal fraction. This statement element always produces a `sl.types::float` element.

## 3.8.3 Hexadecimal number

A hexadecimal number starts with a zero followed by the lowercase letter x (`0x`). After that any combination of the digits `0`, `1`, `2`, `3`, `4`, `5`, `6`, `7`, `8` and `9` and the letters `A`, `B`, `C`, `D`, `E` and `F` (in uppercase) is allowed.
This statement element always produces a `sl.types::number` element.

## 3.8.4 Binary number

A binary number starts with a zero followed by the lowercase letter b (`0b`). After that any combination of the digits `0` and `1` is allowed.
This statement element always produces a `sl.types::number` element.
