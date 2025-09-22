# A.1 definitions.bnf

<code-block lang="BNF" src="definitions.bnf" />

## A.1.1 Notation

The format of Karo is defined in an Extended Backus-Naur Form. Each rule in the grammar defines a symbol in the following form:

<code-block lang="bnf">
symbol ::= expression
</code-block>

<b>#xN</b>
<p>Where `N` is a hexadecimal integer according to ISO/IEC 10646:2020.</p>

<b>[a-zA-Z]</b>, <b>[#xN-#xN]</b>, <b>[a-zABC]</b>
<p>Matches any character in the specified range (a range us specified with a hyphen) or any of the specified characters. Different forms can be mixed.</p>

<b>[^a-zA-Z]</b>, <b>[^#xN-#xN]</b>
<p>Matches all characters expect the specified (ranges).</p>

<b>"string"</b>, <b>'string'</b>
<p>Matches the string literal inside the quotes.</p>

<b>(expression)</b>
<p>Groups an expression to one unit.</p>

<b>A?</b>
<p><code>A</code> is optional and can be specified once</p>

<b>A B</b>
<p>Matches <code>A</code> followed by <code>B</code>.</p>

<b>A | B</b>
<p>Matches <code>A</code> or <code>B</code> exclusively.</p>

<b>A - B</b>
<p>Matches anything that matches <code>A</code> but not <code>B</code>.</p>

<b>A+</b>
<p>Matches one or more consecutive occurrences of <code>A</code>.</p>

<b>A*</b>
<p>Matches zero or more consecutive occurrences of <code>A</code>.</p>