# css-grids-wes-bos
[CSS Grids Course by Wes Bos](https://cssgrid.io/)


## Some Of My Notes From The Course

* `display: grid;`
    * Turns a parent element into a grid.
    * Rows and grids together are called “Tracks"
        * Tracks are numbered in Firefox by the lines that start/stop them, so there will always be one more line number then actual columns and rows.
    * Lines in the grid meaning…
        * Long dashed lines are tracks that were created by us, such as specifying a number of columns
        *  Fainter dotted lines signify implicit tracks that we did not make manually. For example these would be rows that computer made, to fit the items that could not be stored in the specified columns.

* `grid-gap: 20px;`
    * This adds 20px of margin around each grid item. 

* `grid-template-columns: 100px auto 200px;`
    * This divides the grid’s content into 3 columns, with the middle one being fluid.
    * The more values we add, the more columns will be added.
    * Functions can be added as well, such as repeat(5, 200px)

* `grid-template-rows: 100px 200px;`
    * This will create two rows, with the first one being 100px tall and the second being 200px tall. 

* **grid-auto-flow:** this will let you change the direction of elements.
    * `grid-auto-flow: row;` is the default and will stack elements 
    * `grid-auto-flow: column;` will place elements horizontally 
    * This is very similar to flex-direction

* `grid-auto-columns: 200px` This will give implicit (not explicitly defined by us with grid-template-columns) will get this size
    * Example: If I explicitly define sizes for columns 1, 2 and 3 — then GAC will apply to columns 4+

* `grid-auto-columns: 200px` This is the same as above, but for rows.

* **Fractional Units (fr)** this takes into account any grids or used spacing and then only takes up the space that is left. 
    * Example: `grid-template-columns: 100px 2fr 1fr;`
        * This makes the first column 100px, the second column 2 times the space remaining as the third column. 
* **`auto` unit:** This auto fits a row or column to the largest sizes element 

* **`repeat()` Grids** This lets you pass an operator and any number of units into a property and it will repeat that unit(s) for the amount of times specified
    * `grid-template-columns: repeat(2, 1fr);`
        * This will create two columns equally spaced
    * `grid-template-columns: repeat(4, 1fr 2fr);`
        * This will create 8 columns, with every second column being twice as large as the first

* **Spanning:** This lets us specify a child element of a CSS grid to to take up or "span" a specific amount of columns.
    * `grid-column: span 2;`
        * This will take up two columns of space.
        * It will push any items to the right of it over and if there is no more space in the row these items will move to the next row.
    * `grid-row: span 4;`
        * Same as above, but this is for taking up rows.
    * To specifically tell the item where to start and end its span, we can specify the following two properties.
        * `grid-column-start: 2;`
            * This will start it at the second column.
        * `grid-column-end: 5;`
            * This will end it 3 columns down at the 5th column.
        * `grid-column: 2 / 5;`
            * This is the short hand of the above two properties.
        * `grid-column: 2 / span 5;`
            * This is the short hand to start at column two and span for 5 columns.
        * `grid-column: 2 / -1;`
            * This is the short hand to start at column two and span for however many columns are added.
            * This is like saying "go 100% of the remaining grid "
    * `grid-row: span 3;`
        * This works the same way as the columns.
    * To use the 1 / -1 trick for both rows and columns, the child item needs the parent container to have a specified grid-template-rows property. 
    * To force an element take up the whole grid, the columns and rows should both be specified with 1 / -1

* **Auto Fill Property**
    * `grid-template-columns: repeat(auto-fill, 150px);`
    * This tells the grid to auto add as many columns as there is room for, given the grid's width. The smaller the grid, the less columns will be there and the rest will wrap.
* **Auto Fit Property**
    * `grid-template-columns: repeat(auto-fit, 150px);`
    * This tells the grid to fit elements to the grid. It will stop the grid width as specified.
* **Min Max Property**
    * `grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));`
    * This lets you specify a min and max value, and pairs well with an auto-fit or auto-fill.  
    * With auto-fit, the minmax() lets you auto size the content to the width, but then wraps the content on smaller screens.
* **Fit Content Function Property**
    * `grid-template-columns: fit-content(100px) 150px 150px 150px;`    
    * This forces a column to be the amount of space that is specified in the function. Meaning no matter how much space there is in the grid, that column will always be 100px.
* **Area Naming**
    * `grid-template-areas:  
    "sidebar-1 content sidebar-2"  
    "sidebar-1 content sidebar-2" 
    "footer footer .";`
    * This lets you name areas, as you would columns and.
    * `grid-area: sidebar-1;`
        * This then lets us specify how far content should span, based on how wide the area name has been specified.
        * With media queries this lets you dynamically change the layout, by just changing the area name positions for the containers on mobile.
* **Grid Auto Flow**
    * `grid-auto-flow: dense;`
    * This can be added to the parent container and finds where most of the empty spots are in the grid and tries to fill it as best it can with the available items.