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
- A double colon `(::)` is what distinguishes a pseudo-element from a pseudo-class
- CSS Combinators
    - Descendant combinator 
    - Next Sibling Combinator (+)
    - Subsequent Siblings Combinator (~)
    - Direct descendant Combinator (>)

## [The Cascade](https://web.dev/learn/css/the-cascade/)
- In CSS, Cascade is the algorithm for solving conflicts where multiple css rules apply to an HTML element.
- The cascade algorithm is split into 4 distinct stages:
    - **Position and order of appearance**: the order of which your CSS rules appear
    - **Specificity**: an algorithm which determines which CSS selector has the strongest match
    - **Origin**: the order of when CSS appears and where it comes from, whether that is a browser style, CSS from a browser extension, or your authored CSS
    - **Importance**: some CSS rules are weighted more heavily than others, especially with the !important rule type

## [Specificity](https://web.dev/learn/css/specificity/)
- Scoring of each selector type
    | Selector | Point |
    |----------|-------|
    | Universal Selector | 0 |
    | Element or pseudo-element | 1 |
    | Class, pseudo-class or attribute | 10 |
    | Id Selector | 100 |
    | Inline Style | 1000 |
    | !important rule | 10000 |
- In diagrams and specificity calculators, the specificity is often visualized like this: `1-2-1` for `#specialty:hover li.dark`. The left group is `id` selectors. The second group is class, attribute, and pseudo-class selectors. The final group is element and pseudo-element selectors.
- A matching specificity score sees the newest instance win.

## [Inheritance](https://web.dev/learn/css/inheritance/)
- Some CSS properties inherit if you don't specify a value for them. 
- You can make any property inherit its parent's computed value with the `inherit` keyword. 
- The `initial` keyword sets a property back to that initial, default value.
- The `unset` property behaves differently if a property is inheritable or not. If a property is inheritable, the `unset` keyword will be the same as `inherit`. If the property is not inheritable, the `unset` keyword is equal to `initial`.

## [Color](https://web.dev/learn/css/color/)
- An alpha value is a percentage of transparency.
- HSL stands for hue, saturation and lightness. 
    - Hue describes the value on the color wheel, from 0 to 360 degrees, starting with red (being both 0 and 360).
    - Saturation is how vibrant the selected hue is. A fully desaturated color (with a saturation of 0%) will appear grayscale.
    - Lightness is the parameter which describes the scale from white to black of added light. A lightness of 100% will always give you white.
- Second and third parameters of `hsl()` should be in percentages.