# Twinkle-Twinkle

### How to animate stars in the background with CSS

<img src="https://media.giphy.com/media/3ohs4oWkzyVeVgTwKQ/giphy.gif" height="200">

<hr>

Hey all! the team over at:  
[![Foo](astrologia-logo.png)](https://fac21.github.io/week-2-astrologia-de-cada-dia/)  
got some good feedback (thanks!) about the twinkling stars in the background of the page.

I couldn't find any tutorials online so I thought I'd show you how we did it and you can play around with it and use it in your own pages.

**It's a whole lot easier than you might think :)**

## >>> [Here](https://codepen.io/2sexi4skool/pen/mdOZaqw) is a simplified version I drew up in CodePen
<hr>

## HTML

```html
<div id="star-container"><div>
```
- The HTML just needs one div. See? Easy! 
- This wil be the container for the stars that will be created by JS
<br><br>
<hr>

## CSS

```css
#star-container {
  background-color: black;
  height: 100vh;
}
```
- Container gets a black background and takes up the whole screen
<br><br>
```css
.star {
    position: absolute;
    height: 10px;
    width: 10px;
    background-color: white;
}
```

- This is a class that will apply to each star (the element doesn't exist yet!)
- The absolute positioning means we can change where they will be displayed on the page using CSS properties like `top:` and `left:`
<br><br>
```css
  @keyframes twinkle {
    0%   { opacity: 1; }
    50%  { opacity: 0.2; }
    100% { opacity: 1; }
  }
```
- This is a very simple keyframe that will change the opacity of the element it is applied to.
- If you've not used keyframes before  [here](https://css-tricks.com/almanac/properties/a/animation/) is a css-tricks page explaining the use and the syntax! 
<br><br>
<hr>

## JS

```javascript
const starContainer = document.getElementById('star-container')

for (let i = 0; i < 100; i++) {
    const element = document.createElement('div')
    element.style.top=`${Math.random()*100}%`
    element.style.left=`${Math.random()*100}%`
    element.style.animation = `twinkle ${1+Math.random()*10}s ease-out infinite`
    starContainer.appendChild(element)
    element.setAttribute('class', 'star')
    }
```

#### This is where stuff gets a little tricky but it's only 1 paragraph so I'll go through it step by step:

```javascript 
for (let i = 0; i < 100; i++) { 
```
- Does something x100 you know the deal
<br><br>

```javascript 
const element = document.createElement('div') 
```
- Creates an HTML `<div>` element
<br><br>

```javascript 
element.style.top=`${Math.random()*100}%` 
```
- This is where the absolute positioning comes into play: it sets the CSS style of the created element to be a random % away from the top (so down)
<br><br>
```javascript 
element.style.left=`${Math.random()*100}%` 
```
- Same as above, but away from the left (so right)
<br><br>
```javascript 
element.style.animation = `twinkle ${1+Math.random()*10}s ease-out infinite` 
```
- Adds the CSS animation property to the element (see keyframes link above) including a random duration of 0-10 seconds +1 (this is so that the animation time will never be <1 in which case the star would become a pretty angry strobe light) 
<br><br>
```javascript 
starContainer.appendChild(element) 
```
- Makes the element a child (puts it inside of) our HTML star-container div
<br><br>
```javascript 
element.setAttribute('class', 'star') 
```
- Sets the class of our element to "star", which is something we've already defined in our CSS :)
<br><br>
## All done!

<img src="https://media.giphy.com/media/Yr00rD28UDqKI/giphy.gif" height="200">
Now you can twinkle to your hearts content

<hr>

### Stuff to play around with

- Background colour / img / opacity of star-container div
- Size / shape / colour of stars (% sizes help with responsivity ;))
- What the Keyframes animation does at different points
- Where the stars will be created on the page
- Use z-indexing to make sure stars are displayed behind / infront of other elements on page as desired

### Stretch goal:

- See if you can write some JS to create the stars in different colours ;)

