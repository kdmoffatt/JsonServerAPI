This programming test is requires JSON Server to load the JSON file as RESTful API calls [GET, POST, PUT, PATCH, DELETE]

# Installing JSON Server
JSON Server is available as a NPM package. The installation can be done by using the Node.js package manager:

_$ npm install -g json-server_

By adding the -g option we make sure that the package is installed globally on your system.

# Running The Server
Let’s start JSON server by executing the following command:

_$ json-server --watch db.json_

As a parameter we need to pass over the file containing our JSON structure (db.json). Furthermore we’re using the — watch parameter. By using this parameter we’re making sure that the server is started in watch mode which means that it watches for file changes and updates the exposed API accordingly.

# Opening The Server
Now we can open URL http://localhost:3000/ in the browser and we’ll get the following result:

From the output you can see that the employees resource has been recognized correctly. Now you can click on the billers link and a HTTP GET request to http://localhost:3000/Billers shows the following result:

"Billers":\[
		{"id":1, "biller":"Flow(Lime)", "servicefee":3.00},
		{"id":2, "biller":"Jamiaca Public Service (JPS)", "servicefee":5.00},
		{"id":3, "biller":"National Water Commission (NWC)", "servicefee":10.00},
		{"id":4, "biller":"Digicel", "servicefee":120.00},
		{"id":5, "biller":"Sagicor Life", "servicefee":250.00},
		{"id":6, "biller":"Appsession", "servicefee":260.00}
	\]

The following HTTP endpoints are created automatically by JSON server:

GET    /employees
GET    /employees/{id}
POST   /employees
PUT    /employees/{id}
PATCH  /employees/{id}
DELETE /employees/{id}

If you make POST, PUT, PATCH or DELETE requests, changes will be automatically saved to db.json. A POST, PUT or PATCH request should include a Content-Type: application/json header to use the JSON in the request body. Otherwise it will result in a 200 OK but without changes being made to the data.
 
 It's possible to extend URLs with further parameter. E.g. you can apply filtering by using URL parameters like you can see in the following:
 
 _http://localhost:3000/Billers?biller=Digicel_
 
 This returns just one Biller object as a result. Or just perform a full text over all properties:
 
 _http://localhost:3000/Billers?q=codingthesmartway_
 
 For a full list of available URL parameters take a look at the JSON server documentation: https://github.com/typicode/json-server
