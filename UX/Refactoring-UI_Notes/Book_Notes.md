# Refactoring UI - Book
## Starting from scratch
* Start with a feature not layout. Think about the feature and add necessary UI elements for it.
* Details comes later. In the start don't waste much time on low level detials like fonts and icons.
* Hold the color first. Design in gray scale.
* Don't over invest. Move fast and start build the real thing as mockups are of no use to user.
* Don't design too much. Instead of designing everything upfront, work in short cycles. Iterate on working design until there are no problems to solve. Then jump back to design mode and start working on the next feature.
* Be a pessimist. Don't imply functionality in your designs that you aren't ready to build. When you are designing a system, expect it to be hard to build. If part of the feature is nice to have design it later.
* Choose a personality. Eg. Secure & professional for banks, while playful for startups. 
    * For elegant and classic look use serif fonts otherwise use sans-serif. 
    * Choose colors wisely.
    * Use of border radius - No border radius means serious, otherwise playful.
* Limit your choices.
    * Design systems in advance. Eg. colors and font-size.
    * Design by the process of elimination. If one of the outer options looks best, do another comparison using that option as the “middle” value and make sure there’s not a better choice.
    * Systematize everything. You'll want systems for things like:
        * Font size
        * Font weight
        * Font style
        * Color
        * Margin
        * Padding
        * width
        * Height 
        * Box shadows
        * Border radius
        * Border width
        * Opacity
## Hierarchy is Everything
* Not all elements are equal. When everything in an interface is competing for attention, it feels noisy and chaotic.
* Size isn't everything. Relying too much on font size to create hierarchy is a mistake.
    * Stay away from font weights less than 400 for UI work.
* Dont' use grey text on colored backgrounds. Choose a color with same hue as background and adjust saturation and lightness.
* Emphasize by de-emphasizing.
    * De-emphasize competitng elements by giving them a ligher shade. 
    * If side bar is competing with the main area, don't give it a background color.
* Labels are a last resort. You might not need a label at all.
    * Combine labels and values. Eg. 12 left in stock instead of In stock: 12
    * Labels are secondary. The data itself is what matters, the label is just there for clarity.
    * Only emphasize the label when the user is looking for it. Eg: Mobile phone specificaiton.
* Separate visual hierarchy from document hierarchy. Don’t let the element you’re using influence how you choose to style it — pick elements for semantic purposes and style them however you need to create the best visual hierarchy.
* Balance weight and contrast.
    * Use contrast to compensate weight. If an icon is placed next to text, icon will feel more emphasized as it have more weight.
    * Use weight to compensate for contrast. Eg. Increase border width instead of border color.
* Semantics are secondary
    * Destructive actions. If a destructive button is not the primary action in a page, it is better to give it a secondary or tertiary button treatment.
## Layout and Spacing
* Start with too much white space. Give elements a little room to breathe.
    * White space should be removed not added.
* Establish a spacing and sizing system.
    * A linear scale won't work. For a system to be truly useful, it needs to take into consideration the relative difference between adjacent values.
    * If you want your system to make sizing decisions easy, make sure no two values in your scale are ever closer than about 25%.
    * Defining the system. Start with a sensible base value.
    * Using the system. Provide consistency to the design through out.
* You don't have to fill the whole screen.
    * Just because you have space doesn't mean you need to use it.
    * Shrink the canvas. If you are designing a responsive ui, start with 400 px screen and design the mobile layout first.
    * Thinking in columns. If possible make supporting text to another column.
    * Don't force it. If you need a lot of space go for it.
* Grids are overrated.
    * The problem with treating grid systems like a religion is that there are a lot of situations where it makes much more sense for an element to have a fixed width instead of a relative width.
    * Don't shrink an element until you need to.
* Relative sizing doesn't scale.
    * As a general rule, elements that are large on large screens need to shrink faster than elements that are already fairly small — the difference between small elements and large elements should be less extreme at small screen sizes.
    * Relationship within elements
* Avoid ambiguous spacing
    * Whenever you’re relying on spacing to connect a group of elements, always make sure there’s more space around the group than there is within it — interfaces that are hard to understand always look worse.
## Designing Text
* Establish  a type scale.
    * Choosing font sizes without a system is bad idea for two reasons. 
        1. It leads to annoying inconsistencies in your design
        2. It slowsdown your workflow.
    * How to define a type system.
        1. Choose a scale. Linear scale won't work. 
        2. Avoid fractional sizes.
        3. It is better to choose a handpicked scale and relying on mathematical ratios.
        4. Avoid em units. Stick to px or rem units to be consistent with your system.
* Use good fonts
    * Play it safe. Choose readily available and common fonts.
    * Ignore typefaces with less than five weights.
    * Optimise for legibility.
    * Trust the wisdom of the crowd. 
    * Steal from people who care.
    * Develop your intution.
* Keep your line length in check.
    * For the best reading experience, make your paragraphs wide enough to fit
between 45 and 75 characters per line.
    * Dealing with wider content. Images and other elements can have more width but we should sick with 25-35em width for main text.
    * Baseline not center. Baseline is the imaginery line that letters rest on.
