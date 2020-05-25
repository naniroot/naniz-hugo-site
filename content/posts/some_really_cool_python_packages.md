---
title: "Some Really Cool Python Packages"
date: 2013-06-25T19:54:15-07:00
draft: false
images:
tags: [python, packages, mechanize, beautifulsoup, antigravity, pycountry]
---
> Revitilizing very old post from the past. Of course, my thinking has changed since then, but its always fun to open a time capsule.

These definitely must be checked out.

## Mechanize

[Mechanize](https://pypi.org/project/mechanize/) is an awesome package. It basically gives you a programmable browser. It takes care of https, cookies and all the forms. It gives you immense power to do a lot of things.

Imagine you have a browser that fills all the forms for you, submits them and processes the response. Imagine doing it 1000 times or hey, a million times or more depending on the processing power you have. Imagine spamming comments using this, I am not saying that you should, I am only saying you can. But most comments have captcha and limit on comment flooding anyway.

But this package can help you do some managing if required. It helps you access resources required, have custom filtering, provide custom services etc. Things you can probably do is make a separate archive of your emails, email contacts, code alerts based on constraints etc. The most freakingly awesome thing you can do is write your own web crawler. Crawl through the web, index info, handle loops and maybe finally start your own search engine that kicks google’s ass. 

I am pretty sure [Aaron Swartz](https://en.wikipedia.org/wiki/Aaron_Swartz) used mechanize to download all the copyrighted content provided by MIT and the law documents. I have not fully explored the package but I am currently working on a kickass project that uses mechanize and I plan to write all about it once I am done.

## BeautifulSoup

[BeautifulSoup](https://pypi.org/project/beautifulsoup4/) is one weird name for a python package but it is an amazing package in python to navigate, search, modifying parse trees in html and xml files. BeautifulSoup when combined with mechanize forms a very powerful tool to navigate the DOM structure of an website and perform the required function. 

Have you ever tried to guess how if you post a link to facebook, it tries to find a picture in that website to post along with your link. That is done by something like BeautifulSoup that navigates that link’s html or DOM structure to find the images required. BeautifulSoup wraps around python packages [lxml](https://lxml.de/) and [html5lib](https://pypi.org/project/html5lib/) and gives a very powerful parsing tool I am just starting to explore.

## Antigravity
[Antigravity](http://python-history.blogspot.com/2010/06/import-antigravity.html) was a fun package developed based on [this](http://xkcd.com/353/) xkcd comic. I have already shown this comic in my [previous]({{<ref "python_ftw.md">}}). It is really amuzing that engineers develop packages based on likes and whims. But ain’t all packages a result of something like that.

Antigravity is a package that simply opens up a link to the comic in your default browser and also performs geohashing as given in [this](http://www.xkcd.com/426/) comic. Who knows? maybe you will meet your life partner while geo hashing using antigravity package.

## Pycountry

[Pycountry](https://pypi.org/project/pycountry/) is a very useful package that contains the entire world’s ISO country names, ISO numbers, subdivisions, languages, currencies, script definitions and their translations. If you are writing a global application and want to keep track of your user’s global addresses and languages in a standardised format that is easy for later processing like analytics or customised servicing then PyCountry is your best bet. At least in python. It is very easy to use like any python package with upto date ISO codes.

I’ll try to find more cool python packages and keep this list updated as and when I find them.
