---
title: API Reference

language_tabs:
- bash
- javascript

includes:

search: true

toc_footers:
- 
<a href='https://datacube.io'>Create an account</a>
<a href='http://github.com/mpociot/documentarian'>Documentation Powered by Documentarian</a>
---

# API Reference

Welcome to Datacube.io's API!

You can use this API to access all our API endpoints, such as the <a href="#user">User API</a> to look up email addresses, or the <a href="#backup">Backup API</a> to look up backup information.
The API is organized around <a href="http://en.wikipedia.org/wiki/Representational_State_Transfer">REST</a>. All requests should be made over SSL. All request and response bodies, including errors, are encoded in JSON.

We also have some specific language bindings to make integration easier. You can switch the programming language of the examples with the tabs in the top right.
To play around with a few examples, we recommend a REST client called Postman.

<a href="http://api.datacube.io/docs/collection.json">Get Postman Collection</a>

# Authentication


Authentication is done via the API key which you can find in your <a href="/profile">account settings</a> or 
by using the userLogin method.
Requests are authenticated using <a href="http://en.wikipedia.org/wiki/Basic_access_authentication">HTTP Basic Auth</a>.

Before getting your API's key, you need to register to <a href="https://datacube.io">Datacube.io</a>.
## Register

Used to register an user

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/user" \
-H "Accept: application/json" \
    -d "email"="muller.ocie@example.org" \
    -d "password"="qui" \
    -d "first_name"="qui" \
    -d "last_name"="qui" \
    -d "phone_number"="qui" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user",
    "method": "POST",
    "data": {
        "email": "muller.ocie@example.org",
        "password": "qui",
        "first_name": "qui",
        "last_name": "qui",
        "phone_number": "qui"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/user`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    email | email |  required  | 
    password | string |  required  | 
    first_name | string |  required  | 
    last_name | string |  required  | 
    phone_number | string |  required  | 

## Login

Used to login an user and get API's token

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/user/login" \
-H "Accept: application/json" \
    -d "email"="excepturi" \
    -d "password"="excepturi" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/login",
    "method": "POST",
    "data": {
        "email": "excepturi",
        "password": "excepturi"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/user/login`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    email | string |  required  | 
    password | string |  required  | 

<!-- END_7a184547882598fc164c10be7745584b -->

<!-- START_b69ba7ceb457587e7334b7b7b3815a5a -->
## Login with 2FA

Used to login an user with two factor auth and get API's token

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/user/logindouble" \
-H "Accept: application/json" \
    -d "email"="quod" \
    -d "password"="quod" \
    -d "code"="quod" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/logindouble",
    "method": "POST",
    "data": {
        "email": "quod",
        "password": "quod",
        "code": "quod"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/user/logindouble`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    email | string |  required  | 
    password | string |  required  | 
    code | string |  required  | 

# Errors

<p>Our API returns standard HTTP success or error status codes. For errors, we will also include extra information about what went wrong encoded in the response as JSON. The various HTTP status codes we might return are listed below.</p>
<h2 id='http-status-codes'>HTTP Status codes</h1>
<table><thead>
<tr>
<th>Code</th>
<th>Title</th>
<th>Description</th>
</tr>
</thead><tbody>
<tr>
<td>200</td>
<td>OK</td>
<td>The request was successful.</td>
</tr>
<tr>
<td>201</td>
<td>Created</td>
<td>The resource was successfully created.</td>
</tr>
<tr>
<td>202</td>
<td>Async created</td>
<td>The resource was asynchronously created</td>
</tr>
<tr>
<td>400</td>
<td>Bad request</td>
<td>Bad request</td>
</tr>
<tr>
<td>401</td>
<td>Unauthorized</td>
<td>Your API key is invalid.</td>
</tr>
<tr>
<td>402</td>
<td>Over quota</td>
<td>Over plan quota on this endpoint.</td>
</tr>
<tr>
<td>404</td>
<td>Not found</td>
<td>The resource does not exist.</td>
</tr>
<tr>
<td>422</td>
<td>Validation error</td>
<td>A validation error occurred.</td>
</tr>
<tr>
<td>50X</td>
<td>Internal Server Error</td>
<td>An error occurred with our API.</td>
</tr>
</tbody></table>
<h2 id='error-types'>Error types</h1>
<p>All errors are returned in the form of JSON with a type and optional message.</p>

<blockquote>
<p>Example error response.</p>
</blockquote>
<pre class="highlight json"><code><span class="w">  </span><span class="p">{</span><span class="w">
    </span><span class="nt">"error"</span><span class="p">:</span><span class="w"> </span><span class="p">{</span><span class="w">
      </span><span class="nt">"type"</span><span class="p">:</span><span class="w"> </span><span class="s2">"params_invalid"</span><span class="p">,</span><span class="w">
      </span><span class="nt">"message"</span><span class="p">:</span><span class="w"> </span><span class="s2">"Name is required"</span><span class="w">
    </span><span class="p">}</span><span class="w">
  </span><span class="p">}</span><span class="w">
</span></code></pre>

<table><thead>
<tr>
<th>Type</th>
<th>Description</th>
</tr>
</thead><tbody>
<tr>
<td>params_invalid</td>
<td>Your parameters were not valid.</td>
</tr>
<tr>
<td>unknown_record</td>
<td>Record was not found.</td>
</tr>
<tr>
<td>unknown_route</td>
<td>URL was not valid.</td>
</tr>
<tr>
<td>queued</td>
<td>Lookup queued. Try this request again in a few minutes.</td>
</tr>
<tr>
<td>rate_limit</td>
<td>The request has been rate limited.</td>
</tr>
<tr>
<td>api_error</td>
<td>Internal API error.</td>
</tr>
</tbody></table>


#Backup API

The Backup API let you handle all the task link to a backup.
For example you can retrieve the information of a backup or create a 
task to upload one.


## Retrieve a backup information

This Api endpoint let you retrieve the information of a current backup.

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/backup/{id}" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/backup/{id}",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/backup/{id}`

`HEAD api/v1/backup/{id}`


<!-- END_905fb15f2c83e2d6cb615a288395294a -->

<!-- START_4e80844fd62a1c2039ac4678fe554317 -->
## Destroy a Backup

Used to create a destroy task for a given backup

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/backup/{id}/destroy" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/backup/{id}/destroy",
    "method": "POST",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/backup/{id}/destroy`


## Download a backup

Used to create a download task for a given backup

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/backup/{id}/download" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/backup/{id}/download",
    "method": "POST",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/backup/{id}/download`


<!-- END_ee09e2d9c0c9ba8a4f8e652241912b7f -->

<!-- START_912475297b251b9dcbac95c4a48e5641 -->
## Get backup jobs

Used to fetch jobs from a given backup

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/backup/{id}/jobs" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/backup/{id}/jobs",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/backup/{id}/jobs`

`HEAD api/v1/backup/{id}/jobs`



## Get backup blocks

Used to fetch blocs from a given backup

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/backup/{id}/blocs" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/backup/{id}/blocs",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/backup/{id}/blocs`

`HEAD api/v1/backup/{id}/blocs`




#Block API

The Block API let you handle the management of block.
For example you can retrieve the information of a given block or create a 
task to upload one.

## Get a block

Used to fetch a given block

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/bloc/{id}" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/bloc/{id}",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/bloc/{id}`

`HEAD api/v1/bloc/{id}`


#Job API

The Job API let you handle the management of jobs.
For example you can retrieve the information of a given job.


## Get a job

Used to fetch a given job

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/job/{id}" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/job/{id}",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/job/{id}`

`HEAD api/v1/job/{id}`




#Service API

The Service API let you handle the management of backups contain in each services
For example you can create a service, get infromation or delete a service.
You can retrieve backup information from each service too.


## Get all services

Used to fetch all owned services

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/service" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/service",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/service`

`HEAD api/v1/service`


## Get a service

Used to fetch the given service

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/service/{id}" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/service/{id}",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/service/{id}`

`HEAD api/v1/service/{id}`


## Create a new service

Used to create and register a new service

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/service" \
-H "Accept: application/json" \
    -d "name"="deserunt" \
    -d "run_hour"="deserunt" \
    -d "run_day"="deserunt" \
    -d "type"="deserunt" \
    -d "access_host"="deserunt" \
    -d "access_port"="662689" \
    -d "access_username"="deserunt" \
    -d "access_password"="deserunt" \
    -d "access_name"="deserunt" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/service",
    "method": "POST",
    "data": {
        "name": "deserunt",
        "run_hour": "deserunt",
        "run_day": "deserunt",
        "type": "deserunt",
        "access_host": "deserunt",
        "access_port": 662689,
        "access_username": "deserunt",
        "access_password": "deserunt",
        "access_name": "deserunt"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/service`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    name | string |  required  | 
    run_hour | string |  required  | 
    run_day | string |  required  | 
    type | string |  required  | `git`, `ssh`, `ftp`, `mysql`, `postgresql` or `mongodb`
    access_host | string |  optional  | 
    access_port | numeric |  optional  | 
    access_username | string |  optional  | 
    access_password | string |  optional  | 
    access_name | string |  optional  | 

<!-- END_cb9d109b3c89cf7a39568a2825c74718 -->

<!-- START_a34dccf0b80f62b3b69194b4ba55e056 -->
## Update a service

Used to update a given service

> Example request:

```bash
curl -X PUT "http://api.datacube.io/api/v1/service/{id}" \
-H "Accept: application/json" \
    -d "name"="aliquam" \
    -d "run_hour"="aliquam" \
    -d "run_day"="aliquam" \
    -d "notification_email"="aliquam" \
    -d "notification_sms"="aliquam" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/service/{id}",
    "method": "PUT",
    "data": {
        "name": "aliquam",
        "run_hour": "aliquam",
        "run_day": "aliquam",
        "notification_email": "aliquam",
        "notification_sms": "aliquam"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`PUT api/v1/service/{id}`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    name | string |  optional  | 
    run_hour | string |  optional  | 
    run_day | string |  optional  | 
    notification_email | string |  optional  | 
    notification_sms | string |  optional  | 

<!-- END_a34dccf0b80f62b3b69194b4ba55e056 -->

<!-- START_45f418a3960b4fb6eb728750729325af -->
## Destroy a service

Used to destroy a given service

> Example request:

```bash
curl -X DELETE "http://api.datacube.io/api/v1/service/{id}" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/service/{id}",
    "method": "DELETE",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`DELETE api/v1/service/{id}`


<!-- END_45f418a3960b4fb6eb728750729325af -->

<!-- START_b634dccc272149b0cfdaa8e645e08907 -->
## Get backups of a service

Used to fetch the backups of the given service

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/service/{id}/backups" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/service/{id}/backups",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/service/{id}/backups`

`HEAD api/v1/service/{id}/backups`


<!-- END_b634dccc272149b0cfdaa8e645e08907 -->

<!-- START_50a8a9c56a26cc50c0c763fe0863dbbf -->
## Run a backup

Run a standalone backup task on the given service

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/service/{id}/backup" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/service/{id}/backup",
    "method": "POST",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/service/{id}/backup`


<!-- END_50a8a9c56a26cc50c0c763fe0863dbbf -->

#Support API

The Support API let you handle all the task link to the support
For example you can create ticket, get information about one etc...


## Get services list

Used to fetch the services list

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/support/services" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/services",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/support/services`

`HEAD api/v1/support/services`


<!-- END_7dd3d94a878c6b30daa227a04c5916a2 -->

<!-- START_bedccbed6f0b6e01df10601e69b17cb8 -->
## Get categories list

Used to fetch the list of support categories

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/support/categories" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/categories",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/support/categories`

`HEAD api/v1/support/categories`


<!-- END_bedccbed6f0b6e01df10601e69b17cb8 -->

<!-- START_ac397b253e09cc0e63c0f3b9abe0923b -->
## Get a category

Used to fetch a specified category

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/support/category/{id}" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/category/{id}",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/support/category/{id}`

`HEAD api/v1/support/category/{id}`


<!-- END_ac397b253e09cc0e63c0f3b9abe0923b -->

<!-- START_6449fa77bebe56c67ca88927fc4e74e9 -->
## Get tickets

Used to fetch the list of tickets

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/support/tickets" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/tickets",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/support/tickets`

`HEAD api/v1/support/tickets`


<!-- END_6449fa77bebe56c67ca88927fc4e74e9 -->

<!-- START_918a7439fcce89af18cef6bb74356fe3 -->
## Get a ticket

Used to fetch a specified ticket

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/support/ticket/{id}" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/ticket/{id}",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/support/ticket/{id}`

`HEAD api/v1/support/ticket/{id}`


<!-- END_918a7439fcce89af18cef6bb74356fe3 -->

<!-- START_0d23c568a1be885c3a245d3b20cb43cb -->
## Create a ticket

Used to create a new ticket

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/support/ticket" \
-H "Accept: application/json" \
    -d "category_id"="et" \
    -d "service_id"="et" \
    -d "title"="et" \
    -d "message"="et" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/ticket",
    "method": "POST",
    "data": {
        "category_id": "et",
        "service_id": "et",
        "title": "et",
        "message": "et"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/support/ticket`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    category_id | string |  required  | 
    service_id | string |  optional  | 
    title | string |  required  | 
    message | string |  required  | 


## Answser to a ticket

Used to answer to the specified ticket

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/support/ticket/{id}/answer" \
-H "Accept: application/json" \
    -d "message"="temporibus" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/ticket/{id}/answer",
    "method": "POST",
    "data": {
        "message": "temporibus"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/support/ticket/{id}/answer`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    message | string |  required  | 


## Close a ticket

Used to close the specified ticket

> Example request:

```bash
curl -X PUT "http://api.datacube.io/api/v1/support/ticket/{id}/close" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/ticket/{id}/close",
    "method": "PUT",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`PUT api/v1/support/ticket/{id}/close`


## Open a ticket

Used to open the specified ticket

> Example request:

```bash
curl -X PUT "http://api.datacube.io/api/v1/support/ticket/{id}/open" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/support/ticket/{id}/open",
    "method": "PUT",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`PUT api/v1/support/ticket/{id}/open`


<!-- END_df1c86d48ecd1260af41b561584ad7f7 -->

#User API

The User API let you handle all the task link to the user.
For example you can retrieve the information of a given user or register
a user.

<!-- START_b2892eb191cd19c0a6f1aae56ba43db4 -->
## Get a user information

Used to fetch informations about the current user

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/user" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/user`

`HEAD api/v1/user`


## Change password

Used to update password of the current user

> Example request:

```bash
curl -X PUT "http://api.datacube.io/api/v1/user/password" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/password",
    "method": "PUT",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`PUT api/v1/user/password`


## Generate a new password

Used to ask for a new password

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/user/forgot" \
-H "Accept: application/json" \
    -d "email"="maximilian.kessler@example.org" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/forgot",
    "method": "POST",
    "data": {
        "email": "maximilian.kessler@example.org"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/user/forgot`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    email | email |  required  | 


## Initialise 2FA
Used to init the user double authentication

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/user/google/init" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/google/init",
    "method": "POST",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/user/google/init`


## Verify 2FA

Used to verify the user double authentication

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/user/google/verify" \
-H "Accept: application/json" \
    -d "code"="omnis" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/google/verify",
    "method": "POST",
    "data": {
        "code": "omnis"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/user/google/verify`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    code | string |  required  | 


## Disable 2FA

Used to disable the user double authentication

> Example request:

```bash
curl -X POST "http://api.datacube.io/api/v1/user/google/disable" \
-H "Accept: application/json" \
    -d "code"="ut" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/google/disable",
    "method": "POST",
    "data": {
        "code": "ut"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`POST api/v1/user/google/disable`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    code | string |  required  | 

<!-- END_1b03a396e77005d277b6741a9333677a -->

<!-- START_87b8b15c67c936bfd4fa162088389ebd -->
## Get stats

Used to fetch global user's stats

> Example request:

```bash
curl -X GET "http://api.datacube.io/api/v1/user/stats" \
-H "Accept: application/json"
```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/stats",
    "method": "GET",
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```

> Example response:

```json
{
    "result": [],
    "message": "Missing X-API-KEY header",
    "code": 418
}
```

### HTTP Request
`GET api/v1/user/stats`

`HEAD api/v1/user/stats`


## Get a card

> Example request:

```bash
curl -X PUT "http://api.datacube.io/api/v1/user/card" \
-H "Accept: application/json" \
    -d "token"="magni" \

```

```javascript
var settings = {
    "async": true,
    "crossDomain": true,
    "url": "http://api.datacube.io/api/v1/user/card",
    "method": "PUT",
    "data": {
        "token": "magni"
},
    "headers": {
        "accept": "application/json"
    }
}

$.ajax(settings).done(function (response) {
    console.log(response);
});
```


### HTTP Request
`PUT api/v1/user/card`

#### Parameters

Parameter | Type | Status | Description
--------- | ------- | ------- | ------- | -----------
    token | string |  required  | 


