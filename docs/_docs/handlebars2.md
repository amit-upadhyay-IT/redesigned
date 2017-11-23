---
title: Handlebars Engine Cont.
permalink: /docs/handlebars2/
---

Now after writing the different routes to the applicatoin, lets write the `views`. As we have seen in the `routes.js` that we need `login.handlebars`, `landingpage.handlebars`, `city.handlebars`. We may also need a default layout, so for that I will also create `layout.handlebars` this will get open when the handlebars will get initialized for the first time.

Lets say that we have seperated the common code from `login.handlebars`, `landingpage.handlebars` and `city.handlebars` and put them into `partials`.

{: .unreleased .note}
**partials code**<br>file path: `./views/partials/includeHead.handlebars`

```html
    <meta charset="utf-8">
    <title>The Earth Hub</title>
    <link rel="icon" href="/images/favicon.ico" type="image/x-icon">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap-theme.min.css">
    <link  type="text/css" rel="stylesheet"  href="/styles.css" />
	<script src="https://use.edgefonts.net/lobster-two.js"></script>

```

{: .unreleased .note}
**partials code**<br>file path: `./views/partials/includeMenu.handlebars`

```html
<div class="container">
<header>
<h2 class="cursive-text-large" align="center"> The Transport Hub </h2>
</header>
</div>
<div class="navbar navbar-inverse ">
      <div class="container">
          <div class="navbar-header">
            <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
              <span class="icon-bar" ></span>
              <span class="icon-bar" ></span>
              <span class="icon-bar" ></span>
           </button>
          </div>

          <div class="navbar-collapse collapse">
              <ul class="nav navbar-nav">
              { {#if LOGGEDIN}}
                <li><a href="/toLanding"><span class="glyphicon glyphicon-random"> Hub</span></a></li>
                <li><a href="/logout"><span class="glyphicon glyphicon-log-out"> Logout</span></a></li>  
              { {else}}
                <li><a href="/"><span class="glyphicon glyphicon-log-in"> Login</span></a></li>
              { {/if}}
              </ul>
          </div>
      </div>
</div>
```

{: .unreleased .note}
**partials code**<br>file path: `./views/partials/includeFoot.handlebars`

```html
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>
```

{: .unreleased .note}
**partials code**<br>file path: `./views/city.handlebars`

```html
<div class="container">
<h3 class="cursive-text-small" align="center">Hi {{welcomeMessage}}!, You are in the city of {{cityName}}. {{tagline}}.</h3>
  <div class="row">
    {{#each imageArray}}
       <div class="col-md-6">
          <img src="/images/{{../cityName}}{{this}}.jpg" 
          width="400" 
          class="img-circle"/>
       </div>
    {{/each}}
  </div>
</div> 
```


{: .unreleased .note}
**partials code**<br>file path: `./views/landingpage.handlebars`

```html
<div class="container">
  <div class="row">
    <div class="col-md-6 col-md-offset-0 panel panel-default">
      <p class="help-block text-center cursive-text-small">
          Hi {{welcomeMessage}}!, Depending on your interest, I'll take you to a city.  
      </p>
      <form class="margin-base-vertical" method="post" action="/toCity" role="form">
        <div class="form-group"> 
          <label for="interest" class="cursive-text-small">What's your interest?</label>
          <select  required class="form-control" name="interest" id="interest" >
            <option value="finance">Business</option>
            <option value="fashion">Fashion</option>
            <option value="history">History</option>
          </select>
        </div>
        <p class="text-center">
          <button type="submit" class="btn btn-success btn-lg">Submit</button>
        </p>
      </form>
    </div>
  </div>
</div>
```

{: .unreleased .note}
**partials code**<br>file path: `./views/login.handlebars`

```html
<div class="container">
  <div class="row">
    <div class="col-md-4 col-md-offset-0 panel panel-default">
      <h1 align="center" class="margin-base-vertical">Sign In</h1>
      <form class="margin-base-vertical" method="get" action="/toLanding">
        <p class="input-group ">
          <span class="input-group-addon"><span class="glyphicon glyphicon-user"></span></span>
          <input type="text" required class="form-control input-lg" name="nm" placeholder="username" />
        </p>
        <p class="help-block text-center">
          <small>Please login to use the Transport Hub</small>
        </p>
        <p class="text-center">
          <button type="submit" class="btn btn-success btn-lg">Sign-In</button>
        </p>
      </form>
    </div>
  </div>
</div>
```



{: .info .note}
**What is Handlebars Templating Engine?**<br>Handlebars is widely used templating engine. Handlebars templates look like regular `HTML`, with `embedded handlebars expressions`.


```html
<div class="entry">
  <h1>
    <code>{ { title }}</code>
  </h1>
  <div class="body">
    { {body}}
  </div>
</div>
```

Here `{ {title}}` and `{ {body}}` are `Handlebars expressions`.

**NOTE**:
- Use double curly braces when you want to escape HTML.
- Use triple curly braces when you don’t want to escape HTML.

Handlebars is a bit similar to EJS template engine in structure and uses HTML markup syntax. Handlebars offers built in helpers and you can create your own helpers, Handlebars offers partials which allow for code reuse.

Handlebars comes with some very useful built in helpers like `each`, `with`, `if`, `unless` etc. `each` helper is used to `loop` through array elements.

Lets write an application using Handlebars. Handlebars syntax is little simpler than Jade.


{: .note}
**What our application will do?**<br>It will first ask for user login, after the the user will be directed to a page where he/she can enter the choice about which they wanna know. After that they will be directed to page about the info.


### Steps:

- Install required libraries. Example: `express` and `express-handlebars`


```sh
$ npm install express --save
```
```sh
$ npm install express-handlebars --save
```

or simply do,
```sh
$ npm i express express-handlebars -s
```

- Now lets install some `middlewares` which we need in the process of developement of app. To know about middleware you can see [this](http://localhost:4000/docs/middlewares/) post. A typical requirement is to handle sessions thus I am going to install `express-session` library. 

```sh
$ npm i express-session -s
```

`express-session` takes care of your session handling by creating a session on server side. If you don't have session facility provided by your server side page generation engine then `http` being a stateless protocol so nothing will be remembered across the request and response cycle. One request, one response and then everything will get forgotten. So we require `express-session`.


In this application we are going to use `post` request of `http`. The benefit of post request is that it doesn't have a limit of some specified size (i.e. we can send a large request too). Also anything that is being sent in the post request, it comes in the body section of your HTTP request and it doesn't appear in the URL so its a bit safer to send any data in the post request.

To retrieve data from the post request you need a middle-ware which is called `body-parser`.

```sh
$ npm i body-parser -s
```

Now I think I have download the required libraries. Now lets start coding the app.

First lets create the different routes to the application. The different routes might be: `/`, `/toLanding`, `/logout`, `/toCity`.

- `/`: I would like to show the login option.
- `/toLanding`: the page after the user is loggedin.
- `/toCity`: Once the user selects option from the toLanding page.
- `/logout`: When the user wants to logout.


{: .unreleased .note}
**Routes code**<br>file path: `./routes/routes.js`



