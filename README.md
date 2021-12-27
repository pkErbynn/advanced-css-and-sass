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

## Useful resource links
* bennettfeely.com/clippy

## Custom grid w/ float
Grid - a design sys used to build consistent interfaces.
