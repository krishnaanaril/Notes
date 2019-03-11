# Best practices for a clean and performant Angular application
## 1. trackBy
When an array changes, Angular re-renders the whole DOM tree. But if you use trackBy, Angular will know which element has changed and will only make DOM changes for that particular element.
## 2. const vs let