# launchpad-frontend

## Design Challenge:
**Frontend Web**

You and your friends are developing a new start-up called DRUBER, a drone-based ride share application that carries you to your destination. The original specification was to develop a web page that works in 1920x1080 however your company has realized that it is missing an entire market of smartphone users. Describe how you can modify your code to work in smartphone resolutions e.g. 750x1334 (iPhone 8). Please give specific examples where possible, but do not implement an entire DRUBER clone!

## Answer:

There are several ways to address this qusetion.
1. **Using CSS or SASS/SCSS**

Assuming that the start up used the trusty ol' HTML and CSS to build their website, and used platforms such as Drupal or Wordpress to create their 
website, They could modify their code by adding CSS properties for mobile view, then add @media queries for other platforms such as tablets or desktop computers. This follows the "mobile first" approach by making the base css to work on mobile and media queries for sizes bigger than mobile view.

e.g displaying cards stacked on top of each other for mobile vs side-by-side for desktop

example html code:
```
<div class="cards">
  <div><p>card 1</p></div>
  <div><p>card 2</p></div>
  <div><p>card 3</p></div>
</div>
```
example css:
```
.cards {
  display: flex;
  flex-direction: column;
}

@media screen only and (min-width 1920px) {
  .cards {
    flex-direction: row;
  }
}
```

2. **Using React JS**

Assuming the start-up decided to use an up-to-date framework such as React JS, we can still build onto the knowledge we know about CSS to build a responsive design for DRUBER. First, they can add a useState hook to keep track of the state of the width as well as the function setWidth. Then we use eventListener to track window size that has an event called 'resize' and callback function that updates the variable for 'width' by taking the current inner width of the window. This improves responsiveness by including sizes inbetween 750px and 1920px. useEffect can be used to add and remove event listener after event occurs. once the width state is updated, they can then use conditional statements to set the style of the components depending on the width state.

event listener:
```
import React, { useState, useEffect } from 'react'

function App() {
  const [width, setWidth] = useState(0)
   useEffect(() => { 

     updateDimensions();

     window.addEventListener(“resize”, updateDimensions);
     return () => 
       window.removeEventListener(“resize”,updateDimensions);
    }, [])
    const updateDimensions = () => {
      const width = window.innerWidth
      setWidth(width)
    }
}
```
adding to component:
```
const responsive = {
  notMobile: width > 800,
}

return (
  <>
    <Cards notMobile={responsive.notMobile} style={cardsStyle}/>
    <Main />
  </>
)
```
styling:
```
const cardsStyle = {
  display: 'flex',
  flexDirection: notMobile ? 'row' : 'column',
}
```

3. **Using React JS Module**

The third and most preferrable option is to use an existing module for React JS such as [react-responsive](https://www.npmjs.com/package/react-responsive) 
to add specific queries for DRUBER. the base CSS style should still be for mobile, but they can utilise media query to change the display of their components. Using the module allows for a simpler and neater code implementation.

using the module:
```
import React from 'react'
import { useMediaQuery } from 'react-responsive'

const Example = () => {
  const isDesktopOrLaptop = useMediaQuery({ minWidth: 1224 })

return (
  <>
    <Cards notMobile={isDesktopOrLaptop} style={cardsStyle}/>
    <Main />
  </>
)
```

styling:
```
const cardsStyle = {
  display: 'flex',
  flexDirection: notMobile ? 'row' : 'column',
}
```

Lastly, the team needs to be debriefed on the importance of "mobile first" approach in web development to avoid issues such as this one to arise in the future.

References:
- [3 Ways To Implement Responsive Design In Your React App](https://itnext.io/3-ways-to-implement-responsive-design-in-your-react-app-bcb6ee7eb424)
- [react-responsive](https://www.npmjs.com/package/react-responsive)
