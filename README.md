# Principles of web development

**Node.js**

	Node.js app runs in a single process, without creating a new thread for every request.

	The server is set to listen on the specified port and host name.

	The default name of the main file is index.js. 

**Express**

	Use the npm init command to create a package.json file for your application.

	```

	$ npm init

	```

	The app starts a server and listens on port 3000 for connections.

	```

	$ node index.js

	```
	Express supports methods that correspond to all HTTP request methods such GET, POST, and so on. 

	```

	const express = require('express')
	const app = express()
	const port = 3000

	app.get('/', (req, res) => {
	  res.send('Hello World!')
	})

	app.listen(port, () => {
	  console.log(`app listening at http://localhost:${port}`)
	})

	```

**Dockerfile**

	Docker lets you to package an application with its environment and all of its dependencies into a container.

	Run npm install to generate a package-lock.json file which will be copied to the Docker image.

	Define from what image we want to build from in Dockerfile, for example node available from the Docker Hub.

	Use WORKDIR instruction to create a directory to store the application code inside the image, which will be the working directory for your application.

	Use COPY instruction to bundle the app's source code inside the Docker image.

	Define the command to run the app using CMD instruction which defines the runtime.  

	```

	FROM node:14

	WORKDIR /usr/src/app

	COPY package*.json ./

	RUN npm ci

	COPY . .

	EXPOSE 3001

	CMD ["npm", "start"]

	```

	Create a .dockerignore file in the same directory as the Dockerfile to prevent the local modules and debug logs from being copied onto the Docker image.

	Build the Docker image by the following command.

	```

	$ docker build . -t <USERNAME>/<APP_NAME>

	```
	Run the image with -d option for detached mode, leaving the container running in the background. 

	The -p flag redirects a public port to a private port inside the container. 

	The -t flag lets you tag the image.

**XMLHttpRequest**

	XMLHttpRequest (XHR) objects are used to interact with servers.

	An event handler for event onreadystatechange is defined for the xhttp object doing the request.

	The request to the server is sent by send() method, but the code to handle the response uses onreadystatechange method.

	```

	var xhttp = new XMLHttpRequest()

	xhttp.onreadystatechange = function() {
	  // The server response
	}

	xhttp.open('GET', '/data.json', true)
	xhttp.send()

	```

**HTTP**

	Hypertext Transfer Protocol (HTTP) is an application-layer protocol to transmit hypermedia documents, such as HTML.

	The server and the web browser communicate with each other using the HTTP protocol.

	The browser sends an HTTP GET request to the server to fetch the HTML code of the page.

	The browser renders the HTML page and the image to the screen.

	The browser fetches the HTML code defining the content and the structure of the page from the server using an HTTP GET request.

	The server can access the data by accessing the req.body field of the request object req.

	```

	app.post('/note', (req, res) => {
	  notes.push({
	    content: req.body.note,
	    date: new Date(),
	  })

	  return res.redirect('/notes')
	})

	```
**Cross-Origin Resource Sharing**

	Cross-Origin Resource Sharing (CORS) is an HTTP-header based rule that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources.

	A web application using XMLHttpRequest or Fetch APIs can only request resources from the same origin the application was loaded from unless the response from other origins includes the right CORS headers.

**Headers**

	HTTP headers let the client and the server pass additional information with an HTTP request or response.

	A request header is an HTTP header that can be used in an HTTP request to provide information about the request context.

	A response header is an HTTP header that can be used in an HTTP response and that doesn't relate to the content of the message.

**Event handlers**

	Event handler functions are called callback functions. 

 	An event handler for the event is defined for the object doing the request.

 	When the state of the object changes, the browser calls the event handler function.

**Callback functions**

	Node.js uses asynchronous callback functions and a callback function is called at the completion of a task.

	A callback function is a function you pass into another function so that function can call it at a later time.

	Asynchronous callback functions replace the use of the return instruction.

	Using asynchronous callback functions, we can run other fucntions while the function is waiting for activities like network requests to finish.

	An example callback function using setTimeout function.

```

var callback = function () {

  console.log("A second later")
}

setTimeout(callback, 1000)

```

**Document Object Model**

	Document Object Model (DOM), is an Application Programming Interface (API) which enables programmatic modification of the element trees corresponding to web pages.

**Cascading Style Sheets**

	Cascading Style Sheets (CSS) are used to describe the appearance of Web content.

**Single-page application (SPA)**

	Single-page application (SPA) is a web app implementation that loads only a single web document, and then updates the body content of that single document via JavaScript APIs such as XMLHttpRequest and Fetch when different content is to be shown on the document.

A link to Mozilla's web technology for software developers. 

https://developer.mozilla.org/en-US/docs/Web
