# Mobile Portfolio Project

In this project I have used a combination of tools such as googles page speed insights and chrome dev tools to identify performance bottle necks in the material provided and set about fixing these issues. I have hosted the website on my own personal web page www.jackie-robson.com to enable me to leverage browser caching.

### running the app

To run the app simply clone or download the repo, and then veiw index.html in your favourite browser. Or alternitively veiw the web page [here](jackie-robson.com)

## page speed insights score
One of the aims of this project was to take the provided Portfolio page and increase the ratings found on googles pagespeed insights service, a higher score indicates that a web page is performant.

![screen shot of 99 page speed insight score](https://github.com/Jackie-Robson/mobile-portfolio/blob/master/readmeimg/99mobile.png)

the details of how i achieved this score can be found below.


### image optimisation
The first step I took to optimise both *index.html* and *pizza.html* was to format and compress the images that would be loaded on pages, I went about this by resizing the images to the maximum height and width that would be displayed as outlined in the artistic direction of the page, then I used the image optim program to compress the images, this saved a considerable amount of data being sent through the network, decreasing page load time.



### Render blocking Elements
After optimizing the images I went on to eliminate the render blocking elements by using the built in fonts rather than the performance costly web fonts being used as they acheived a similar effect, I then used the async functionality of HTML5 to make it so that when parsing the HTML the broswer could identify script tags that could be dealt with after the initial page load, I also used media queries to enable the browser to identify when parsing the html which of the CSS files would only need to handled when printing the page and finally i used the style tag in the header to inline the main.css contents into the index.html to stop the css document from blocking the rendering of the page due to having to download it and deal with it.

### minification
The Javascrpit file that is used to control the page is min.js. How ever reading this is extremely difficult so a formmatted version can be found in the main.js, also by hosting the page on my own domain i was able to emply a CDN which will automatically minify any html javascript or css files served to the users browser.

