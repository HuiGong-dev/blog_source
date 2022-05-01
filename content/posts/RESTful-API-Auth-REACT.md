---
title: "RESTful API, Authentication & React study log"
date: 2022-04-26T15:54:54+02:00
draft: false
tags: [study log, api, authentication, React, web3]
---

The past two months were the so-called "Klausurphase '' in Germany and I barely updated anything here in those two months. Now it's time to restart in this new semester.

Here is my plan:

- Learn how to create RESTful API from scratch
- Learn OAuth 2.0 (perhaps also JWT)
- Learn React basics
- Dive into React and build (at least one)  MERN Stack App

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