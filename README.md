# Reverse-Engineering-Authentication

### In this assignment I will be reverse engineering the starter code provided and create a tutorial for the code.

```
AS A developer

I WANT a walk-through of the codebase

SO THAT I can use it as a starting point for a new project
```

## FILE BREAKDOWN: 
* The `config` folder contains `middleware`, `config.js`, and `passport.js`.
  * `middleware` contains `isAuthenticated.js`
     * `isAuthenticated.js` restricts routes that a user cannot access if not logged in, if a user is logged in, it will redirect to the restricted routes.
  * `config.json` contains a generic username and password for MYSQL database.  Please enter your own username and password.
  * `passport.js` requires an email and valid password for login.  If a user enters a username or password incorrectly, it will notify the user.  This file uses Sequelize boilerplate to serialize and deserialize the user.
* The `models` folder contains `index.js` and `user.js`
    * `index.js` will connect to the database
    * `user.js` will use `bcrypt` for password hashing to secure the database.  This requires a valid username and password.
* The `public` folder contains `js`,`stylesheets`, and `html`
    * `js` contains `login.js`, `members.js`, and `signup.js`
        * `login.js` uses reference to the forms and input.  Upon submission, it validates the email and password. If the correct email and password is entered, the form is cleared, and there is a POST to the api/login, and the user is redirected to the members page.  
        * `members.js` uses a GET to find out which user is logged in and updates the HTML.
        * `signup.js` uses reference to the form and input.  When the signup button is clicked, the email and username is validated.  If there is a valid username and password, the signUpUser function runs.  There will be a POST to the signup route and the user will be redirected to the members page. Otherwise, an error will be thrown.   
    * `stylesheets` contains `styles.css` for the signup and login
    * `login.html` contains html for user login
    * `members.html` contains html for members page
    * `signup.html` contains html for user signup
* The `routes` folder contains `api-routes.js` and `html-routes.js`
        * `api-routes.js` requires the models and passport.  If the user has valid credentials, and directs them to the members page, otherwise it routes them to signup.  The password is hashed for security.  Then the user is logged in.  There is also a GET route to log out the user.  There is also a GET to retrieve data to determine if user is signed in.  If not an empty object is returned, if so, the username and id is returned.
        * `html-routes.js` requires path and isAuthenticated.js. There will be a GET to redirect users to the members page if they already have a username and password from the login page.  There is also a GET to redirect users to the members page if they have a valid username and password from the sign up page.  If the user does not have a valid username and password, they will be redirected to the signup page.    
* `server.js` requires npm packages (listed), sets up ports requiring models, creates express routes and configures middleware, uses sessions to keep track of login status, requires our routes, and syncs to the database.  

## GETTING STARTED: 

* Using MYSQL WorkBench, create the `passport_demo` database.

* Update `config.json` with your personal information.

* Open terminal and run `npm i`.

* Install the node packages `passport`, `fs`, `path`, `sequelize`, `bcryptjs`

* In terminal run `node server.js`


* Open browser and put "http://localhost:8080" in search bar
  


## Google Docs
## https://docs.google.com/document/d/1Q9PhjgP1sXGOS0QtnpOhWUZXh7j_anOSONIcTlhMfEk/edit?usp=sharing


 
 ## License: 
 * MIT


