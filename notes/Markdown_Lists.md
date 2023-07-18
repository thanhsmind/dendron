---
alias:
- Lists
type: programing 
---
# Markdown Lists

## Ordered Lists

ordered lists can be explicitly numbered

```
1. First item
2. Second item
3. Third item
4. Fourth item
```

Or they will be automatically numbered based on order and indentation

```
1. First item
1. Second item
1. Third item
1. Fourth item
```

becomes:

```
1. First item
2. Second item
3. Third item
4. Fourth item
```

Indentation levels reset the counts for each instance of a sublist

1.  First item
2.  Second item
3.  Third item
    1.  Indented item
    2.  Indented item
4.  Fourth item

Even when unordered the relative links still work correctly

```
1. First item
1. Second item
1. Third item
    1. Indented item
    1. Indented item
1. Fourth item
```

becomes:

```
1. First item
2. Second item
3. Third item
    1. Indented item
    2. Indented item
4. Fourth item
```

## Unordered lists

List items are set with specific characters: `-*+`

The sublevels are only determined only by indentation either 2 spaces or a tab for indenting the levels

-   spaces
    -   two of them

-   tabs
    -   one tab