# ScraperScript

A simple bookmarklet that lets you click any element in a page and returns the smallest unique (and reliable) selector it can find for that element.

Create a bookmark with the following content for the `href`/`link` attribute:

```javascript
javascript:(function(){_scraper_script=document.createElement('SCRIPT');_scraper_script.type='text/javascript';_scraper_script.src='https://raw.githubusercontent.com/cathalgarvey/scraperscript/master/scraperscript.js';document.getElementsByTagName('head')[0].appendChild(_scraper_script);})();
```

Then, try clicking it on a website to load the info frame. If it loads successfully, try clicking something to get a CSS selector.

Licensed under the WTFPL. A working example can be found at http://cryto.net/scraperscript.

**Usecase:** Figuring out a CSS-style selector for screenscraping.

**How to use the selector:** Use your favourite screenscraping library with CSS selector support. If you are using BeautifulSoup, you'll need to use my [patched version](https://github.com/joepie91/beautifulsoup) to have support for :nth-of-type() pseudoselectors as returned by ScraperScript.

**TODO:** Maybe generating CSS rules on mouseover is more useful, as it would speed up exploration and permit click-free operation on buttons and other "active" content?

**How to make it stop killing my input:** Just click the X in the ScraperScript bar. ScraperScript will release your input.

**How to develop:** Modify the bookmarklet to point at a scraperscript.js that is hosted locally. It's loaded with a cachebuster, so you can simply use the same bookmarklet every time you change the local code.

Known bugs: 

* On certain kinds of elements (some submit buttons, some elements with click events), ScraperScript can't prevent the attached event from happening. I'm unsure what causes this.
* You can't ctrl+C the selector because keyboard input is killed when ScraperScript is running. Needs to be fixed to allow ctrl+C.
