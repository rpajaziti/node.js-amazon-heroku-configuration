Node.js configurations, platforms, deployment etc.
========

 1. [Introduction](https://github.com/RamadanPajaziti/nodeConfigDoc#installation)
 2. [Installation](https://github.com/RamadanPajaziti/nodeConfigDoc#Installation)
 3. [Working with node.js applications in localhost(without any service)](https://github.com/RamadanPajaziti/nodeConfigDoc#working-with-nodejs-applications-in-localhostwithout-any-service)
 4. [Working with applications in node.js](https://github.com/RamadanPajaziti/nodeConfigDoc#working-with-applications-in-nodejs)
 5. [Configuration and deployment to Heroku](https://github.com/RamadanPajaziti/nodeConfigDoc#configuration-and-deployment-to-heroku)
 6. [Configuration and adding AWS RDS instances](https://github.com/RamadanPajaziti/nodeConfigDoc#configuration-and-adding-aws-rds-instances)
 7. [Configuration and adding AWS Elastic Beanstalk application/environment](https://github.com/RamadanPajaziti/nodeConfigDoc#configuration-and-adding-aws-elastic-beanstalk-applicationenvironment)
 


### Introduction

[Node.js®](https://nodejs.org/en/) is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.

[Projects, Applications, and Companies Using Node.](https://github.com/nodejs/node-v0.x-archive/wiki/Projects,-Applications,-and-Companies-Using-Node)


### Installation

 1. First download and install node.js
[Download](https://nodejs.org/)
 2. Download a text editor
 I Recommend using [notepad++](https://notepad-plus-plus.org/) | [sublime](http://www.sublimetext.com/), because they are free to use and great text editors.
 3. [Download](https://toolbelt.heroku.com/) Heroku Toolbelt(used to config and deploy heroku apps)


### Working with node.js applications in localhost(without any service)

 1. First you should download,install and configure MySQL WorkBench to create a localhost with a database.
* [Download.](http://dev.mysql.com/downloads/windows/installer/)
* [Install and use!](https://www.youtube.com/watch?v=N039SxEpvW0)

 2. Open localhost instance after you open MySQL WorkBench, and create any table you want. 
 So now you have a database instance where you can create databases, create table inside them, also you can add another database from aws RDS services or from somewhere else. You just click + sign in MySQL WorkBench and enter data's of online RDS(endpoint, username, password, database etc).
 
 3. If you want to configure a node.js application to have the possibility to run both localhost and in a service(Elastic Beanstalk, Heroku etc), when you write `app.listen(port)`, you should set port like `var port = proccess.env.PORT || 3000;` where proccess.env.PORT is whatever is in the environment variable PORT or 3000 if there is nothing in there.
 
 4. After you finish task 3, open command prompt in the folder you have you `.js` file. There write `node file_name.js` and it runs application.
 
 5. Then go to the browser and write `localhost:3000` and it opens what you programmed in your node application.
 
 TIP: When you create a localhost by launching you application, be careful not to work on that same CMD windows, because you can try opening same application in another CMD window, and it wont work, because port:3000 is already opened, and it will show an error, which will result in minutes and maybe hours spend to try and fix that.

### Working with applications in node.js

 1. Very simple node application that display's [helloworld](http://expressjs.com/starter/hello-world.html).
 
 2. To run applications on different service or to make applications that require user input, we will need modules, which are not pre-installed because there are alot of modules which you will need to install the module you use it.
 
 3. Installing modules can be made in two ways:
 
 * First way, you open command prompt in the folder you have your file, then write npm init, and this creates a file called package.json, which then you add a property(object) called `"dependencies"`, where you put your modules plus the version of them, if you dont know what version it has you just write `'*'` in the value of a property.
 After that you write npm install to install all the modules located in package.json file in dependencies property.
 Dependencies in a file with some most used modules will look like this:
```javascript
  {
    "name": "node-api",
    "main": "index.js",
    "dependencies": {
      "body-parser": "~1.6.2",
      "express": "~4.13.1",
      "http": "~0.0.0",
      "mysql": "*",
    },
    ...
   }
```
 * Second way is to first write npm init in the folder you want to install modules, then write `npm install name_of_the_module version --save`(if you want the latest dont write the version word), and this installs and saves the property name and version of the module in dependencies.


### Configuration and deployment to Heroku

* First after you install Heroku toolbelt, open the command prompt and write heroku login where you pass your username and password.
Everything you can find it here, how to config, deploy and edit heroku apps. 
[Getting started with Heroku](https://devcenter.heroku.com/articles/getting-started-with-nodejs#deploy-the-app)

* PS: In the 4th step(Getting started with Heroku), when you create an heroku app, if you want to create that app with a specific name, just type:
`heroku create your_name` , and this creates an application with your_name.herokuapp.com
Heroku works with most RDS Databases, but supports best PostgreSQL Database and it is less painful, and better if you want to deploy apps in heroku, to work with PostgreSQL.

### Configuration and adding AWS RDS instances


 Note: After you open an AWS account and add a credit card just for activating. 
 Be careful after you add a credit card if you want to use just the free tier that Amazon offers. Choose only the lowest settings, because if you select something like:
 
* In MySQL RDS you should select the lowest settings, like lowest cpu option(t2.micro), small amount of HDD, storage type - Magnetic, and select No to Multi-AZ.

* In Elastic Beanstalk in the option Environment type: select Single instance.

 1. Select Services Top left, then select RDS. After you select RDS Select the database you want(MySQL in our example), select other options but always remembering not to select anything wrong, because it can take spend of your money.
 
 2. Important: After you create an MySQL RDS Instance, this service by default it puts your IP in the white list in the FireWALL of aws RDS, and it lets only your PC with that IP to have access to your MySQL RDS instance. You should modify this to have access everyone to this instance, or you to have access from anywhere. This it sounds dangerous but it isnt, because if someone wants to have access to your instance, it needs alot of details(endpoint, user, password, database).
 
 3. Configuring IP: 
 First expand MySQL RDS Instance, then next to EndPoint Link there is (authorized) and next to it is an info icon. Hover mouse uppon info   icon then click the Security Group rule(the blue link) to modify the exact Security Group.
 After you click that link it opens a new tab with Security Groups Instances, in the bottom of the browser select Inbound and click Edit, and in MySQL row in the Source column change down-menu to Anywhere, and IP automaticaly changes to 0.0.0.0/0, this gives access to use RDS instance from any IP.
 
 4. If you want to use this instance in some node.js application, or to config/add/delete databases/tables, you need log-in details of RDS instance. To see these details you should expand your RDS instance, and click instance Actions, then See details. Then all details are found there, except the password. Password is set in the beggining of the instance creation.


### Configuration and adding AWS Elastic Beanstalk application/environment

 1. To deploy Node.js applications, Elastic Beanstalk is a great service to use, and it is really stable. 
 Select Node.js application to deploy, then click Launch now. This creates node.js application, but still you should create an environment
 You should set Environment type to Single instance, because if you set to Load-Balancing, then if application needs more resources, it uses them and in this way, money spent it increases alot. If you dont see this settings option then after your environment is finished creating, in the left side of Environment, click Configuration then in scaling click the settings button to change the environment type to single instance.
 
 2. There are two options to deploy applications in Elastic Beanstalk:
 
 * Deploy application using Elastic Beanstalk in browser, by first Zip-ing your application, then click Upload and Deploy, find the zip file, and set a unique name every time you deploy application here. 
 
 * Deploy application ussing CLI commands in command prompt. In the application folder, open command prompt, by holding shift and clicking the right mouse click, open command prompt. Then write `eb init` and enter, then select the region you have set in you AWS account. Then click the environment you want to deploy this application(number) and hit enter. After all these, when you are prompted to log-in, enter your log-in details. aws-access-key-id and aws_secret_access_key are found in Security Credentials in Top of the page in your account name.
 When you click that if you are prompted with something, click Continue to Security Credentials and then click Access Keys (Access Key ID and Secret Access Key), then Create a new Key(or some other word) then copy that and paste in command prompt what it asks(aws-access-key-id then aws_secret_access_key).
 After you are logged in and selected environment, write `git add .`(if you see some warning or something write git add --all to deploy all changes without a warning), then write `git commit -m "your_message_here"`, and last one write `eb deploy` to deploy your application to your environment.
 TIP 1: If you want to change the environment, because you have created another environment, delete the folder ".elasticbeanstalk", and repeat all steps told above. 
 TIP 2: If you want to have two AWS Accounts to deploy application, without messing around alot, you can add the second account into ".aws' folder, then open "config" file inside that folder with wordpad or some other text editor and add the other profile to "config" file.
 Other profile should be named different from first account. A config file with two accounts looks like this:
```shell
 [profile eb-cli]
 aws_access_key_id = AKI******************
 aws_secret_access_key = xxd5****************************
 [profile eb-cli2]
 aws_access_key_id = AKI*****************
 aws_secret_access_key = xxd5********************************
```
 * Now the default profile is eb-cli, and if you want to select the second profile, when you should delete ".elasticbeanstalk" file, then write `eb init profile eb-cli2`(or some other profile), then follow the steps above.
 So every time you want to deploy your application, you follow the steps above, without the `eb init` command. 
 