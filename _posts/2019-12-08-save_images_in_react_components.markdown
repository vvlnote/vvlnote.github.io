---
layout: post
title:      "Save images in react components"
date:       2019-12-08 21:57:58 +0000
permalink:  Images inside React App
---


My react app needed to display images on one web page. We all know how to import images inside the React componet by using <img src={image_name} />. However, if those images are not from the internet, but you like to save them with your app, where should those images be saved? And how to retreive them to display on the web page?

After looked through the tech web sites that could find, it seems suggested me to store all the images under the public folder inside React app.


## Images are located under react project /public folder
I use the folloiwng method to dynamically load the images into one component:

		render(){
		const imagePath = require.context('../../public/dishImages', true);
		let imgsrc = this.findImgSrc();
		let image = imagePath(`./${imgsrc}`);
		return(
		    <div>
		    	<img src={`${image}`} />
		    </div>
		)
		}
require.context() this function allow you to create your own context.
the syntax of require.context is as following:
require.context(directory, useSubdirectores, regExp= /^\.\/.*$, mode="sync');
This funtion allows you to pass in a directory to serach. a flag indicatin whether subdirectories should be searched too, and a requlare expression to match files against.

The code: const imagePath = require.context('../../public/dishImages', true);
It means that a context with files under the relative directory (../../public/dishImages, this is directory contains all the images that you were referring to.) can be access by imagePath.

One more thing I would like to mention was that the a particulare image was dynamically loaded into to web page based on the id that passed down from the parent component. I have a component to keep all the images with name and id in an array that match with the names of images under public/dishImages folder. So the component would load the image that match with the id that component be assigned by its parent component. this is "let imgsrc = this.findImagSrc(); to get the image name. and combined imagePath + imgsrc to passed to <img src={$image}/> to load the right image for this compoenent. 
