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

## [Sizing Units](https://web.dev/learn/css/sizing/)
- It's a good idea to use a unitless value for `line-height`, rather than specifying a unit. It denotes a ratio. Defining a unitless `line-height` keeps the line-height relative to the font size.
- Other angle units include `rad` (radians), `grad` (gradians), and `turn` units, which represent a part of an angle, where `1turn = 360deg`, and `0.5turn = 180deg`.
- Relative units are more adaptive and fluid because of their contextual awareness, but there's a power and predictability to absolute units that can be foundational for certain designs.

## [Layout](https://web.dev/learn/css/layout/)
- You can't set an explicit width and height on inline elements. Any block level margin and padding will be ignored by the surrounding elements.
- Flexbox is a layout mechanism for one-dimensional layouts. Layout across a single axis, either horizontally or vertically. 
- `flex-grow` specifies how much of the remaining space in the flex container should be assigned to the item (the flex grow factor).
- In case both `flex-basis` (other than auto) and `width` (or height in case of flex-direction: column) are set for an element, `flex-basis` has priority.
- Use `float` to wrap text around an image.

## [Flexbox](https://web.dev/learn/css/flexbox/)
- The key to understanding flexbox is to understand the concept of a **main axis** and a **cross axis**. The main axis is the one set by your `flex-direction` property.
- You should be cautious when using any properties that reorder the visual display away from how things are ordered in the HTML document, as it can negatively impact accessibility. The `row-reverse` and `column-reverse` values are a good example of this.
- The set of properties can be placed into two groups. Properties for space distribution, and properties for alignment. 
- The properties which distribute space are:
    - **justify-content**: space distribution on the main axis.
    - **align-content**: space distribution on the cross axis.
    - **place-content**: a shorthand for setting both of the above properties.
- The properties used for alignment in flexbox:
    - **align-self**: aligns a single item on the cross axis
    - **align-items**: aligns all of the items as a group on the cross axis

## [Grid](https://web.dev/learn/css/grid/)
- A grid is made up of lines, which run horizontally and vertically. If your grid has four columns, it will have five column lines including the one after the last column.
- A track is the space between two grid lines. A row track is between two row lines and a column track between two column lines.
- `auto-fill` places as many items into the template as possible, without stretching. Fit makes them fit.

## [Logical Properties](https://web.dev/learn/css/logical-properties/)
- **Block flow** is the direction in which content blocks are placed. 
- The **inline flow** is how text flows in a sentence.
-  With logical properties, `margin-top` becomes `margin-block-start`. This means that regardless of language and text direction, the block flow has appropriate margin rules.
- Logical properties bring two new units: `vi` and `vb`. A `vi` unit is 1% of the viewport size in the inline direction. The non-logical property equivalent is `vw`. The `vb` unit is 1% of the viewport in the block direction. The non-logical property equivalent is `vh`.

## [Spacing](https://web.dev/learn/css/spacing/)
- The margin shorthand can also be used with one, two, or three values. Adding a fourth value lets you set each individual side. These are applied as follows:
    - One value will be applied to all sides. `(margin: 20px)`.
    - Two values: the first value will be applied to the top and bottom sides, and the second value will be applied to the left and right sides. `(margin: 20px 40px)`
    - Three values: the first value is top, the second value is left and right, and the third value is bottom. `(margin: 20px 40px 30px)`.
- If you make an element absolutely positioned, using position: absolute, the margin will no longer collapse. The margin also won't collapse if you use the float property, too.
- If we apply margin to flexbox with column direction, the margins are combined, instead of collapsed.

