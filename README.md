# advanced-css-and-sass

Taking my CSS skills to the next LEVEL!

- consists of 3 projects
    - natour (float heavy)  ...a nature tour site simulation
    - trillo (flexbox heavy) ...fictional all-in-one booking app, user can book hotel, flight, car
    - ??? (grid heavy)

# Natour
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

element:psuedoclass....eg. btn:hover
element::psuedoelement....eg. btn::after

</pre>
box-sizing: border-box...padding, border part of declared **width** or **height**


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

### Inheritance
- some specific declarations are passed from parent to children
- text declarations are inherited: font-family, font-size, color, etc
- computed value of a property is what gets inherited, not the declared value
- every property is set, if not declared, it is inherited
- "inherit" keyword forces inheritance on a property
- "initial" resets property to its initial value 

## Positioning schemes
- Normal flow: 
    - relative position by default
    - not floated
    - not absolutely positioned
    - elements being in normal flow, laid out according to their code/source order
- Float:
    - element removed from the normal flow
    - text and inline elements will **wrap around the floated element**
    - container's height not adjusted, fixed with clear-fix
    - float = right or left
- Absolute:
    - element removed from the normal flow
    - no impact on surrounding elements
    - top, bottom, right, left to offset from relative element
    - absolute / fixed
    - can overlap and form stack.....z-index arranges that 

## CSS architecture, components and BEM  
* Think -> Build -> Architect
* Think: modular bulding blocks, layout, reuseable and independent components
* Build: BEM (Block Element Modifier)
    * .block {}
    * .block__element {}
    * .block__elmenet--modifier {}
* Architect: logical file and folder structure

## SASS 
* SASS is a CSS preprocessor that extends CSS and adds power and elegance to the basic language
    * Preprocessor: processing by compiling sass source code into css first.
    * SASS Source Code -----SASS Compiler----> (into) Compiled CSS code
        * The website has no idea that css is written in SASS, only the output (css code compiled) 

* Features
    * variables, nestings, operators, 
    * mixins (block of reusable code, multiple lines), 
    * functions (similar to mixins but returns result), 
    * extends 
    * partials & imports, control directives
    * easy comment syntax - //

* 2 SASS Syntaxes
    1. SCSS: curly braced
    2. Sass: no curly braces, only indentation

### Sass Usage
// html
```html
<ul class="navigation">
    <li><a href="#">about us</a></li>
    <li><a href="#">pricing</a></li>
    <li><a href="#">contact us</a></li>
</ul>
```

// sass
```scss
$color-primary: blue;
$color-text-primary: #fff;

@mixin style-link-text($col) {
    text-decoration: none;
    color: $col;
}

@function divide($a, $b){
    @return $a / $b;
}

.navigation {
    list-style: none;
    background-color: $color-primary;
    margin: divide(60, 2) * 1px;  // 30px;

    li {    // .navigation li
        display: inline-block;

        &:first-child {     // .navigation li:first-child
            margin: 0;
        }

        a {     // .navigation li a
            //text-decoration: none; (mixined)
            //color: $color-text-primary; (mixined)

            @include style-link-text($color-text-primary);

            &:hover {       // .navigation li a:hover
                text-decoration: underline;
            }
        }
    }
}
```

## NPM and Node ecosystem
- Node: 
    - Js server-side dev tool,
    - also, tool for **local web dev**
- NPM:
    - cmd tool for devs to **install and manage packages locally**
    - contains **open-source tools, libraries and frameworks** for modern web dev
- Usage:
    ```cmd
    $ npm init (creates package.json file)
    $ npm install <pkg> --save (persist in package.json's dependencies block + node_module creation(including supported files))
    $ npm install <pkg> --save-dev (persist in package.json's devDependencies block + node_module creation(including supported files))
    $ npm install <pkg> -g (install globally on pc, not seen in package.json)
    $ npm install (installs all mode-modules)
    $ npm uninstall pkg --save
    ```
- Script block: Compiling sass locally:
    ```script
    "script": {
        "compile:css": "node-sass input output",
        "<script-name>": "<node-pkg-dependency> <args>" or usage...makes use of installed dependencies in the package.json
    }
    ```
    - Script run:
    ```
    $ npm run <scrip-name>
    ```

## CSS Architecture w/ Sass
- Used in mult-page big web project 
- uses `imports` and `partials`<br>

file structure

- /sass 
    - /abstracts
        - _variables.scss
        - _mixins.scss
        - _functions.scss
    - /base
        - _animation.scss
        - _base.scss
        - _typography.scss
        - _utilities.scss
    - components
    - layout
    - /pages
        - _home.scss

## The 3 basic principles of responsiveness design
1. Fluid grids and layout
    - Use % instead of px for layout lenght
    - Layout types
        - Float
        - Flexbox
        - Grid
2. Flexible images
3. Media queries


## Custom grid w/ float
Grid - a design sys used to build consistent interfaces.

## Section Concepts
what you will learn...
- Feature section
    - creating skewed section
    - direct child selector use-case
- Tour section
    - card rotation
    - perspective in css
    - backface-visibility property
    - using background blend modes
    - box-decoration-break
- Feedback story section
    - text flow around shape wit 'shape-outside' and 'float'
    - apply filter to img 
    - bg vid covering entire section
    - using 'object-fit' prop