* Line height is proportional
    * Your line-height and paragraph width should be proportional — narrow content can use a shorter line-height like 1.5, but wide content might need a line-height as tall as 2.
    * Line-height and font size are inversely proportional — use a taller line-height for small text and a shorter line-height for large text.
* Not every link needs a color.
    * If there are more links in a page, give emphasis using dark color or font weight.
* Align with readability in mind
    * Don't center long form of text. If something is longer that 2-3 lines, it will always look better in left-alignment.
    * Right align numbers
    * Hyphenate justified text
* Use letter spacing effectively
    * As a general rule, you should trust the typeface designer and leave letterspacing alone.
    * It often makes sense to increase the letter-spacing of allcaps text to improve readability
## Working with color
* Ditch hex for HSL. Hex and RGB are the most common formats to represent color, but they aren't the most useful.
    * HSL vs HSB. Both are different. HSB is more common than HSL in design software, but browsers only understand HSL, so if you’re designing for the web, HSL should be your weapon of choice.
* You need more colors than you think.
    * You can break a good color palette down into three categories.
        1. Greys
        2. Primary colors
        3. Accent colors
* Define your shades upfront.
    * Define a fixed set of shades up front that you can choose from as
you work.
    * Choose base color first. There’s no real scientific way to do this, but for primary and accent colors, a good rule of thumb is to pick a shade that would work well as a button background.
    * Find the edges. Choose the darker and lighter shades.
    * Fill in the gaps. Nine is a great number because it’s easy to divide and makes filling in the gaps a little more straightforward. Let’s call our darkest shade 900, our base shade 500, and our lightest shade 100.
* Don't let lightness kill your saturation
    * Use perceived brightness to your advantage.
        * A way to change the brightness of a color is by rotating the hue. Don’t rotate the hue more than 20-30° or it will look like a totally different color instead of just lighter or darker.
* Greys don't have to be grey. 
    * True greys have zero saturation, add some saturation to make it nice.
    * Color temperature. To make greys cool and some blue saturation. To make greys warm add some yellow or orange saturation.
* Accessibility doesn't have to mean ugly
    * Flipping the contrast. Apply dark color on light backgrounds.
    * Rotating the hue towards a brighter color helps to add contrast.
* Don't rely on color alone.
    * Add some contrast to help people with color blindness.
## Creating Depth
* Emulate a light source.
    * Light comes from above.
    * Simulating a light source.
        1. Raised elements
        2. Inset elements
    * Don't get carried away. Borrowing some visual cues from the real world is a great way to add a bit of depth, but there’s no need to try and make things look photo-realistic.
* Use shadows to convey elevation.
    * Shadows can be more than just a flashy effect — used thoughtfully, they let you position elements on a virtual z-axis to create a meaningful sense of depth.
    * Small shadows with a tight blur radius make an element feel only slightly raised off of the background, while larger shadows with a higher blur radius make an element feel much closer to the user.
    * Use a smaller shadow for something like a button. Medium shadows are useful for things like dropdowns. Large shadows are great for modal dialogs.
    * Establish an elevation system
* Shadows can have two parts. - One cast by the direct light and other by the object/element. <Not if sure this significant>
    * Accounting for elevation. 
* Even flat designs can have depth
    * Creating depth with color. Make an element lighter than the background color to make it feel like it’s raised off of the page, or darker than the background color if you want it to feel inset like a well.
    * Using solid shadows, without blur radius.
* Overlap elements to create layers.
## Working with Images
* Use good photos
    * If design needs photos and you are not a talented photagrapher, you've two options:   
        1. Hire a photagrapher
        2. Buy stock photos
* Text need consistent contrast.
    * Add an overlay. To fix the contrast issue of images. To make the text readable.
    * Or Add contrast or colorize the image.
    * Or add text shadow
* Everything has an intended size.
    * Don't scale up icons, even if they are vector. The reason is that small icons lack details.
    * If small icons are all you've got, try enclosing them in another shape and give background color
    * Don't scale down screenshots. 
    * Dont' scale down icons either.
* Beware use uploaded content.
    * Control the shape and color of user submitted images.
    * Prevent background bleed. if user submitted image is same as that of background color.
## Finishing touches
* Supercharge the defaults.
    1. Replace bullets with icons.
    2. Promote 'quotes' by changing color and size.
    3. If you've forms. Try to have custom checkboxes and radio buttons.
* Add color with accent borders
* Decorate your backgrounds
    * Change background color. Give slight gradient for energetic look.
    * Use a repeating pattern. It do not have to be through out the background but along the borders.
    * Add a simple shape or illustration
* Don't overlook empty states.
    * If you’re working on something that has a bunch of supporting UI like tabs or filters, consider hiding that stuff entirely. There’s no point in presenting a bunch of actions that don’t do anything until the user has created some content.
* Use fewer borders
    * Use a box shadow
    * Use two different background colors.
    * Add extra spacing.
* Think outside the box
    * Don’t let your existing beliefs hold back your designs. Eg. selectable cards instead of radio buttons.
## Leveling Up
* Looking for decisions that you wouldn't have made.
* Rebuid your favourite interfaces.