# General CSS Concepts
## Individual transform properties 
- There are individual properties for CSS transforms, the properties are `translate`, `rotate` and `scale`.
- Not all transformation functions have matching css properties. eg: `skewX()`, `matrix()`
- With the individual transformation properties, the order is not the order in which they are declared. The order is always the same: first `translate` (outside), then `rotate`, and then `scale` (inside). 
- These new properties also work with the `will-change` property.
- The `will-change` CSS property hints to browsers how an element is expected to change. Browsers may set up optimizations before an element is actually changed.
- The **stacking context** is a three-dimensional conceptualization of HTML elements along an imaginary z-axis relative to the user, who is assumed to be facing the viewport or the webpage.
- `z-index` only works on positioned elements (position:absolute, position:relative, or position:fixed).