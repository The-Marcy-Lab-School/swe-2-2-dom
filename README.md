# The Document Object Model

- [Setup](#setup)
- [Before you start](#before-you-start)
  - [CRUD to the rescue](#crud-to-the-rescue)
  - [New testing](#new-testing)
  - [Running Your Own Functions In `main()`](#running-your-own-functions-in-main)
- [Questions](#questions)
  - [Question 1: getMainHeadingText - modify.js (READ)](#question-1-getmainheadingtext---modifyjs-read)
  - [Question 2: getAllMainText - modify.js (READ)](#question-2-getallmaintext---modifyjs-read)
  - [Question 3: setSubtitleText - modify.js (UPDATE)](#question-3-setsubtitletext---modifyjs-update)
  - [Question 4: modifyDivClassList - modify.js (UPDATE)](#question-4-modifydivclasslist---modifyjs-update)
  - [Question 5: add H2 - modify.js (CREATE)](#question-5-add-h2---modifyjs-create)
  - [Question 6: removeOldInfo - modify.js (DELETE)](#question-6-removeoldinfo---modifyjs-delete)
  - [Question 7: makeAlphabet - modify.js](#question-7-makealphabet---modifyjs)
  - [Question 8: makeBio](#question-8-makebio)
  - [Question 9: Make it from scratch!](#question-9-make-it-from-scratch)
- [BONUS - next steps](#bonus---next-steps)

## Setup

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

After cloning your repository, make sure to run the following commands:

```sh
npm i
git checkout -b draft
npm t
```

## Before you start
This is exciting! But a lot has changed! You're now dealing with a GUI and the tests look different, and there are so many new Browser APIs and DOM methods to learn.

We'll guide you through a lot of these changes, but it's important for you to know that our assignments are the *minimum* you should know. There's just so much out there, it's impossible to cover it all here and in lectures. **So when questions ask you to look up extra information, even if they don't use it...learn about those techniques.**

### CRUD to the rescue

As we said, there's so much to learn! So our question prompts are going to tell you what they're looking for, but *also* lead you to resources to check out. 

Maybe you learned what you needed to in lecture, but maybe not! Follow the links to learn what you need.

Feeling overwhelmed by all the things the DOM can do? Whenever you're learning a new piece of tech, a helpful guiding light is CRUD. Can you...
* **C**reate an element? 
* **R**ead data from an element? 
* **U**pdate an element? 
* **D**elete an element?
  
Those actions (and a little more) are going to be our goals today.

Alright, let's get going!

### New testing

Start by opening `modify.html` in your browser. Notice that it loads in the script `modify.js`. Then, open up `src/modify.js` in your IDE, that's the first file you'll be working on.

You'll notice there are no imports or exports, the file just *runs*. What that means is the tests are more general *and* more specific. 
* General because we can't run individual functions right now
* More specific because they'll look for *exact* matches on things like id and class names. 
* Just because your test page looks right, doesn't mean the tests will pass. Read them carefully and make sure you have *exactly* what it's looking for.

Also, we give you `modify.html`, but the tests don't use it directly. We made a copy so we could randomize the data. Use `modify.html` as practice, but do yourself a favor and *do not edit it*. We want to make sure your test html matches it.

### Running Your Own Functions In `main()`
Without imports/exports, we can't call your functions directly in tests. You have to call your own functions and we'll just test the end result, after your function calls have resolved.

In `modify.js`, we've done this for you in the `main` function. This is a common pattern called the "runner pattern". It's where you write small focused functions, and then we call them in a larger function. In this case `main`. 

Mimic this pattern when you create your `index.js` file from scratch! If you open your `index.html` file in your browser, you should see the changes caused by `index.js`. Same thing if you open `modify.html` in the browser, you should see the changes caused by `modify.js`

## Questions

### Question 1: getMainHeadingText - modify.js (READ)

For these first two functions, make sure that your `modify.html` file is open in the browser. Then, inspect the page and look at the **Console** tab. There, you should see the console log output of your first two functions

In the function `getMainHeadingText`, use the `querySelector` to grab the `H1` by it's `id`. Then, console.log the text of the element.

**Helpful Resources**:
* https://www.w3schools.com/jsref/met_document_queryselector.asp (read all of this, its a good one)
* https://www.w3schools.com/jsref/prop_node_textcontent.asp

### Question 2: getAllMainText - modify.js (READ)
In the function `getAllMainText` you'll need to grab *all* the elements with the class of `main-text`. Then, iterate through them so you can build a new string value. The new string value should be all the individual element's text contents, separated only by commas, no spaces! Finally, log that new string to the console.

**Helpful Resources**:
* https://www.w3schools.com/jsref/met_document_queryselectorall.asp
* https://stackoverflow.com/a/3199627
(For this one, look at the **other cases section**, as you can see there are a lot of possible solutions!)

### Question 3: setSubtitleText - modify.js (UPDATE)

The remaining questions will have you directly modifying the content of the `modify.html` page. You should see the content on the page changing as you write your JavaScript code!

Now we're getting into grabbing *existing* elements, and updating them in some way. For this one, use the `setSubtitleText` function, and grab the subtitle `h2` element somehow (maybe `id` or the tag name?). It is currently an empty element so we want you to update its `textContent` to say:

```
This is a subtitle!
```

### Question 4: modifyDivClassList - modify.js (UPDATE)
Editing classes is going to be a *super* common task for you. So, to do this correctly, learn about the `classList` element property (see links below). We'll only need its `add` and `remove` methods here, but it has a lot of useful ones, like `toggle`.

Inside `modifyDivClassList`, we'll edit out `#modify-classes` div. It has 2 classes on it. All we want to do is remove `"bad-class"`, and then add `"new-class"`. That means there will still be 2 classes on it by the time you're done.

`classList` allows us to edit only the class names we need to, without touching the rest. Get good with it!

**Helpful Resources**:
* https://www.w3schools.com/jsref/prop_element_classlist.asp

### Question 5: add H2 - modify.js (CREATE)
In order to create a new element, you should usually follow this pattern:

1. **create** a new element with `document.createElement`
2. **modify** that element however you want
3. **add it to the DOM** with some `append` type method to a parent element

The `addH2` function should append a new `H2` element, with an `id` of `h2-test` and text value of `Another one!`, to the end of the `body` tag.

**Helpful Resources**:
* https://www.w3schools.com/jsref/met_document_createelement.asp
* https://developer.mozilla.org/en-US/docs/Web/API/Element/append

### Question 6: removeOldInfo - modify.js (DELETE)
Finally, there's an old `p` tag that we no longer want. Use the `removeOldInfo` function to grab it by its id `old-info`, and then remove it.

**Helpful Resources**:
* https://www.w3schools.com/jsref/met_element_remove.asp

### Question 7: makeAlphabet - modify.js
Here is where things get interesting. We're going to do a bunch of stuff on this one!

First, notice that there's a data attribute called `num-letters` on our alphabet list `ul` element. Data attributes are a great way to encode more information into a tag. We didn't cover them, but we've included resources to check out.

Here's a *super* quick tutorial

```html
<p id="main-text" data-my-test="hello there">Just a p tag</p>
```

```js
const p = document.querySelector('#main-text');
console.log(p.dataset.myTest); // logs: hello there
// notice how the `data-my-test` attribute was camel-cased to `myTest`
```

And here's [*everything* you'd ever need to know about data attributes](https://css-tricks.com/a-complete-guide-to-data-attributes/#attributes-javascript), focus on part 4, which is the JS part.


Your job is to:
* read from the data attribute using JS to get the number of letters we want to add.
* Then, using our "create > modify > add" pattern from question 5, loop through and add `li`s with text content like: `A is letter #1 in the alphabet`. 
* No need to put `id`s or `class`es on the `li`s. 
* The `li`s *must* be children of the `#alphabet` `ul` tag.

This one is tricky, so we'll be helpful. If the dataset attribute is 3, then the list in the html would print:

```
A is letter #1 in the alphabet
B is letter #2 in the alphabet
C is letter #3 in the alphabet
```

Remember, each one of those lines is in an `li` tag.


### Question 8: makeBio
Ok, so for dynamic information or user-entered info, the create, update, add pattern is safest. However, what if you have a big blob of HTML that *you* know is safe, and you want to insert it? Try the `.innerHTML` property.

The `makeBio` function should set the inner html of the `#my-bio` div to be this exactly:

```html
<h2 id="bio-heading">About Me</h2>
<p>My name is Zo and I like to learn cool new things</p>
<h3 id="hobby-heading">My Hobbies</h3>
<ul>
  <li>Running</li>
  <li>Reading</li>
  <li>Writing</li>
</ul>
```

**Helpful Resources**:
* https://www.w3schools.com/jsref/prop_html_innerhtml.asp

Just be *careful* with `innerHTML` and use it wisely! It can be a big help, or it can *super* hurt you. Never use it with unescaped user generated input.

### Question 9: Make it from scratch!
So everything we just did was great, but we want to be sure that you know how to set up your *own* projects as well! To that end, in the `src` directory, you must fill in the `index.html` and `index.js` file.

The `index.html` file should be an html document, but *nothing* in the body except a script tag that links to your `index.js`. (we know you can also add scripts to the head, but let's keep it simple here and add it to the body).

Now, in whatever manner you want, your `index.js` file must:

- add an `H1` to the `body` with an `id` of `main-heading` and text of `"Hello World!"`
- add a `p` tag with an `id` of `main-text`, a class of `boring-text`, and text that reads `"Look, I'm some text!"`

This is important, you have to be able to create new documents and link your scripts to them correctly.

## BONUS - next steps
Like we said, there's so much out there for you to learn that we won't have time to cover in class. Check out [videos like this one](https://www.youtube.com/watch?v=v7rSSy8CaYE) which talk about how you can get around the dom effectively.
