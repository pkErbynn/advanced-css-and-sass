# Nexter 
A fictional company called "nexter" which sells luxury home across the world
- This project heavily focuses on **CSS Grid Layout**

## Demo
...
## What & why css grid
    - brand new module that brings a 2-dimensional grid sys to css for the 1st time
    - replaces float layout, using less and more readable + logical css and html
    - works perfectly well with _Flexbox_ - best for 1D layouts
    - completely changes the way we envision and build 2D components and layouts
    - easily implementation even without framework like Bootrap, etc

## Css Grid terminologies
    - grid container
    - grid items 
    - grid column
    - grid row

    - grid line
    - grid gutter
    - grid area 

### Grid properties overview
- grid-template-column: <X>fr, repeat(), %
- positioning: 
    - grid-row-start/end
    - grid-column-start/end
- spaning grid items:_
    - increase grid-row-start/end & grid-column-start/end values
        - eg: `2 / span 3`
        - -1 === till the end
    - can have multiple grid items in same cell, *stacking*
    - stack order with _z-index_
    - can be used to create animation effects
- Ways of positioning grid: using...
    1. grid line numbering (as default reference)
    2. grid line naming...[name], defined with grid template 
    3. grid area naming...using `grid-template-areas`...perfect for small layout
- Implicit/Explicit Grids
    - Explicit: manually defined and declared
        - uses `grid-template-rows/columns`
    - Implicit: off-grid, out of manually defined grid
        - `grid-auto-rows`...set off-grid sizes
        - `grid-auto-flow`...fill additional grid in row/column...`dense` - fills out all grid without leaving a grid placeholder empty
        - used when grid size isn't known beforehand. eg. loading data from server without knowing how many they are but can be controlled 
- Aligning Grid Items
    - vertical align: `align-self`, `align-item(s): [start/center/end/stretch]`
    - horizontal align: `justify-self`, `justify-item(s)`   
- Aligning Tracks:
    - horizontal: `justify-content`
    - vertical: `align-content`
- `min-content / max-content / minmax()`:
    - `max-content`...wide as much as possible to fit its content WITHOUT line break
    - `min-content`...adjust to accomodate content w/ line breaks
    - `minmax()`...help content to grow in its grid cell
    - example
        ```
        grid-template-columns: max-content 1fr 1fr min-content;
        grid-template-rows: repeat(2, minmax(150px, min-content));
        ```
- `auto-fill / auto-fit`
    - adoptive and flexible 
    - help to achieve responsiveness
    - help not to use any media queries
    - rewatch
    
### Adding a build process
A sequence of task that happens after a feature/product is completed and the resulted file(s) that is(are) ready for production env.
Example is the  `package.json` script
    - compile -> concatenate (with font icon) -> prefix -> compress
