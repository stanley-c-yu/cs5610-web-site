# Chapter Notes
## Chapter 4: React State
### What are states?
In React, React Components can store information in data structures known as "States".  These React States can be manipulated to change what Components display.  Previously, we were using immutable "Properties", or `props` to hold data for the Components to display, which, unlike "States", can't be manipulated by the user.  

### Initial State:
Each React Component is represented by its own Class.  The Class' "State" is captured by a variable for that Class called `this.state`, which is an object consisting of one or more key-value pairs.  React doesn't specify what needs to go into the State, but it is useful to store anything in the State that affects the rendered view and that can change to a Event, which is typically triggered by the user.

### Async State Initialization:
Usually the data for the State isn't available statically to begin with.  Typically, we'll have to query the server using an API call, which means an Asynchronous Call is needed.  As a stand in, we use timer method within in the component to stimulate it.  We'll also need to pass the constructor an empty array of data to begin with.  

Note that the constructor creates the component first, and that rendering happens only when we call upon the component, so we need to make sure that the data is loaded only after the component is created by using a Life Cycle Method, which in this is `componentDidMount()`, which comes after the construction part in the component's class.  

More specifically, its description states, "This method is called as soon as the component's representation has been converted and inserted into the `DOM`.  A `setState()` can be called within this method".   

### Updating State:
In this section, we added a method to the Issue Table Class that adds a new issue.  

This method takes an "issue" as an argument, and adds that issue plus an auto-incremented ID to the Table of Issues in the Issue Table Class.  It also adds the creation Date, which is automatically set to today's date.  

There's a specific way we need to use to actually push these changes to the Issue Table for good.  Firstly, we need to make a copy of the array using JS' `slice` method.  

For now, we're using a hard coded issue to be added upon the expiry of a timer, instead of actually having to do something like develop a UI to use to add a handwritten issue.  It's appropriately titled "Samples Issues", and is created after the initial array of Issues are defined that are first used to populate the empty Issue Table.  

Reminder: Use `npm run watch` to activate the "Watcher", which will automatically update the app if the page is refreshed and changes have been made.  Use `npm start` to start the app.

### Lifting State Up
In this section, we move the code responsible for Creating Issues from its location in the Issue Table Class to the Issue Add Class, which is a more appropriate place for it.  

However, the code responsible for executing the creation of initial issues is defined in the same class as the method that is used to do so, the Create Issue Method, which is also within the Issue Table Class to begin with.  Because of this, we also need to move this method to a Common Parent Class that can pass it on to child classes.  In this case, our Common Parent is the Issue List Class, which will propagate information down to the Issue Add and Issue Table Classes.  

We'll need to start by moving the state to "Issue List" and the methods employed to load the initial state.  Currently, the state is being defined by Issue Table Class, and the methods `componentDidMount()`, `loadData()`, and `createIssue()` as well, which all need to be moved to the Issue List Class.  

By moving the state to Issue List, we leave Issue Table without a state to construct the Issue Row Components from, so instead we'll pass the array of issues from the state within Issue List by using props:

`<IssueTables issues={this.state.issues} />`

Within Issue Table, we will also have to map the issues using props as well.  

We then passed the Create Issue Method to the Issue Add Class from the parent Issue List Class to the child Issue Add Class so that it can be called by Issue Add.  We then call this method using props.  

We need to `bind` the method to the Issue List component before passing it around to make sure its calling data from the lexical scope of Issue List and not Issue Add, which is where we are calling Create Issue.  

### Event Handling
In this section, we removed the placeholder `div` from the Issue Add class and replaced it with a form and button for adding the name of the owner of an issue, plus the title of the issue, to the table of issues.  Because of this, we no longer need the timer that creates an issue from the constructor, so we get rid of the Set Timeout Function.  

To actually handle the submission, we added a new method to the Issue Add Class called Handle Submit, which takes the data filled out in the form and adds them to a data structure titled Issue that is then fed as an argument to the Create Issue Method, which in turn adds that to the table of issues.  

At this stage, we no longer need our sample issue, so we delete it from the App JSX file.  

![ch04-event-handler](/readme_images/chap-4-event-handler)

## Chapter 3: React Components

In Chapter 3, we learned that React can be used to create things in the UI called components, and that the aggregation of all these components are used to create interesting UI for users.  We learned that in React, we create React Classes that we can later instantiate and render as React Components.  These components can be composed by nesting to create complex displays.  These components can be passed data either through the use use of special object variables called Properties or `props`, or through the use of so-called Children, written in code as `props.children`.  Finally, we learned about Dynamic Composition, and how it is used to programatically generate componenets from an array, which eliminates the need to hard code the information into the parent component by hand.  

![ch03](/readme_images/Ch03.png)

## Chapter 2: Hello World

In the first section of Chapter 2, titled Server-Less Hello World, we learned how to create a simple web page that could be displayed locally on my own browser.  We started by creating an HTML file titled `index.html`, where we called upon the React Core Module and the ReactDOM Module within the HTML file itself using the `<script>` tags.  The React elements are JavaScript objects that can create and then render things we want to display on the web page, which we used within a `<div>` to display `“Hello World!”` in the browser.  

For the next section, titled JSX, we learned that React has a markup language similar to HTML called JSX, which is short for JavaScript XML.  We learned that we can include JSX within our HTML file, and then use a compiler called Babel to take JSX snippets and transform then into regular JavaScript, which is important because the JS engine in browsers don’t understand JSX.  Once translated, we can then create things we want to display and render them using React elements.  

Section three, titled Project Setup introduces us to nvm and npm.  We learned how to use Node Version Manager, or `nvm`, to install Node.js, and that it can be used to switch between different versions of Node.js.  In addition, we learned how to initialize a project in its own directory using Node Package Manager, or `npm`, and that it’s important to do this for each project.  Initializing npm for each project means that for all packages used for a particular project, their versions remain localized and specific, such that they won’t interfere with other projects on the same computer in different directories.  We then used npm in the terminal to install Express.  
