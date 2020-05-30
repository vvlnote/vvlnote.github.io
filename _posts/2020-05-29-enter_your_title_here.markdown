---
layout: post
title:      "Enter your title here"
date:       2020-05-30 00:33:54 +0000
permalink:  enter_your_title_here
---


I would like to continue my journey about CSS Layout. In my previous, I have introduced flexbox, it is one-dimention layout, you either layout items in column direction or row direction. please refer to [Flexbox](https://vvlnote.github.io/note_about_css_-_part_iv_css_layout).  

### Grids
In this post, I am going to learn about Grid layout. It is two-dimentional layout for the web. The content can be laid out by specify row and column.   

The grid layout is as following:



![grid layout](https://mdn.mozillademos.org/files/13899/grid.png)  

**Terminology:**   
* Grid Container  
   The element where display: grid is applied. 
	 It is the direct parent of all the grid items. 
```
  <div class='grid'>   /* this is the Grid container */
   <div class='one'>One</div>   /* this is the direct child of grid containter, it is grid item */
   <div class='two'>Two</div>    /* this is the direct child of grid containter, it is grid item  */
   <div class='three'>Three</div>   /* this is the direct child of grid containter, it is grid item  */
   <div class='four'>Four</div>   /* this is the direct child of grid containter, it is grid item  */
  </div>  
```  

![Grid](https://webkit.org/wp-content/uploads/grid-concepts.svg)  



* Grid Line  
These lines make up the sturcture of the grid. 
* Grid Track  
  A grid track is the space between two grid lines. 
* Grid Area  
  A grid area is the total space surrounded by four grid line. 
	A grid area may be composed of any number of grid cells. 
	In the picture, the yellow Grid Area is between row grid lines 4 and 6, and column grid lines 4 and 6. 
* Grid Item  
* Grid Cell  
   The space between two adjacent row and two adjacent column grid lines. 
	 It is the single 'unit' of hte gird.
	 In the picuture, the green grid cell is between row grid lines 1 and 2, and column gird lines 5 and 6.  

**Properties for the Grid Container (Parent element)  **  
* display: grid | inline-grid
* grid-template-columns
* grid-template-rows
  
	grid-template-columns and grid-template-rows are used to defined the columns and rows of the grid with space-separated lit of value. The values represet the track size, and the spac between them represents the grid line.
	
	Syntax :    
	`
	.container {
	     grid-template-colums: <line-name> <track-size> <line-name> <track-size> ....
			 grid-template-rows: <line-name><track-size><line-name><track-size>...
	 }
	 `     
	 
	 example:  
	 `
	 .container {
	     grid-template-colums: 40px 50px auto 50px 40px;
			 grid-template-rows: 25% 100px auto;
		} 
		`       
		
![grid](https://css-tricks.com/wp-content/uploads/2018/11/template-columns-rows-01.svg)   

When you leave an empty space between the track values(i.e. 40px, 25%, auto, etc...) the grid lines are automatically assigned positive and negative numbers as shown on the picture above.  

Note: <track-size> can be length (40px, 50 px...) or a fraction of the free space in the grid (**fr** unit).  

* grid-template-areas  

  Example:   
	
```
.item-a {
  grid-area: header;
} 

.item-b {
  grid-area: main;
}

.item-c {
  grid-area: sidebar;
}

.item-d {
  grid-area: footer;
}

.container {
  display: grid;  
  grid-template-columns: 50px 50px 50px 50px;  
  grid-template-rows: auto;  
  grid-template-areas:   
    "header header header header"  
    "main main . sidebar"  
    "footer footer footer footer";  
}
```

![grid-template-areas](https://css-tricks.com/wp-content/uploads/2018/11/dddgrid-template-areas.svg)  

Note: `"main main . sidebar" `  , the . (a period) indicate an empty grid cell. 

* grid-tempate:  
   This is a shorthand for setting grid-tempalte-rows, grid-template-colums, and grid-template-areas in a single declaration.  
	 
	 Syntax : 
	 
	 `
	    .container { 
			   grid-template: grid-template-rows / grid-template-columns;
			}
			
	 `
	 
* gap, grid-gap:  
   These are shorthand for row-gap, and colum-gap.  
	 
	 Syntax: 
	 `
	   .container {
		    gap: <grid-row-gap> <grid-column-gap>;
		}
	 `  
	 Note: if no row-gap is specified, it's set to the same value as column-gap.  
	 
* justify-itmes: 
  This is for aligning grid items alogn the inlin(row) axis. This value applies to all grid items inside the container.  
	
	Syntax:  
	`
	    .container {
			  jusity-items: start | end | center | stretch;
		}
	
	`  
	
	start: aligns grid items in the start edge (left side) of the cells.
	end: aligns grid items in the end edge (right side) of the cells.  
	center: aligns grid items in the center of the cells.  
	stretch: fills the whole width of the cell (this is the default value of justify-items).  

	 
* align-items:  
  This is for aligning grid items along the column axis). This value applies to all grid items inside the container.  
	
	Syntax:  
	`
	   .container {
		    align-items: start | end | center | stretch;
		}
	
	`  
	start; aligns grid items in the start edge (top) of the cells.  
	end: aligns grid items in the end edge (bottom) of the cells. 
	center: aligns grids items in teh center of the cells.  
	stretch: fills the whole height of the cell (this is the default value of align-items).  
	
* place-items:  
   This is for setting both the align-items and justify-items properties in a single declaration.  
	 
	 Syntax:  
	 `  
	    .container {
			  place-items: <align-items> / <justify-items>;
		 }
	 
	 `  
	 Note: if the second value is omitted, the first value is assigned to both properties.   
	 

When the total size of the grid is less than the size of the grid container. This could happen if all the grid items are set to fixed size like px. 
In this case, the following properties can align the grid within the grid container. 

* justify-content  
  This property algins the grid along the row axis.
* align-content.  
  This property algins the grid along the column axis. 
* place-content  
  This property sets both align-content, and justify-content in a single declaration.  
	
	Syntax:   
	`
	    .container {
			    place-content: align-content / justify-content;
			}
	
	`   
	
	Note: if the second value is omitted, the both properties are asigned to the first value.  


* grid-auto-columns
* grid-auto-rows  
   These two properties are also known as implicit grid tracks. 
	 Implicit traks get created when there are mot grid items than cells in ghe grid or when a grid item is placed outside of the explicit grid.  
	 
	 Syntax:  
	 
	 `
	    .container {
			    grid-auto-columns: track-size ...;
					grid-auto-ros:  track-size...;
			}
	 
	 `  
* grid-auto-flow  
   If there grid items are ot explicitly place on the grid, the auto-placement algorithm will be preformed to automatically place these items. 
	 This proprty controls how the auto-placement algoright works.  
	 
	 Syntax:  
	 
	 `
	     .container {
			    grid-auto-flow: row | column | row dense | column dense;
			}
	 
	 `  
	 row: put the non-specified grid items to fill the rows, adding new rows as necessary (default).  
	 column: put the non-specified grid items to fill the columns, adding new columns as necessary.
	 dense: to fill holes earlier in the grid if smaller grid items come up later.  This value changes the visual order of the grid items and might cause them to appear out of order.  

* grid  
  This property is the shorthand for setting grid-template-rows, grid-etmplate-columns, grid-template-areas, grid-auto-rows, grid-auto-columns, and grid-auto-flow. 


**Properties for the Grid Items:  **  

* grid-column-start  
* grid-column-end  
   Spceify how many columns this grid item would cross  
	 
* grid-row-start  
* grid-row-end  
   Spcify how many rows this grid item could cover   
	
    "span" is used to declare the grid item  will span across the provided number of grid tracks or until it hits the next line with the provided name.   
    "auto" is used to indicate auto-placement.

    Note: 
    If no grid-column-end /grid-row-end is declared, this item will span 1 track by default.  
    Items can overlap each other, z-index can be used to control the stacking order.  

* grid-column  
  Shorthand for grid-column-start and grid-column-end.  
* grid-row  
   Shorthand for grid-row-start and grid-row-end.  
	 
* grid-area  
   a. given a grid item a name, so it can be refereced by **grid-template-areas** property of parent element.   
	 b. this can be used as a shorter shorthand for grid-row-start+grid-column-start + grid-row-end + grid-column-end.  


* justify-self  
  This is for aligning a single grid item inside a signle cell along the row axis.
* align-self  
  This is for aligning a single grid item inside a signle cell along the column axis.
* place-self  
  This is setting both the align-self and justify-self properties in a single declaration. 
		
