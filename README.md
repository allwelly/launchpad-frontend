# launchpad-frontend

## Design Challenge:
**Frontend Web**

You and your friends are developing a new start-up called DRUBER, a drone-based ride share application that carries you to your destination. The original specification was to develop a web page that works in 1920x1080 however your company has realized that it is missing an entire market of smartphone users. Describe how you can modify your code to work in smartphone resolutions e.g. 750x1334 (iPhone 8). Please give specific examples where possible, but do not implement an entire DRUBER clone!

## Answer:

There are several ways to address this qusetion.
1. **Using CSS or SASS/SCSS**

Assuming that the start up used the trusty ol HTML and CSS to build their website, and used platforms such as Drupal or Wordpress to create their website, 
They could modify their code by adding CSS properties for mobile view, then add @media queries for other platforms such as tablets or desktop computers. This follows the "mobile first" approach by making the base css to work on mobile and media queries for sizes bigger than mobile view.

2. **Using React JS**

Assuming the start-up decided to use an up-to-date framework such as React JS, we can still build on to the knowledge we know about CSS to build a responsive design for DRUBER. First, they can add a useState hook to keep track of the state of the width as well as the function setWidth. Then we use eventListener to track window size that has an event called 'resize' and callback function that updates the variable for 'width' by taking the current inner width of the window. This improves responsivity to include sizes in between 750 px and 1920 px. useEffect can be used to add and remove event listener after event occurs. once the width state is updated, they can then use conditional statements to set the style of the components depending on the width state.

3. **Using React JS Module**

Lastly, the team needs to be debriefed on the importance of "mobile first" approach in web development to avoid issues such as this one to arise in the future.

The code example is referenced from react-responsive and used specifically to handle smartphone dimension as specified in the question.
