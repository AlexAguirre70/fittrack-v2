# Fitness Tracker 

## Inspiration
Two things we like to do, and share in common. <br />
Working out and Programming. 
We came together build an app that we can personally use, and be proud to share with out friends!

## Details
User will be able to register and login into the Fitness Tracker. <br/>
Once logged in they will be able to update the own personal data to track their progress on their weight and measurements. <br/>
They will also able to log their workouts and meals to track their calorie consumption.<br/>
They will be able to select different exercises to target specific muscle groups.<br/>
The interface will be resizable to view on different size screens. <br/>
<br/>
## Technology
* React - Frontend UI development
* NodeJS  - Backend API development and Testing
* Express - for middleware and routing
* Bootstrap - CSS library for UI Styling
* CSS - UI Styling
* SASS - Prei-processer to format CSS for Readibility 
* Sequelize - ORM to Generate and Migarte Models to Database
* Postgres on AWS RDS - Database
* RapidAPI to access exercises
* Heroku- Web Deployment
* JWT Token Authorization - Security to authenticate user login
* BCrypt - Security to Hash Password
<br/>
<br/>

## Screenshots

### Home

![alt Profile-Snapshot](public/fittrack-home-snapshot.png/) 

### Profile
![alt Profile-Snapshot](public/fittrack-profile-snapshot.png/) 

<br/>

## API - Controllers

### Register and Login Authentication
| Method | Path | Purpose |
|--------|------|---------| 
|POST | authentication/ | Authenticate User|
|GET | authentication/profile | Retrieve User data|
<br/>

### Users & UserData
| Method | Path | Purpose |
|--------|------|---------|
|POST | /* | Login and Assign JWT|
|GET | /profile | Get User Data for Profile |
<br/>

### Workouts
| Method | Path | Purpose |
|--------|------|---------|
|GET | / | Get all workout logs for User for selected date|
|POST| / | Create a workout log for User|
|PUT | /:id | Update a workout log for User |
|DELETE| /:id | Delete a workout log for User|
<br/>

### Meals
| Method | Path | Purpose |
|--------|------|---------|
|GET | / | Get all meal logs for User for selected date|
|POST| / | Create a meal log for User|
|PUT | /:id | Update a meal log for User |
|DELETE| /:id | Delete a meal log for User|
<br/>

## Database Structure
Users 1:1 with UserData on user_id <br>
Users 1:n with Workouts on user_id <br>
Users 1:n with Meals on user_id<br>
Exercises (3rd Party API) <br>
<br/>

## Issues Encountered

### Deployment
<br/>
Initially, we attempted to deploy our App using AWS Amplify but due to the app file structure, the build failed.<br/>
Initially, we attempted to deploy our App using AWS Beanstalk but due to the app file structure, the build failed. It also required that we install ELB CLI, Python, virtualEnvironment and was requesting to change Windows/System32 files and paths. It's over complicated, so we took another route
<pre><b>Resolution:</b>
Having successfully deployed on Heroku, we chose this for deployment.
We recreated a basic app, deployed on Heroku successfuly the continued to resolve the app file structure</pre>

### File Structure
<br/>
On our Version 1, we realize that we nested the backend and frontend without server.js and Package.json at the root. <br/>
<pre><b>Resolution:</b> 
We recreated the App with the proper monorepo file structure and copied the code into their respective files.
We needed to update all the relative paths to reflect the new file strutures.
Ran the app and it works great, but ran into the issue of the server running on port 5000, but the frontend not running on Port 3000
</pre>

### Running the APP - not running port 3000
<br/>
When running npm start from the root folder, it tries to run on PORT 5000, but that is for the server.<br/>
The npm start says there is already an app running on port 5000, and sets the default port to run on port 5001
The app launches fine, but then 
<pre><b>Resolution:</b>
</pre>

### CORS Access Errors
<br/>
When running the app, we check to see if the CurrentUser is logged in which is done with a fetch request.<br/>
This returns an error on the console on the local client because the origin header shows port: 5001 and does not match the server port:5001.<br/>
On the deployment version, it is trying to hit the path LocalHost:5000, and that doesn't exist on the web server.<br/>
<pre><b>Resolution:</b>
</pre>

### Setting FETCH Path
<br/>
We set the fetch request to a static path  https://localhost:5000, and the creates an issue with the deployment server.
<pre><b>Resolution:</b>
</pre>

## Contributors

[Alex Aguirre](https://github.com/AlexAguirre70) <br>
[Gustavo Martinez ](https://github.com/Gustavo0623) <br>
[Matthew Herrera](https://github.com/Machew115) <br>