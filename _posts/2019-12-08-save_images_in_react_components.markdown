---
layout: post
title:      "Save images in react components"
date:       2019-12-08 21:57:58 +0000
permalink:  save_images_in_react_components
---


My react project needs to display some images in one component. I am thinking about doing this by the following steps:  

1. the images file is located under react project/public folder, and load into component dynamically  
2. images are stored in the backend database, and can be loaded from backend and display in the component


## Images are located under react project /public folder
I use the folloiwng method to dynamically load the images into one component:

		</>
		const imagePath = require.context('../../public/dishImages', true);
		let imgsrc = this.findImgSrc();
		let image = imagePath(`./${imgsrc}`);
		console.log(image);
		</>

