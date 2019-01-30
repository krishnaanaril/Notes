* What can Sass/SCSS do that Vanilla CSS can’t?
    1. Nested Rules
    2. Variables
    3. Better Operators
    4. Functions
    5. Trigonometry
    6. Code flow and control statements
    7. Mixins
* SASS stands for Syntactically Awesome Style Sheet.
* SCSS stands for Sassy Cascading Style Sheets.
* There are 5 CSS pre-processors: Sass, SCSS, Less, Stylus and PostCSS.
* Nesting 
    ```css
    .a {
    background-color: $acolor;
    width: 100vw;
    height: 100vh;
    .b {
        background-color: $bcolor;
        width: 80vw;
        height: 80vh;
        .c {
            background-color: $ccolor;
            width: 60vw;
            height: 60vh;
        }
    }
}
    ```
* A partial is simply a Sass file named with a leading underscore. You might name it something like _partial.scss. The underscore lets Sass know that the file is only a partial file and that it should not be generated into a CSS file. Sass partials are used with the @import directive.
*  A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. A good use of a mixin is for vendor prefixes. To create a mixin you use the @mixin directive and give it a name. After you create your mixin, you can then use it as a CSS declaration starting with @include followed by the name of the mixin.    