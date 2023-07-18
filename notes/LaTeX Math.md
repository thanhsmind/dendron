---
type: programing 
---
# LaTeX Math

## Math Environment

to use LaTeX math you need to create a math environment:

```
$MATH GOES HERE$
```

When rendered this will look like: $MATHGOESHERE$

This is an in-line equation

For a multi-line equation that also centers itself you use double dollars

```
$$MATH GOES HERE$$
```

Rendered it will center:$$MATHGOESHERE$$

## Syntax

### Common Constructs

-   `x^2` = $x^2$
-   `x_{ij}` = $x_{ij}$
-   `\sqrt{4}` = $\sqrt{4}$
-   `\sqrt[n]{4}` = $\sqrt[n]{4}$
-   `\frac{2}{3}` = $\frac{2}{3}$

### Super and sub script

Super uses a carat `^`

-   `x^2` = $x^2$

Sub-script uses an underscore `_`

-   `x_{ij}` = $x_{ij}$

### Grouping Items

using the braces `{ }` we can group items together

-   `x_{ij}` = $x_{ij}$

V.S.

`x_ij` = $x_ij$

Where the `J` is back at the normal level not the subscript level

### Optional Arguments

Some commands take optional arguments in square brackets `[ ]`

-   `\sqrt[n]{4}` = $\sqrt[n]{4}$

### Escaped Operators and Characters

things like `\pi` yield π they have no braces `{ }` or brackets `[ ]` and instead are just themselves. This means they can be inserted into other commands and the only limitation might be a space after the escaped sequence so that it doesnt turn into something like `\pix` when you wanted πx

#### Equations are like sentences

These sequences all together read like a sentence with symbols and syntax determining positioning and what is rendered in a logical format

```
$$\sum_{j=0}^7j^2$$
```

$$\sum_{j=0}^7j^2$$

Reads like "_∑_, then below it add _J=5_, raise that whole combo to the power of _7_ then adjacent to that place _J2_.

### Insertable Symbols

#### Calligraphic letter

`\mathcal{LETTER}` == LETTER

#### Greek

[Greek Letters In Statistics](https://publish.obsidian.md/bryan-jenks/Z/Greek+Letters+In+Statistics)

`$\Sigma\,\Delta$` == $\Sigma\,\Delta$

#### Dots

Vertical dots == _⋮_  
Centered dots == _⋯_  
Low dots == _…_  
diagonal dots == _⋱_

using the spacer comma `\,` [[#^2cf429]]

$\{2,3,…\}$

#### Fences

![[Pasted image 20210110231926.png]]

#### Arrays and Matrices
  

![[Pasted image 20210110232016.png]]

  
  

$$\begin{array}{rcl}
0   &6  &6 \\
0   &6  &6 \\
0   &6  &6 
\end{array}$$

#### Spacing

| LaTeX       | Code           |
| ----------- | -------------- |
| $x\,y$      | `$x\,y$`       |
| $x\:y$      | `$x\:y$`       |
| $x\;y$      | `$x\;y$`       |
| $x \quad y$  | `$x \quad y$`  |
| $x \qquad y$ | `$x \qquad y$` |
| $x\!y$      | `$x\!y$`       |
|             |                |


Sometimes you may want some extra space between elements and a space wont work and you need something like `\,`: ^2cf429

`\Sigma \Delta` == $\Sigma \Delta$

v.s.

`\Sigma\,\Delta` == $\Sigma\,\Delta$

There is now a slight space between the two

---
Tags:
Reference:
- ![[undergradmath.pdf]]

Related:
- [https://castel.dev/post/lecture-notes-1/](https://castel.dev/post/lecture-notes-1/)
- [https://arachnoid.com/latex/](https://arachnoid.com/latex/)