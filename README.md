Node.js configurations, platforms, deployment etc.
========

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

 1. Select Services Top left, then select RDS. After you select RDS Select the database you want(MySQL in our example), select other options but always remembering not to select anything wrong, because it can steal alot of your money.
 
 2. Important: After you create an MySQL RDS Instance, this service by default it puts your IP in the white list in the FireWALL of aws RDS, and it lets only your PC with that IP to have access to your MySQL RDS instance. You should modify this to have access everyone to this instance, or you to have access from anywhere. This it sounds dangerous but it isnt, because if someone wants to have access to your instance, it needs alot of details(endpoint, user, password, database).
 * Configuring IP: 
 First expand MySQL RDS Instance, then next to EndPoint Link there is (authorized) and next to it is an info icon. Hover mouse uppon info   icon then click the Security Group rule(the blue link) to modify the exact Security Group.
 After you click that link it opens a new tab with Security Groups Instances, in the bottom of the browser select Inbound and click Edit,   then in Source column change down-menu
 
 3. 








Features
------------

* **Clean, intuitive design** — with Slate, the description of your API is on the left side of your documentation, and all the code examples are on the right side. Inspired by [Stripe's](https://stripe.com/docs/api) and [Paypal's](https://developer.paypal.com/webapps/developer/docs/api/) API docs. Slate is responsive, so it looks great on tablets, phones, and even print.

* **Everything on a single page** — gone are the days where your users had to search through a million pages to find what they wanted. Slate puts the entire documentation on a single page. We haven't sacrificed linkability, though. As you scroll, your browser's hash will update to the nearest header, so linking to a particular point in the documentation is still natural and easy.

* **Slate is just Markdown** — when you write docs with Slate, you're just writing Markdown, which makes it simple to edit and understand. Everything is written in Markdown — even the code samples are just Markdown code blocks!

* **Write code samples in multiple languages** — if your API has bindings in multiple programming languages, you easily put in tabs to switch between them. In your document, you'll distinguish different languages by specifying the language name at the top of each code block, just like with Github Flavored Markdown!

* **Out-of-the-box syntax highlighting** for [almost 60 languages](http://rouge.jayferd.us/demo), no configuration required.

* **Automatic, smoothly scrolling table of contents** on the far left of the page. As you scroll, it displays your current position in the document. It's fast, too. We're using Slate at TripIt to build documentation for our new API, where our table of contents has over 180 entries. We've made sure that the performance remains excellent, even for larger documents.

* **Let your users update your documentation for you** — by default, your Slate-generated documentation is hosted in a public Github repository. Not only does this mean you get free hosting for your docs with Github Pages, but it also makes it's simple for other developers to make pull requests to your docs if they find typos or other problems. Of course, if you don't want to, you're welcome to not use Github and host your docs elsewhere!

Getting starting with Slate is super easy! Simply fork this repository, and then follow the instructions below. Or, if you'd like to check out what Slate is capable of, take a look at the [sample docs](http://tripit.github.io/slate).

<!--As an example, you can check out the [TripIt API docs](http://tripit.github.io/api), which we create with Slate. You can also view the source of the [markdown file used to generate it](http://github.com/tripit/api/blob/master/source/index.md).-->

Getting Started with Slate
------------------------------

### Prerequisites

You're going to need:

 - **Linux or OS X** — Windows may work, but is unsupported.
 - **Ruby, version 1.9.3 or newer**
 - **Bundler** — If Ruby is already installed, but the `bundle` command doesn't work, just run `gem install bundler` in a terminal.

### Getting Set Up

 1. Fork this repository on Github.
 2. Clone *your forked repository* (not our original one) to your hard drive with `git clone https://github.com/YOURUSERNAME/slate.git`
 3. `cd slate`
 4. Install all dependencies: `bundle install`
 5. Start the test server: `bundle exec middleman server`

Or use the included Dockerfile! (must install Docker first)

```shell
docker build -t slate .
docker run -d -p 4567:4567 slate
```

You can now see the docs at <http://localhost:4567>. Whoa! That was fast!

*Note: if you're using the Docker setup on OSX, the docs will be
availalable at the output of `boot2docker ip` instead of `localhost:4567`.*

Now that Slate is all set up your machine, you'll probably want to learn more about [editing Slate markdown](https://github.com/tripit/slate/wiki/Markdown-Syntax), or [how to publish your docs](https://github.com/tripit/slate/wiki/Deploying-Slate).

Examples of Slate in the Wild
---------------------------------

* [Travis-CI's API docs](http://docs.travis-ci.com/api/)
* [Mozilla's localForage docs](http://mozilla.github.io/localForage/)
* [Mozilla Recroom](http://mozilla.github.io/recroom/)
* [ChaiOne Gameplan API docs](http://chaione.github.io/gameplanb2b/#introduction)
* [Drcaban's Build a Quine tutorial](http://drcabana.github.io/build-a-quine/#introduction)
* [PricePlow API docs](https://www.priceplow.com/api/documentation)
* [Emerging Threats API docs](http://apidocs.emergingthreats.net/)
* [Appium docs](http://appium.io/slate/en/master)
* [Golazon Developer](http://developer.golazon.com)
* [Dwolla API docs](https://docs.dwolla.com/)
* [RozpisyZapasu API docs](http://www.rozpisyzapasu.cz/dev/api/)
* [Codestar Framework Docs](http://codestarframework.com/documentation/)
* [Buddycloud API](http://buddycloud.com/api)
* [Crafty Clicks API](https://craftyclicks.co.uk/api/)
* [Paracel API Reference](http://paracel.io/docs/api_reference.html)
* [Switch Payments Documentation](http://switchpayments.com/docs/) & [API](http://switchpayments.com/developers/)
* [Coinbase API Reference](https://developers.coinbase.com/api)
* [Whispir.io API](https://whispir.github.io/api)
* [NASA API](https://data.nasa.gov/developer/external/planetary/)
* [CardPay API](https://developers.cardpay.com/)
* [IBM Cloudant](https://docs-testb.cloudant.com/content-review/_design/couchapp/index.html)
* [Bitrix basis components](http://bbc.bitrix.expert/)
* [viagogo API Documentation](http://developer.viagogo.net/)
* [Fidor Bank API Documentation](http://docs.fidor.de/)
* [Market Prophit API Documentation](http://developer.marketprophit.com/)
* [OAuth.io API Documentation](http://docs.oauth.io/)
* [Aircall for Developers](http://developer.aircall.io/)
* [SupportKit API Docs](http://docs.supportkit.io/)

(Feel free to add your site to this list in a pull request!)

Need Help? Found a bug?
--------------------

Just [submit a issue](https://github.com/tripit/slate/issues) to the Slate Github if you need any help. And, of course, feel free to submit pull requests with bug fixes or changes.


Contributors
--------------------

Slate was built by [Robert Lord](https://lord.io) while at [TripIt](http://tripit.com).

Thanks to the following people who have submitted major pull requests:

- [@chrissrogers](https://github.com/chrissrogers)
- [@bootstraponline](https://github.com/bootstraponline)
- [@realityking](https://github.com/realityking)

Also, thanks to [Sauce Labs](http://saucelabs.com) for helping sponsor the project.

Special Thanks
--------------------
- [Middleman](https://github.com/middleman/middleman)
- [jquery.tocify.js](https://github.com/gfranko/jquery.tocify.js)
- [middleman-syntax](https://github.com/middleman/middleman-syntax)
- [middleman-gh-pages](https://github.com/neo/middleman-gh-pages)
- [Font Awesome](http://fortawesome.github.io/Font-Awesome/)
