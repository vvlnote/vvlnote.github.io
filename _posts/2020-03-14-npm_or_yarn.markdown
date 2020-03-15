---
layout: post
title:      "npm -i  or yarn -add "
date:       2020-03-14 23:27:32 -0400
permalink:  npm_or_yarn
---


Since I am continuing on learning new things about web development, I look up so many tech docs about new package, and new way to implmenet the Web app. Recently, I was trying to download the packages for my side project. I saw some engineers use  **npm -i** to download and install the needed packag, however, I saw a lots of engineer using **yarn add** to install the package. I am curious what are the difference between these two.  

The first thing I read is : The most 2 popular package managers in the ecosystem as of today are **npm** and **yarn**.  
note: npm is an acronym for *Node Package Manager.*

### A breif introducation of npm and yarn
* **npm**  
It is written by JavaScript and developed by Isaac Z. Schlueter on January 12, 2010.   
*   **yarn**  
It is written in JavaScript and developed and released by Facebook in October, 2016.  
It is meat to replace the existing workflow for the npm client or othere package managers.  
Facebook engineers attempt to permanently fix some consisitency, security, and performance issues that they   have experienced with npm as the size of codebase and staff grew, 

### npm -i

* Manage packages that are local dependencies of a particular project.  
   * in one comand, npm can install all the dependencies of a project through the **package.json** file.  
   * provides version-bumping tools for developers to tag their packages with particular version.  This information can be specified in **package.json** file.  
   * npm also provides the **package-lock.json** file, which has the entry of the exact version used by the project after evaluating semantic versioning in package.json.  This improvement would avoid that different machines with same package.json file having different version of a package installed, prossibly introducing bugs.
*   Serial installation of packages. Package installation involved a series of tasks.  npm executes installation per package and sequentially, meaning it will wait for a package to be fully installed before moving to the next package. 
*   Requires network to install packages.  
*   **npm -i** installs dependencies from the package.json file, and allow you to add new packages. 

### yarn -add
* It is a new CLI client that fetches modules from the npm registry.  
* It generates yarn.lock file by default. This file is to avoid package version mis-matches, and exact installed version is recorded in this file.   Every time a module is added, yarn create (or update) a yarn.lock file.  This way you can gurantee antoher machine installs the exact same package, while still having a range tof allowed versions defined in package.json. 
**Note**:  
Starting from npm version 5,  npm would generate **package.json** file and **package-lock.json** file by default. **package-lock.json** file servers the same purpose of  **yarn.lock** file.  
* Parallel installation. **yarn**  installs package in parallel, it makes the package installation faster than npm installation since it is serial installation.  When the package has big amount of dependencies that need to be installed, the speed difference will be shown significantly.  
* **yarn install** only installs the dependencies listed in yarn.lock or package.json, in that order.  


## Conclusion  
After reading all the documents about yarn - add and npm -i, for myself, I have not gotten a chance to try out yarn at this moment. And the size of my side project is not that big, I did not need to install so many packages to work on, I properly will still use npm. However, for learning purpose, I will use yarn myself in the future to experience the differences. 



### Reference
This summary is based on the following documents. If you need more detail information, please click on the the following links:  
[YARN vs NPM (vs pnpm) in 2019 : compariosn and verdict](https://www.ryadel.com/en/yarn-vs-npm-pnpm-2019/)  
[Yarn vs npm: Everything You Need to Know](https://www.sitepoint.com/yarn-vs-npm/)  
[Why Developers Are Moving to Yarn](https://circleci.com/blog/why-are-developers-moving-to-yarn/)  
[NPM vs Yarn Cheat Sheet](https://shift.infinite.red/npm-vs-yarn-cheat-sheet-8755b092e5cc)  
[npm vs Yarn](https://stackshare.io/stackups/npm-vs-yarn)
