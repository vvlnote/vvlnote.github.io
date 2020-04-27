---
layout: post
title:      "Note about CSS - part II"
date:       2020-04-26 20:31:07 -0400
permalink:  note_about_css_-_part_ii
---


In my [previous note](https://vvlnote.github.io/note_about_css_-_part_i), based on [w3schools](https://www.w3schools.com/css/css_selectors.asp), CSS selectors can be catogorized into 5 categories, they are:  
* **Simple Selector**: this has been introduced in my [previous note](https://vvlnote.github.io/note_about_css_-_part_i)  
* **Combinator  Selectors **   
   * Descendant combinator   
      The  (single space) cominator selects nodes that are descendants of the first element.    
			
		Combines 2 selectors such that elements matched by the 2nd selector are selected if they have ancestor (parent, parent's parent, grand grand parents, etc) element matching the first selector.  
		Syntax:   
		A B  
	
	Reference: [Descendant cominator](https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_combinator)   
			
   * Child combinator  
      The **>** cominator selects nodes that are direct childern of the first element.  

		Elements matched by the 2nd selector must be the immediate children of the elements matched by the 1st selector.   
		Syntax:  
		A>B  
		B is the direct children of A.  
		Reference: [Child cominator](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_combinator)  
		
   * General sibling combinator  
      The **~** combinator selectos sibling.   
			
		Elements matched by the 2nd element follows the 1st (though not necessarily immediately) element, and both elements share the same parent.  
		Syntax:  
		A ~ B  
		Reference: [General Sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/General_sibling_combinator)  

   * Adjacent sibling combinator  
     The **+** cominator selectors adjacent siblings.    
		 
	 Element that matched 2nd element directly follows the first element, and both share the same parent.  
	 Syntax:  
	 A + B  
	 all the B elements that directly follow A element.  
	 Reference: [Adjacent Sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_combinator)  
* **Pseudo-class selectors **    
  
	The **:** pseudo allow the selection of elements based on state information that is not contained in the document tree. 
	Pseudo-class is a keyword added to a selector that specifies a special state of the selected element(s). 
	
	Ex:   
```
	a:hover {
	     color: orange;
			 }  
```
			 
   it means that when the mouse move to the a element, the text in the link will turn orange color, however, when the mouse leaves the  a element, the text will turn into it original color.   
	 
	 Standard pseudo-classes:  
	 :active, :checked, :default, :defined, :disabled, :empty, :enabled, :first, :first-child, :first-of-type, :focus, :focus-within, :host,  :host(),  :hover, :indeterminate, :in-range, :invalid, :lang(), :last-child, :last-of-type, :left, :link, :not(), :nth-child(), :nth-last-child(), :nth-lsat-type(), :nth-of-type(), :only-child, :only-of-type, :optional, :out-of-range, :read-only, :read-write, :required, :right, :root, :scope, :target, :valid, :visited  
	 
	 for the example of each pseudo-class selector, please refer to [Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
	 
* **Pseudo-elements selectors**    
  The **::** pseudo represent entities that are not included in HTML.  
	
	Pseudo-element is a keyword added to a selector that lets you style a specific part of the seleclted element(s).  
	Note: a selector can only have one pseudo-element, and this pseudo-element must appear after the simple selector in the statement.  
	
	Standard pseudo-elements:  
	::after, ::before, ::cue, ::cue-region, ::first-letter, ::first-line, ::selection, ::slotted()  
	
	for the examples of each pseudo-element selector, please refer to [Pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)

* **Attribute selectors**


note: the general rule of selectors:  
[CSS Seelector Reference](https://www.w3schools.com/cssref/css_selectors.asp)
