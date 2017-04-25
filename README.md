## Mobile Portfolio Project

In this project I have used a combination of tools such as googles page speed insights and chrome dev tools to identify performance bottle necks in the material provided and set about fixing these issues.

## running the app
to run the app simply clone or download the repo, and then veiw index.html in your favourite browser.


### image optimisation
The first step I took to optimise both *index.html* and *pizza.html* was to format and compress the images that wouldbe loaded on pages, I went about this by resizing the images to the maximum height and width that would be displayed as outlined in the artistic direction of the page, then I used the image optim program to compress the images, this saved a considerable amount of data being sentthrough the network, decreasing page load time.

### Render blocking Elements
After optimizing the images I went on to eliminate the render blocking elements by using the built in fonts rather than the performance costly web fonts being used as they acheived a similar effect, I then used the async functionality of HTML5 to make it so that when parsing the HTML the broswer could identify script tags that could be dealt with after the initial page load, I also used media queries to enable the browser to identify when parsing the html which of the CSS files would only need to handled when printing the page and finally i used the style tag in the header to inline the main.css contents into the index.html to stop the css document from blocking the rendering of the page due to having to download it and deal with it.

### minification
The Javascrpit file that is used to control the page is min.js. How ever reading this is extremely difficult so a formmatted version can be found in the main.js.

