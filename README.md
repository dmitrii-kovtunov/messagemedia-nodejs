# MessageMedia NodeJS SDK
This library provides a simple interface for sending and receiving messages using the [MessageMedia SOAP API](http://www.messagemedia.com.au/wp-content/uploads/2013/05/MessageMedia_Messaging_Web_Service.pdf?eacfbb).

If you have any issue using this sample code, or would like to report a defect, you could [create a new Issue](https://github.com/messagemedia/messagemedia-nodejs/issues/new) in Github or [Contact us](http://www.messagemedia.com.au/contact-us).

## Installation:
Clone the repository into your application's *node_modules* directory.
```
$ git clone https://github.com/messagemedia/messagemedia-nodejs.git messagemedia
```

**OR**

Install it as a package from **npm** (Node Package Manager).
```
$ npm install messagemedia
```

**OR**

Create a **package.json** file in the project's root directory and add **messagemedia** as a dependency. You can refer to the one in this project's root directory. After this file is created you can run the following command...
```
$ npm install
```
## Usage:
### Project directory structure:
* **/lib** MessageMedia library.
* **/test** Contains test scripts called from **/test/tests.js**.
* **/sample** Contains a sample application.
* **/node_modules** Is created after running **$ npm install**.

#### This project was created using an IDE:

IDE: Eclipse Standard

Version: Kepler Service Release 2.

It is suggested that you install http://www.nodeclipse.org/ into Eclipse. This plugin allows you to interact with NodeJS from within Eclipse.

You do not need Eclipse or any IDE to use this library. You can get started with as little has 4 lines of code...

```javascript
// app.js
const mm = require('messagemedia');
mm.checkUser('userId', 'password', function(resp){
	console.log(resp);
});
```

### Sample REST based Web App:

![alt text](sample/screenshots/screenshot1.png "Screenshot 1")

To run the sample web application type the following command:

```node sample/app.js```

In **/sample** there is a sample web application that can be used to test/demonstrate the library. 

In your web-browser go to [http://localhost:3000/](http://localhost:3000/)

#### Major Parts:
* **Server** (NodeJS)
* **Client** (AngularJS)

This sample uses the Express web application framework package, on the NodeJS side.

The server (NodeJS) hosts a http server which serves a single-page for a web browser to access and a REST service. The REST service acts as a translation layer allowing two-way communication between MessageMedia's WSDL based SOAP API and this NodeJS's JSON based REST API. I have chosen to use AngularJS on the client (browser) because it is feature-rich and allows easy access to REST resources on the server.

The code snippet below shows how a very simple REST interface could be made to access MessageMedia's SOAP API via this library.
```javascript
var messagemedia = require('messagemedia');

app.post('/api/checkUser', function(req, res){
  messagemedia.checkUser(req.body.userId, req.body.password, function(result){
    res.send(result);
  });
});
```

### Unit Tests:
When attempting to run **/tests.js** for the first time you must...

* Create a **config.json** file in project root directory (use the **config.template.json** file as a template)
* Run ```$ npm install nodeunit -g```
* In ```/test``` execute ```$ nodeunit tests.js```

* **TC 1:** Checking
	* **TC 1.1:** Check User. 
	* **TC 1.2:** Check Replies
	* **TC 1.3:** Check Reports
* **TC 2:** Number Blocking
	* **TC 2.1:** Get blocked numbers.
	* **TC 2.2:** Block numbers(s).
	* **TC 2.3:** Unblock numbers(s).
* **TC 3:** Confirmations
	* **TC 3.1:** Confirm Replies.
	* **TC 3.2:** Confirm Reports.
* **TC 4:** Messages
	* **TC 4.1:** Send Messages.
	* **TC 4.2:** Delete Scheduled Messages.
	
Please note: The unit tests require an active MessageMedia account in order for them to function.

## Contributing

We welcome contributions from our users. Contributing is easy:

  1.  Fork this repo
  2.  Create your feature branch (`git checkout -b my-new-feature`)
  3.  Commit your changes (`git commit -am 'Add some feature'`)
  4.  Push to the branch (`git push origin my-new-feature`)
  5.  Create a Pull Request