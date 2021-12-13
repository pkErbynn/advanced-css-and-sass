# advanced-css-and-sass

Taking my CSS skills to the next LEVEL!

## 3 pillars of good html and css
1. Responsive design
    - Fluid layouts
    - Media queries
    - Responsive images
    - Correct units
    - Desktop-first vs mobile-first
2. Maintainable and scalable code
    - Clean
    - Easy-to-understand
    - Growth/extensible
    - Reuseable
    - How to organize files
    - How to name classes
    - How to structure html
3. Web performance
    - Less http request
    - Less code
    - Compress code
    - Use a CSS preprocessor
    - Less images
    - Compress images

## CSS behind-the-scenes
<pre>
Load html ---> Parse html ---------------> Document Object Model (DOM) ----------------------------
                    |                                                                              |
                    |                                                                              |
                    |                                                                              |
                Load CSS ---> Resolve conflicting CSS                                              |
                              declarations (Cascade)                                               | 
                                            +                                                      |
                              Process final css values    -----------> CSS Obj Model (CSSOM) ------|
                                                                                                   |
                                                                                                   |
                                                                                                   |
Final rendered website <--- Website rendering(by the visual formatting model) <--- Render tree <---|
</pre>

## CSS Terminology
<pre>
.selector {
    declaration block
    property: declared value;  <---- declaration
}
</pre>

## CSS Presedence
1. Importance: author/dev > user > browser
2. Specificity: inline > IDs > Classes,pseudo-classes,attrib>Elements,pseudo-elements
3. Source css order: the last declation in the code will override all other declarations and will be applied

NB: <br>
* declarations marked !importance has the highest priority
* but, better to use correct specificities - more maintainable code
* inline style over external stylesheets
* priority calculator: (inline, id, class, element) == (0, 0, 0, 0)

## CSS Value processing
- each property has init value, if not declared/no inheritance
- browser specify a root font-size (usually 16px)
- Percentages and relative values are always converted to pixels
- %: measured relative to parent's font-size, if used to specify font-size
- %: measured relative to parent's widths, if used to specify leghts (padding, margin, etc)
- em: measured relative to **parent's font-size**, if used to specify font-size (2em = (2 x parent's size))
- em: measured relative to **current** font-size, if used to specify font-size (2em = (2 x parent's size))
- rem: measured relative to the **document's root** font-size
- vh && vw: % measurement of the viewport's height and width respectively.

