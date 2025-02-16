# React Local Setup

## Learning Objectives

* SWBAT set up a React project locally on personal computer 
* SWBAT edit the React starter page to display HTML they have written

## Local Setup

#### Step 1

First you need to check if you have Node installed on your computer. You can check by typing the following into your terminal/command line.

```HTML
npm -v
```

You should have Node 5.2 or higher installed. If it tells you Node is not installed please go to https://nodejs.org and install the version called 16.14.0 LTS

#### Step 2

Once Node is installed, cd into Documents, 
then run each of the following lines of code in your terminal:

```HTML
npx create-react-app local-react-app
cd local-react-app
```

The first command tells node where to find the files on the internet to create a new React project and install those files on your computer. "local-react-app". is the name of the project we create as well as the directory where the files are installed. You can name this project anything as long as there are no spaces or special characters. We could have named it "cat-lovers-website" or "best_dressed_robots".

#### Step 3

Type the following line of code into your terminal:

```HTML
npm start
```

This command tells Node to begin running the React program we have created. You should see the following message in your terminal:

![npm start](./img/npm-start.png)

As instructed, let's view our app using the link provided. Open your browser and visit http://localhost:3000/ (or whatever address is provided in your terminal) to see what our React application looks like.

#### Step 4

You should see a page that looks like this. Pretty cool, right? Also - notice how it tells us to edit src/App.js - let's try it out and see what happens.
![Starter Page](./img/first-page.png)

#### Step 5

Test the file locally by doing the folloing below:

Open directory that contains your React project in your code editor. Find the App.js file in the "src" directory. Delete the code inside of the div with the class name "App."

![Delete Code](./img/delete-code.png)

Try adding some HTML to get "Hello World" to appear on the web page instead!

![Hello World](./img/hello-world.png)

<a id="mini-challenges"></a>
#### Step 6

* Add an `<h1>` tag with the text "Local Development Completed" within the `div` with the class `"App"`

