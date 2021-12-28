---
title: "Grab Homework With Python and Telegram Bot"
date: 2021-11-06T19:48:08+01:00
draft: false
tags: [python, web scrapping, telegram bot, automate the boring stuff]
---

So I'm taking a programming paradigms course this semester and the homework will be published every Friday on a webpage. It's kinda boring to check this webpage manually every Friday to grab the homework. Meanwhile, I noticed that the webpage is quite simple and easy to be scraped using python. So...why not? Spending a few hours to write a small piece of code to grab the homework automatically sounds great.

## All these efforts just to grab your homework? Why?

- It's fun!
- It's cool and that's what we CS student do 😉
- It's a great way to apply what I've learned to solve real world problem.
- It's a typical use case for web scraping and the code can be easily adapted to other scenarios. Have you ever applied for something (for example: a Visa for traveling in another country), and eagerly waited for the result to be published online? Have you ever manually refreshed the webpage again and again just in hope that the result would pop up? Well, let Python do all the work for you so that you can ~~Netflix and Chill~~ spend your time on something more interesting.

## Web scrapping with python

### Study the webpage

The homework links are located in this [webpage](https://pp.ipd.kit.edu/lehre/WS202122/paradigmen/uebung/). Right click and choose `Inspect` to view the HTML code of this site.

The homework links are located in a `table` element.

![Table](/image/table.png)

And then we can see all the links of homework are located in the `<a>` (or [_anchor_](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)) element.

 ![Table_details](/image/table_details.png)

 All right, time to write some code to get all the links.

### Write the code

Import libraries:

```Python
import bs4, requests, os
import urllib.parse as ul
```

`bs4` for beautiful soup, `os` to read and write files, `requests` to get HTML information and `urllib.parse` to make URL more friendly.

Get the HTML of this page:

```Python
def get_page(url):
      page = requests.get(url)
      page.raise_for_status()
      return page.text
```

To be continue...

## Store result of last scrape as local file

### Do the comparison

## Setting up Telegram Bot

### Create your own bot

### Get your chat ID

### Prepare the text

### Call the bot

## Scheduling

## Future improvement

### Scrape website with authentication system

### Downloading file automatically

### Dealing with VPN requirement
