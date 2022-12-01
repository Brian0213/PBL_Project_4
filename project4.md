# Documentation for Project 4: MEAN STACK IMPLEMENTATION

## Preparing prerequisites

- Create a new EC2 Instance of t2.nano family with Ubuntu Server 20.04 LTS (HVM) image.

1. **Install NodeJs**

- Update ubuntu

`sudo apt update`

![Ubuntu Update](./image/ubuntu-mean-update.PNG)

Upgrade ubuntu

`sudo apt update`

![Ubuntu Upgrade](./image/ubuntu-mean-upgrade.PNG)

- Add certificates

`sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates`

![Sudo Apt -y Install](./image/apt-y-install-cert.PNG)

`curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -`

![Curl Status](./image/curl-status-output.PNG)

1. Install NodeJS

`sudo apt install -y nodejs`

![Install -y Nodejs](./image/install-y-nodejs-output.PNG)

2.**Install MongoDB**

- MongoDB stores data in flexible, JSON-like documents. Fields in a database can vary from document to document and data structure can be changed over time. For our example application, we are adding book records to MongoDB that contain book name, isbn number, author, and number of pages. mages/WebConsole.gif

`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6`

![Sudo Keyserver](./image/apt-keyserver-output.PNG)

`echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list`

![Echo Repo](./image/echo-repo-output.PNG)

- Install MongoDB

`sudo apt install -y mongodb`

![Install -y Mongodb](./image/install-y-mongodb-output.PNG)

- Start The server

`sudo service mongodb start`

![Mongodb Start Service](./image/mongodb-service-start.PNG)

- Verify that the service is up and running:

`sudo systemctl status mongodb`

![Mongodb Systemctl Status](./image/systemctl-mongodb-run-status.PNG)

- Install npm – Node package manager.

`sudo apt install -y npm`

![Mongodb Systemctl Status](./image/install-y-npm.PNG)  N.B. Error in the package

- Install body-parser package

We need ‘body-parser’ package to help us process JSON files passed in requests to the server.

`sudo npm install body-parser`

![Install Body Parser](./image/install-body-parser-output.PNG)

- Create a folder named ‘Books’

`mkdir Books && cd Books`

![Create Folder Book](./image/folder-book-output.PNG)

- In the Books directory, Initialize npm project:

`npm init`

![Create Folder Book](./image/book-npm-initialize.PNG)

- Add a file to it named server.js:

`vi server.js`

![Server Js Output](./image/server-js-output.PNG)

3.**Install Express and set up routes to the server**

- Express is a minimal and flexible Node.js web application framework that provides features for web and mobile applications. We will use Express in to pass book information to and from our MongoDB database. We also will use Mongoose package which provides a straight-forward, schema-based solution to model your application data. We will use Mongoose to establish a schema for the database to store data of our book register.

`sudo npm install express mongoose`

![Express Mongoose Install](./image/express-mongoose-install-output.PNG)

- In ‘Books’ folder, create a folder named apps:

`mkdir apps && cd apps`

![Create apps Folder](./image/apps-create.PNG)

- Create a file named routes.js:

`vi routes.js`

- In the ‘apps’ folder, create a folder named models:

`mkdir models && cd models`

![Create models Folder](./image/create-models-folder-output.PNG)

- Create a file named book.js:

`vi book.js`

![Create Bookjs File](./image/file-book-js.PNG)

4.**Access the routes with AngularJS**

-AngularJS provides a web framework for creating dynamic views in your web applications. In this tutorial, we use AngularJS to connect our web page with Express and perform actions on our book register.

Change the directory back to ‘Books’:

`cd ../..`

![Change to Book Directory](./image/change-book-directory.PNG)

- Create a folder named public:

`mkdir public && cd public`

![Create Public Directory](./image/create-public-folder.PNG)

- Add a file named script.js

`vi script.js`

![Create Scriptjs File](./image/file-scriptjs-output.PNG)

- In public folder, create a file named index.html;

`vi index.html`

![Create Index Html File](./image/index-html-create-file.PNG)

- Change the directory back up to Books:

`cd ..`

![Directory Change to Books](./image/change-directoty-to-books.PNG)

- Start the server by running this command:

`node server.js`

![Node Serverjs Run](./image/node-serverjs-output.PNG)

- The server is now up and running, we can connect it via port 3300. You can launch a separate Putty or SSH console to test what curl command returns locally.

`curl -s http://localhost:3300`

![Curl Http 3300](./image/curl-http-output.PNG)

- It shall return an HTML page, it is hardly readable in the CLI, but we can also try and access it from the Internet.

For this you need to open TCP port 3300 in your AWS Web Console for your EC2 Instance.

![Edit Inbound Rules 3300](./image/tcp-3300-output.PNG)

- You can find it in your AWS web console in EC2 details:

`curl -s http://169.254.169.254/latest/meta-data/public-ipv4`

![Retrieve public IP from Command line](./image/public-ip-from-command-line.PNG)

- This is how your Web Book Register Application will look like in browser:

[Server Url Success Lunch](http://18.216.255.120:3300/)

![Server URl launch](./image/server-success-output.PNG)