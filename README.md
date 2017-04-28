# Mobile Portfolio Project

In this project I have used a combination of tools such as googles page speed insights and chrome dev tools to identify performance bottle necks in the material provided and set about fixing these issues. I have hosted the website on my own personal web page www.jackie-robson.com to enable me to leverage browser caching.

### running the app

To run the app simply clone or download the repo, and then veiw index.html in your favourite browser. Or alternatively veiw the web page www.jackie-robson.com

## page speed insights score
One of the aims of this project was to take the provided Portfolio page and increase the ratings found on googles pagespeed insights service, a higher score indicates that a web page is performant.

![screen shot of 99 page speed insight score](https://github.com/Jackie-Robson/mobile-portfolio/blob/master/readmeimg/99mobile.png)

the details of how i achieved this score can be found below.


### image optimisation
The first step I took to optimise both *index.html* and *pizza.html* was to format and compress the images that would be loaded on pages, I went about this by resizing the images to the maximum height and width that would be displayed as outlined in the artistic direction of the page, then I used the image optim program to compress the images, this saved a considerable amount of data being sent through the network, decreasing page load time. This means that even using a 3G network the page load was under 800ms as seen below.

![alt text](https://github.com/Jackie-Robson/mobile-portfolio/blob/master/readmeimg/Screen%20Shot%202017-04-28%20at%2009.24.01.png)



### Render blocking Elements
After optimizing the images I went on to eliminate the render blocking elements by using the built in fonts rather than the performance costly web fonts being used as they acheived a similar effect, I then used the async functionality of HTML5 to make it so that when parsing the HTML the broswer could identify script tags that could be dealt with after the initial page load, I also used media queries to enable the browser to identify when parsing the html which of the CSS files would only need to handled when printing the page and finally i used the style tag in the header to inline the main.css contents into the index.html to stop the css document from blocking the rendering of the page due to having to download it and deal with it.

### Minification
The Javascrpit file that is used to control the page is min.js. How ever reading this is extremely difficult so a formmatted version can be found in the main.js, also by hosting the page on my own domain i was able to emply a CDN which will automatically minify any html javascript or css files served to the users browser.

### Browser Caching 
By hosting the page on my own private server i was able to leverage browser caching, which tells the browser to load content from it's memory unless a specific amount of time has passed. This means that on a page where the content is not updated regularly the browser has to download less information from the server on subsequent visits to the page.

## Get the randomPizzaContainer images to resize in under 5ms
the second goal of this project was to get the images in the randomPizzaContainer class to resize using the slider in under 5ms

![under 1ms](https://github.com/Jackie-Robson/mobile-portfolio/blob/master/readmeimg/Screen%20Shot%202017-04-28%20at%2010.25.17.png)

The details of how i achieved this are below.

### Refactoring the function

* By removing ``` var pizzaSizes = document.querySelectorAll(".randomPizzaContainer") ```from the loop and storing it in a variable outside of the loop saved a lot of needless recalculations as the loop runs because the amount of all elements with the randomPizzaContainer class doesn't change while the for loop runs. This helps  

* The determineDx function was not needed so it was removed.

* Because the value width is always going to be 25%, 33.3% or 50% based on the size value, those values were hard coded into the switch statement instead of adding a '%' string on the end.

## Get pizza.html to render at 60fps (frames per second)
The third goal of this project was to get the pizzeria site to render at 60 frames per second.

![59.8fps screenshot](https://github.com/Jackie-Robson/mobile-portfolio/blob/master/readmeimg/Screen%20Shot%202017-04-28%20at%2008.17.19.png)

The details of how i achieved this are below.

### Refactoring functions

* `document.body.scrollTop/1250` is a costly calculation, so when the updatePositions function runs it was repeating this calculation every time the event listener registerd scrolling. This caused a significant fps decrease due to the intensity of the calculations, so i removed this from the body of the for loop and saved it in a variable called cachedScrollTop to save repeating the calculation every time the loop ran.

* By changing the end conditions for the function that loads the moving pizzas on screen to dynamically adjust based on the height of the screen resulted on a reduced number of sliding pizzas being generted and rendered. The calcuation was saved inside variables stored outside of the for loop as such

```
 var cols = 8;
 var s = 248;
 var pizzaRows = screen.height / s;
 var pizzasOnScreen =  pizzaRows * cols;
  ```
    
* `var cols = 8;` dictatates the number of columns to be displayed
* `var s = 248;` sets the height of each row of pizzas
* `var pizzaRows = screen.height / s;` takes the height of the screen and devides it by the height of each row to decide how many rows can be displayed on screen
* `var pizzasOnScreen = pizzaRows * cols;` takes the amount of rows and multiplies it by the amount of columns to calculate the total amount of moving pizzas to be generated.
    
