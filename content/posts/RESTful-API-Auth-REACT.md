---
title: "RESTful API, Authentication & React study log"
date: 2022-04-26T15:54:54+02:00
lastmod: 2022-05-03 08:57:13
draft: false
tags: ["study_log", "api", "authentication", "React", "web3"]
---

The past two months were the so-called "Klausurphase '' in Germany and I barely updated anything here in those two months. Now it's time to restart in this new semester.

Here is my plan:

- Learn how to create RESTful API from scratch
- Learn OAuth 2.0 (perhaps also JWT)
- Learn React basics
- Dive into React and build (at least one) MERN Stack App

Other than that I also want to learn more about web3 concepts. I’ll update my progress here. Hopefully I will finish building a few more fun projects at the end of this semester.

- What I’ve learned
- What was the challenge
- How I tackled it (if done)

Cheers 🍻

---

Date: 27 Apr 2022

- What I've learned

Building API using Node.js, express, MongoDB. Finished GET/POST/DELETE methods.

- What was the challenge

Now the API is running on localhost but I need to run it on a server so the next step is to install MongoDB on my server. Other than that everything is fine.

---

Date: 1 May 2022

- What I've learned

create react app with create-react-app command. Use dynamic values and Lists in JSX. Use conditionals in JSX to control the content of the page.

- Notes

JSX feels like a mixture of JavaScript and HTML but some keywords are reserved in JSX such as `class` so if I want to set class for a HTML element I should use `className` instead.

The tutorial I'm following is aged and it's still using `ReactDOM.render`(react 17) which is no longer supported in React 18. I followed the React document and rewrote it with `root.render`.

Another problem is I did not see any mention of `index.js` in the `index.html` file like it usually does but somehow `index.js` still has access to the `index.html` DOM. I did some googling and found out it's using Webpack with [html-webpack-plugin](https://www.npmjs.com/package/html-webpack-plugin).

---

Date: 2 May 2022

- What I've learned

Add css for components, set inline css.

- Notes

Again, the `index.css` is bundled with `index.html` through webpack just as the case of `index.js`.

Color tokens in JSX will not show color picker in VS Code by default so I looked up some extensions. The first one I tried is `json-color-token`. It actually worked but only supported hex color tokens. Sometimes I also use for example `ragb` so I tried another one called `vscode-color-picker` and now it worked! After installation remember to add this to your `setting.json`:

```json
"vscode-color-picker.languages": [
   "python",
   "typescript",
   "json",
   "jsonc",
   "javascript",
   "javascriptreact"
 ]
```

If the color picker did not show up, try cmd+shift+p and then `reload window`. After that the color picker should be there.

---

Date: 5 May 2022

- What I've learned

State and global state in React and useState hook.

- Notes

1. I kinda like the concept of components. It reminds me of the EJS template but in a more elegant way. Hook in React is new to me and the purpose of hook is to handle events thus to make the app interactive. Maybe later I should draw some flow charts to visualize the flow of this concept.

2. [Keys](https://reactjs.org/docs/lists-and-keys.html#keys) are needed for list component!

3. Passisng props from one component to another component should be careful. For example passing `element` from `ElementList.jsx` to `Element.jsx`, the element in `ElementList.jsx` looks like this:

```json
{id: 1, 
score: 10, 
comment: 'Lorem ipsum dolor sit amet consectetur adipisicing…ommodi alias voluptatem est voluptatum ipsa quae.'}
```

And then pass it to the `Element.jsx`:

```javascript
<Element key={item.id} item={item} />
```

The item in `Element.jsx` would be:

```json
{item: {id: 1, 
score: 10, 
comment: 'Lorem ipsum dolor sit amet consectetur adipisicing…ommodi alias voluptatem est voluptatum ipsa quae.'}}
```

In order to access `score` information, instead of 

```javascript
item.score
```

 you need to use:

```javascript
item.item.score
```

I understand why it works this way but still it looks a bit weird. Maybe it's because I'm new to this. I'll update here if I get better explaination/understanding.