- Form book section
    - solid-color gradient
    - adjacent sibling selectors
    - '::input-placeholder' pseudo-element
    - :focus, :invalid, :placeholder-shown & :checked pseudo-class
    - custom radio buttons
- Navigation section
    - "checkbox hack"
    - custom animation timing function using cubic bezier curves
    - solid-gradient animation
    - transform origin
- Popup section
    - equal-height boxes using 'display: table-cell;'
    - css text columns
    - word hyphenate
- Advanced img responsive
    - allowing browser to decide the best img to download
    - using 'srcset', w/ descriptors and size attribute of img element
    - 'screen only' media queries
    - @support() 
    - special style tailored to hoverless touch screens
    - custom text highlight
    - build pipeline script


## Responsive Design Strategies - Media Queries
- MQ: tools to override specific part of css for specific viewport width
- Two forms
    - Desktop first (preferred, but depends)
        - uses max-width
        - indicates the max width at which media query still applies
    - Mobile first approach
        - uses min-width
        - indicates the min width at which media query starts to apply
        - queries to stay away from the small size, working for only bigger screens
        - reduces app to the absolute essentials, striping away unnecessary things 
            - to end up in a smaller, faster product
        - Pros
            - 100% optimizesd experience for mobile
            - web app with the absolute essentials
            - smaller,faster and more efficient product
            - prioritizes content over aesthetic design
        - Cons
            - desktop version might feel empty
            - less creative freedom, diff to create distinct prod
            - clients are used to see desktop version as prototype
            - more difficult do develop
        - nb: have both in mind which ever is chosed

### Breakpoint selection
- Bad: specific target to popular screens
- Good: screen range target (preferrable)
- Perfect: design breaks, fix css while expanding width, more difficult

### Media query pixel spectrum
Basically: 600px, 900px, 1200px, 1800px <br><br>

0 - 600px: ............   Phone   <br>
600px - 900px: ........   Tablet portrait <br>
900px - 1200px: .......   Tablet landscape <br>
[1200 - 1800px]: ......   where normal style apply [Desktop-first] <br>
1800px +: .............   Big desktop <br>

## Responsive Design Strategies - Responsive Image
The goal of responsive images is to serve the **right image** to the **right screen size** and device, in order to avoid downloading unnecessary large images on small screens 

### Module application
Some of the images are applied either via html (img tag) or css (bg-image)

### The 3 Use-cases
1. Resolution switching: 
    - decrease img resolution on smaller screens
    - nb: 1px == 2 physical pixels
    - specifies and depends on the width descriptor
    - application: line #74 (in .html)

2. Density switching:
    - reserve to half the img resolution on @1x-screen (ie. low resolution screen, 2x for high res)
    - serve a larger version of img for higher res screens and smaller version of same image for smaller res screens
    - depends on screen resolution
    - uses `srcset` and has density descriptor (of 1x, 2x)...eg, `<img srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x" ...`
    - application: line #371 (in .html)
3. Art direction:
    - different img on smaller screen
    - (img content is preserved but img is different)
    - depends on screen width...diff img for diff viewport width
    - application: line #368 (in .html)


## Demo
* Header <br> <br>
![Header demo](https://j.gifs.com/57VlGA.gif)

* Image composition <br> <br>
![Image composition demo](https://j.gifs.com/08E2KN.gif)

* Feature and card <br> <br>
![Feature and card demo](https://j.gifs.com/RlkMzV.gif)

* Story <br> <br>
![Story](https://j.gifs.com/x68VDl.gif)

* Form <br> <br>
![Form](https://j.gifs.com/QkjNwG.gif)

* Form and footer <br> <br>
![Form and footer](https://j.gifs.com/57Vl5Y.gif)


# Trillo
## Flexbox concepts
- Flex container
    - its display set to flex
    - has the ff properties
        - flex-direction
        - flex-uurap ...uuraps overflouun items to next line/rouu
        - justify-content ...houu items uuill be positioned (horizontally depending on the flex-direction) to the main axis
        - align-items ...houu items uuill be positioned (vertically depending on the flex-direction) to the cross axis
        - align-content ...houu it positions rouus vertically across main axis
- Flex items
    - found inside the container
    - can be aligned in main (horizontal) or cross (vertical) axis
    - has the ff properties
        - align-self...aligns a particular / ONE item in the flex-container vertically...overrides container's align-items value
        - order...the order of AN item depending on 0 > value < 0 is set. each item as 0 order value by default 
        - flex-grouu...expands item as much as it can occupying more space...depends on other nearby items value (1,2,3..)
        - flex-shrink...0 == non-shrinkable (default), 1 == shrinkable
        - flex-basis...sets flex uuidth basically
            - all together shortened as
                - fleuu: grouu shrink basis; ...eg flex: 0 1 20%;

## Architecture 
Going uuith simple architecture unlike Natour

- /sass 
    - _base.scss
    - _layout.scss
    - _components.scss

## Useful resource links
* bennettfeely.com/clippy
* linea.io
* unsplash.com
* coverr.co
* gs.statcounter.com
* sizzy.co ...for responsive testing
* caniuse.com
<br>

// Need To
- Review last 3 vids