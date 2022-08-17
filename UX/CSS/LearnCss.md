# [Learn CSS](https://web.dev/learn/css)

## [Box Model](https://web.dev/learn/css/box-model/)

- Everything displayed by css is a **box**.
- The four main areas of the box model: *content box, padding box, border box and margin box* (inner to outer).
- An `inline` element has block margin, but other elements won't respect it. Use `inline-block`, and those elements will respect the block margin, while the element maintains most of the same behaviors it had as an `inline` element. A `block` item will, by default, fill the available inline space, whereas a `inline` and `inline-block` elements will only be as large as their content.
- Having `content-box` as the value of `box-sizing` means that when you set dimensions, such as a `width` and `height`, they will be applied to the content box. If you then set `padding` and `border`, these values will be added to the content box's size.

## [Selectors](https://web.dev/learn/css/selectors/)

- The value of a class attribute can be almost anything you want it to be. One thing that could trip you up, is that you can't start a class (or an ID) with a number, such as `.1element`
- You can use case-sensitive attribute selectors by adding an `s` operator to your attribute selector. You can do the opposite—case insensitivity—by using an `i` operator.
    ``` css
    [data-type='primary' s] {
    color: red;
    }
    ```
- Along with case operators, you have access to operators that match portions of strings inside attribute values.
    ``` css
    /* A href that contains “example.com” */
    [href*='example.com'] {
    color: red;
    }

    /* A href that starts with https */
    [href^='https'] {
    color: green;
    }

    /* A href that ends with .com */
    [href$='.com'] {
    color: blue;
    }
    ```
- You can also use `::selection` to style the content that has been highlighted by a user.
- CSS Combinators
    - Descendant combinator 
    - Next Sibling Combinator (+)
    - Subsequent Siblings Combinator (~)
    - Direct descendant Combinator (>)
