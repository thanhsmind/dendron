---
alias:
- Definition Lists
type: programing
---
# Markdown Definition Lists

## Syntax

```
First Term
: definition

Second Term
: This is one definition of the second term.
: This is another definition of the second term.
```

First Term  
: definition

Second Term  
: This is one definition of the second term.  
: This is another definition of the second term.

The HTML looks like this:

```
<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>
```

and renders like this:

![Pasted image 20201207020100.png](https://publish-01.obsidian.md/access/dfaa274ac11551c6243126bea0bf012c/Media/Pasted%20image%2020201207020100.png)

In Obsidian it renders like this:


<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>