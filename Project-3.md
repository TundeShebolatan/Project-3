# PROJECT 3: MERN STACK IMPLEMENTATION

SIMPLE TO-DO APPLICATION ON MERN WEB STACK

Step 0 : Preparing prerequisites

- Sign in to AWS free tier account and create a new EC2 Instance of t2.nano family with Ubuntu Server 20.04 LTS or 22.04 LTS, (HVM) image.
  
- Connect to this instance via SSH.

STEP 1 : BACKEND CONFIGURATION

Update ubuntu

`sudo apt update`

Upgrade ubuntu

`sudo apt upgrade`

Get the location of Node.js software from Ubuntu repositories

`curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -`

Install Node.js on the server with the command below

`sudo apt-get install -y nodejs`

both nodejs and npm (Package manager for Node) are installed

Verify the node installation with the command below

`node -v`

![Installation status](images/Node-installation-confirmed.PNG)

Verify the node installation with the command below

`npm -v`

![Installation status](images/npm-version.PNG)

***Application Code Setup***

Create a new directory for your To-Do project:

`mkdir Todo`

`ls`

![Mkdir Todo](images/Todo-directory-confirmation.PNG)

Now change your current directory to the newly created one:

`cd Todo`

Initialize your project

`npm init`

Press Enter several times to accept default values, then accept to write out the package.json file by typing yes.

![initialize project](images/Initialize-project.PNG)

To use express, install it using npm

`npm install express`

![Installation status](images/Install-Express-npm.PNG)

Now create a file index.js with the command below

`touch index.js`

Run ls to confirm that your index.js file is successfully created

![Installation status](images/Install-confirm-index-js.PNG)

Install the dotenv module

`npm install dotenv`

![installation status](images/install-dotenv.PNG)

Open the index.js file with the command below

`vim index.js`

![Open file](images/Open-index-js-file.PNG)

To start the server to see if it works, Open the terminal in the same directory as the index.js file and type:

`node index.js`

![server status](images/server-status.PNG)

Since an inbound rule to open TCP port 5000 was already created in step 0, open up your browser and try to access your server’s Public IP or Public DNS name followed by port 5000:

![Access confirmed](images/Welcome-to-Express.PNG)

Create routes that will define various endpoints that the To-do app will depend on. So create a folder routes

`mkdir routes`

Change directory to routes folder

`cd routes`

create a file api.js

`touch api.js`

![mkdir routes](images/routes.PNG)

Open the file

`vim api.js`

Copy and paste the new code

![API file](images/Script-API.PNG)

To create a Schema and a model, install mongoose which is a Node.js package that makes working with mongodb easier.

Change directory back to "Todo" folder and install Mongoose

`cd Todo`

`npm install mongoose`

![installation status](images/install-mongoose.PNG)

Create a new folder models :

`mkdir models`

![Models directory](images/mkdir-Models.PNG)

`cd models`

`touch todo.js`

![Create Todo-file](images/touch-todo-js.PNG)

Open the file

`vim todo.js`

![Open file](images/open-todo-js.PNG)

In Routes directory, open api.js

`:%d`

paste the code

![Updating Routes](images/Script-API-replaced.PNG)

***Create a MongoDB database and collection inside mLab***

![Mongodb Setup](images/MongoDB-SetUp.PNG)

In the index.js file, we specified process.env to access environment variables, but we have not yet created this file. So we need to do that now.

Create a file in your "Todo" directory, and name it ".env"

`touch .env`

`vi .env`

![Open dotenv file](images/open-dotenv-file.PNG)

Add the connection string to access the database in it, just as below:

`DB = 'mongodb+srv://<username>:<password>@<network-address>/<dbname>?retryWrites=true&w=majority'`

![Connecting string](images/connect-string-to-access-DB.PNG)

update the index.js

`vim index.js` `esc` `:` `%d`

![Replaced script](images/replaced-script-index-js.PNG)

Start your server

![server status](images/server-status.PNG)

Database connected successfully.

Now open your Postman, create a POST request to the API

"http://3.17.208.229:5000/api/todos"

![POST Request](images/Postman1.PNG)

Create a GET request to your API on "http://3.17.208.229:5000/api/todos"

![Get Request](images/Postman2.PNG)

In the "Todo" directory, run:

`npx create-react-app client`

Install *concurrently*. It is used to run more than one command simultaneously from the same terminal window.

`npm install concurrently --save-dev`

![Installation status](images/concurrently.PNG)

Install *nodemon*. It is used to run and monitor the server. If there is any change in the server code, nodemon will restart it automatically and load the new changes.

`npm install nodemon --save-dev`

![Installation status](images/nodemon.PNG)

In "Todo" folder open the package.json

Change the highlighted part of the script and replace with the new code.

![Replacement script](images/Package-json-replacement-script.PNG)

***Configure "Proxy" in "package.json"***

Change directory to ‘client’

`cd client`

Open the package.json file

`package.json`

![cd client](images/cd-into-client.PNG)

Add the key value pair in the package.json file "proxy": "http://localhost:5000".

![Configure proxy](images/Configure-Proxy-package-json.PNG)

Inside the "Todo" directory, run:

`npm run dev`

Your app should open and start running on localhost:3000

![React page](images/React-page-loads.PNG)

!["Todo" Page loads](images/Todo-App-up-and-running.PNG)

*Creating your React Components**

From your "Todo" directory run

`cd client`
`cd src`

Inside your src folder create another folder called components

`mkdir components`

Move into the components directory

`cd components`

Inside ‘components’ directory create three files Input.js, ListTodo.js and Todo.js.

![mkdir components](images/creating-3-react-components.PNG)

`vi Input.js`

![open file](images/open-input-js1.PNG)

Copy and paste new script

![edit file](images/open-input-js.PNG)

To make use of Axios, Move to the src folder

`cd ..` `cd ..`

Install Axios

`npm install axios`

![installation status](images/install-axios.PNG)

Go to ‘components’ directory

`cd src/components`

After that open your ListTodo.js

`vi ListTodo.js`

![open file](images/edit-list-todo.PNG)

![Edit file](images/list-todo.PNG)

Then in your Todo.js file you write the following code

![open file](images/open-todo-js.PNG)

![Edit file](images/components-todo-js.PNG)

We need to make little adjustment to our react code. Delete the logo and adjust our App.js

Move to the src folder

`cd ..` `vi App.js`

![open file](images/reconfiguring-app-js.PNG)

Edit the code

![Edit file](images/new-script-for-app-js.PNG)

Exit the editor. In the src directory

`vi App.css`

![open file](images/edit-index-css1.PNG)

![Edit file](images/edit-index-css.PNG)

Exit

`vim index.css`

![open file](images/edit-index-css1.PNG)

![Edit file](images/edit-index-css.PNG)

Go to the "Todo" directory

`cd ../..`

`npm run dev`

![Application functional](images/Project-3-completed.PNG)