## [Pseudo-elements](https://web.dev/learn/css/pseudo-elements/)
- You can also insert a [counter](https://developer.mozilla.org/docs/Web/CSS/counter()) in the `content` property of `::before` and `::after`.
- You can only insert a `::before` or `::after` element to an element that will accept child elements (elements with a document tree), so elements such as `<img />`, `<video>` and `<input>` won't work.
- `input[type="checkbox"]` is an exception. It is allowed to have pseudo-element children.
- You can only use `:first-letter` on block containers. Therefore, it won't work if you try to add it to an element that has `display: inline`.

## [Pseudo-classes](https://web.dev/learn/css/pseudo-classes/)
- A pseudo-class lets you apply styles based on state changes and external factors. 
- The `:target` pseudo-class selects an element that has an id matching a URL fragment. 
-  It's recommended that you use the **LVHA** rule for styling links with pseudo-classes in a particular order: `:link`, `:visited`, `:hover`, `:active`.
- It's not a good idea to rely solely on color to signify state changes— especially red and green—because colorblind and low-vision users can struggle to see a state change, or even miss it completely. A good idea is to use color to support state changes, along with text changes and icon changes to visually signify change.

## [Borders](https://web.dev/learn/css/borders/)
- The order of values in the border shorthand are `border-width`, `border-style` and then, `border-color`.
- By defining a single value for a corner with `border-radius`, you are using another shorthand because a border radius is split into two parts: the vertical and horizontal sides. This means that when you set `border-top-left-radius: 1em`, you are setting the **top-left-top** radius and the **top-left-left** radius.

## [Shadows](https://web.dev/learn/css/shadows/)
- The `drop-shadow()` CSS function applies a drop shadow effect to the input image.
- You can add as many shadows as you like with box-shadow. Add a comma separated collection of value sets to achieve this.
- When you add a `box-shadow` it is clipped to the shape of your box, but `text-shadow` has no clipping. This means that if your text is fully or semi transparent, the shadow is visible through it.
- The `drop-shadow` filter has the same values as `box-shadow` but the `inset` keyword and `spread` value are not allowed. You can add as many shadows as you like, by adding multiple instances of `drop-shadow` values to the `filter` property.

## [Focus](https://web.dev/learn/css/focus/)
- The `<main>` has a `tabindex="-1"` attribute value, which means it can be programmatically focused. 
-  If `tabindex` on a HTML element is set to `0`, it can receive focus via the tab key and it will honour the global tab index, which is defined by the document source order.
- If you set `tabindex` to `-1`, it can only receive focus programmatically.
- Certain elements are automatically focusable; all form elements, buttons and links.
- **Global tab index** is defined by the document source order.
- Creating a focus state that has contrast with an element's default state is incredibly important. The default browser styles do this already for you, but if you want to change this behaviour, remember the following:
    - Avoid using `outline: none` on an element that can receive keyboard focus
    - Avoid replacing `outline` styles with `box-shadow` as they don't show up in Windows High Contrast Mode
    - Only set a positive value for `tabindex` on an HTML element if you absolutely have to
    - Make sure the focus state is very clear vs the default state

    ## [Z-index and stacking contexts](https://web.dev/learn/css/z-index/)
    - Elements will appear above another element if they have a higher `z-index` value. 
    - If no `z-index` is set on your elements then the default behaviour is that document source order dictates the Z axis. This means that elements further down the document sit on top of elements that appear before them.
    - In normal flow, if you set a specific value for `z-index` and it isn't working, you need to set the element's position value to anything other than `static`.
    - A **stacking context** is a group of elements that have a common parent and move up and down the z axis together.
    - The `z-index` of elements inside of a stacking context are always relative to the parent's current order in its own stacking context.
    - You can create a new stacking context by adding a value for properties which create a new composite layer such as `opacity`, `will-change` and `transform`. 

    ## [Functions](https://web.dev/learn/css/functions/)
    - The arguments passed into **functional selectors** are CSS selectors, which are then evaluated. If there is a match with elements, the rest of the CSS rule will be applied to them.
    - The `calc()` function can be nested inside another `calc()` function. You can also pass custom properties in a `var()` function as part of an expression.
    - The `clip-path`, `offset-path` and `shape-outside` CSS properties use shapes to visually clip your box or provide a shape for content to flow around.
    - `perspective` property —which is part of the transform family of properties—to alter the distance between the user and the Z plane. This gives the feeling of distance and can be used to create a depth of field in your designs.

    ## [Gradients](https://web.dev/learn/css/gradients/)
    - You can add as many colors and color stops as you like in a `linear-gradient()`, and you can layer gradients on top of each other by separating each gradient with a comma.
    - You can add as many color stops as you want in `conic-gradient()`, like with other gradient types. A good use case for this capability, with conic gradients is rendering pie charts with CSS.
    - They could be the same color and appear solid, but yes, at least 2 colors are required to create a gradient.

    ## [Animations](https://web.dev/learn/css/animations/)
    - Inside the keyframes rule, `from` and `to` are keywords that represent `0%` and `100%`, which are the start of the animation and end.
    - Values appear to curve with easing functions because easing is calculated using a **bézier curve**, which is used to model velocity. 
    - The `steps()` easing function lets you break the timeline into defined, equal intervals.
    - Users can define in their operating system that they prefer to reduce motion experienced when they interact with applications and websites. This preference can be detected using the `prefers-reduced-motion` media query.
    - The browser will take the current state of the element as a keyframe, so at minimum, 1 keyframe is required inside a `@keyframe` animation.

    ## [Filters](https://web.dev/learn/css/filters/)
    - If you pass an angle to `hue-rotate`, such as degrees or turns, it shifts the hue of all the element's colors, changing the part of the color wheel it references. 
    - The difference between `backdrop-filter` and filter is that the `backdrop-filter` property only applies the filters to the background, where the `filter` property applies it to the whole element.
    - The `url` filter allows you to apply an SVG filter from a linked SVG element or file. 

    ## [Blend Modes](https://web.dev/learn/css/blend-modes/)
    - **Duotone** is a popular color treatment for photography which makes an image look like it is only made up of two contrasting colors: one for highlights and the other for lowlights.
    - The `mix-blend-mode` applies blending to a whole element and the `background-blend-mode` applies blending to the background of an element.
    - Blend modes fall into two categories: **separable and non-separable**. A separable blend mode considers each color component, such as RGB, individually. A non-separable blend mode considers all color components equally.