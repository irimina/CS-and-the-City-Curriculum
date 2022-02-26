# Props + JSX in React

## Learning Objectives

* Students will be able to pass props from a parent component to a child component.
* Students will be able to export and import variables between files.
* Students will be able to create components that operate as templates.


## Components and props

As we have discussed, React allows developers to build websites by piecing together various components. This makes the development processing easier, as the website is now built with modular pieces that can be modified, added, and removed. But what if we want to reuse and customize a component without copying-and-pasting our code into a whole new component? That's where props come in, and they allow us to use our components as templates that can be customized with specified PROPerties.

<a id="singleprop"></a>
### Passing Our First Property

Props are passed from the implementation of a component, e.g. `<someComponent />`, down into the definition of that component, e.g. `function someComponent(){..}` in `someComponent.js`. We are going to pass our first prop from where we use `<Testimonials />` in `App.js` to our `Testimonials` function in `Testimonials.js`. To do so, we are going to modify the code in the `App.js` and `Testimonials.js` files to the following:

```javascript
function App() {
  return(
    <div className="App">
      <Navbar/>
      <Splash/>
      <Testimonials userTestimonial="Street Eats is the best food review site that has ever been built. Now I can pick the best food cart with confidence instead of wondering if I'm getting a raw deal."/>
      <div className = "container">
        <div className="row">

        </div>
      </div>
    </div>
  )
}
```

You will notice we only modified line 16 of the code. We added an attribute to the `Testimonials` element called `userTestimonial`. By adding this attribute to our `Testimonials` element, it will be passed down as props from `App.js`.

From the [React documentation](https://reactjs.org/docs/components-and-props.html): "When React sees an element representing a user-defined component, it passes JSX attributes to this component as a single object. We call this object "props"."

```javascript
function Testimonial(props) {
  return(
    <div className="Testimonials">
      <div className="row">
        <div className="col-6 offset-3 testimonial">
          <h3 className="secondary-text-testimonial">Testimonial</h3>
          <p className="paragraph-text"> {props.userTestimonial}</p>
        </div>
      </div>
    </div>
  )
}
```

In this case, we're using the  `<p className="paragraph-text"> {props.userTestimonial}</p>` to indicate that the contents of this paragraph should be filled with whatever prop was passed with the attribute `userTestimonial`.

Now we are going to modify two lines of code in our `Testimonials.js` file:

We need to have our functional component take in a parameter called `props`. By creating this parameter we are now able to pass the props object down from `App.js` into our `Testimonials` component.

We are then going to render our prop onto the screen. To embed our prop into the HTML we have written, we just have to add `{ props.testimonial }` to the paragraph element on the page.

> React uses a syntax extension of JavaScript called JSX. JSX allows us to embed JavaScript into our HTML by wrapping the JavaScript in curly braces. To use the JavaScript variable `testimonial` in our HTML, we just need to add curly braced around it.


In the example we just did, we passed a hard-coded string down as the prop "userTestimonial." We can also pass down a JavaScript variable (or even a function! But that's for another time.) as a prop. Let's try this by refactoring our code a bit. We are going to create a variable called `testimonial` and set it equal to our previous review. Then we can pass it down as a prop by using JSX syntax as seen below:

```javascript
function App() {
  // Declare our variable called testimonial
  let testimonial = "Street Eats is the best food review site that has ever been built. Now I can pick the best food cart with confidence instead of wondering if I'm getting a raw deal."

  // Pass that variable to the Testimonials component as part of the return
  return(
    <div className="App">
      <Navbar/>
      <Splash/>
      <Testimonials userTestimonial={testimonial} />
      <div className="container">
        <div className="row">

        </div>
      </div>
    </div>
  )
}
```

![Testimonials](./img/testimonials.png)

If done correctly, our web site should look like the example above.

<a id="multipleprop"></a>
### Passing Multiple Properties

We can pass multiple props down to a component, allowing us to use a component as a template that can be customized. By passing more props, we can add more and more customizations to our components. This is how the component we looked at the beginning of class might have had the same size or styling, but completely different images and text.

To complete We Eat Street Meat, we need to add reviews to our site. We have saved the reviews in a separate file, which we will import into our App component and then pass down as props to multiple review cards.

> It should be mentioned that the `review_data.js` file is serving as our "database" in this application. In a real application, we wouldn't save the reviews in a static file, but rather have saved in a database that is loaded when the website is reached.

Let's create our first review card by adding the following code to our `App.js` file:

```javascript
function App() {
  let testimonial = "Street Eats is the best food review site that has ever been built. Now I can pick the best food cart with confidence instead of wondering if I'm getting a raw deal."
  return(
    <div className="App">
      <Navbar/>
      <Splash/>
      <Testimonials userTestimonial={testimonial} />
      <div className="container">
        <div className="row">
          <ReviewCard
            name={ reviews[0].name }
            headline={ reviews[0].headline }
            summary={ reviews[0].summary }
            stars={ reviews[0].stars }
            posted={ reviews[0].posted }
          />
        </div>
      </div>
    </div>
  );
}
```

The first step is to create a `<ReviewCard />` element and add the attributes as seen above.

```javascript
function ReviewCard(props) {
	return(
	  <div className="col-4 Review">
	    <div className="card text-center mb-3r">
	      <div className="card-header">
	        { props.name }
	      </div>
	      <div className="card-body">
	        <h5 className="card-title">{ props.headline }</h5>
	        <p className="card-text">{ props.summary }</p>
	        <p className="card-text">{ props.stars }</p>
	        <a href="#" className="btn btn-warning">Full Review</a>
	      </div>
	      <div className="card-footer text-muted">
	       { props.posted }
	      </div>
	    </div>
	  </div>
	);
};
```

Now we need to modify `ReviewCard.js` to utilize the props that are being passed down to it.

#### Mini-Challenges  - answer in the document 

* How could we pass the review data to each card using only one attribute?
* Complete the website by creating a review card for each of the six reviews
* Extra challenge: Refactor your code so that you **iterate** through the review data and create each card programmatically (rather than hard coding each one). Try researching how to do this.

## Close
* Describe the process of creating a review card for each review.
* What is the key benefit to building components with props?
* What did you learn/practice/understand better today?

