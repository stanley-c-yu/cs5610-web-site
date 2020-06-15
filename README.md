# Chapter Notes

## Chapter 3: React Components

In Chapter 3, we learned that React can be used to create things in the UI called components, and that the aggregation of all these components are used to create interesting UI for users.  We learned that in React, we create React Classes that we can later instantiate and render as React Components.  These components can be composed by nesting to create complex displays.  These components can be passed data either through the use use of special object variables called Properties or "props", or through the use of so-called Children, written in code as "props.children".  Finally, we learned about Dynamic Composition, and how it is used to programatically generate componenets from an array, which elimnates the need to hard code the information into the parent component by hand.  

## Chapter 2: Hello World

In the first section of Chapter 2, titled Server-Less Hello World, we learned how to create a simple web page that could be displayed locally on my own browser.  We started by creating an HTML file titled “index.html”, where we called upon the React Core Module and the ReactDOM Module within the HTML file itself using the “<script>” tags.  The React elements are JavaScript objects that can create and then render things we want to display on the web page, which we used within a “<div>” to display “Hello World!” in the browser.  

For the next section, titled JSX, we learned that React has a markup language similar to HTML called JSX, which is short for JavaScript XML.  We learned that we can include JSX within out HTML file, and then use a compiler called Babel to take JSX snippets and transform then into regular JavaScript, which is important because the JS engine in browsers don’t understand JSX.  Once translated, we can then create things we want to display and render them using React elements.  

Section three, titled Project Setup introduces us to nvm and npm.  We learned how to use Node Version Manager, or “nvm”, to install Node.js, and that it can be used to switch between different versions of Node.js.  In addition, we learned how to initialize a project in its own directory using Node Package Manager, or “npm”, and that it’s important to do this for each project.  Initializing npm for each project means that for all packages used for a particular project, their versions remain localized and specific, such that they won’t interfere with other projects on the same computer in different directories.  We then used npm in the terminal to install Express.  

![ch03](/readme_images/Ch03.png)
