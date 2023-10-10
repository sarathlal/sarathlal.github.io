---
title: Handling dynamic subdomain with Flask - Python
layout: post
tags:
  - Flask
  - Python
---

Here is my minimal flask application.

    from flask import Flask

    app = Flask(__name__)

    @app.route("/")
    def hello_world():
        return "<p>Hello, World!</p>"

Now to run the application, I have to use the commands below in the terminal.

    export FLASK_APP=hello
    flask run

Visit `http://localhost:5000` in your browser & we can see `hello world`. Just try with subdomain - `http://app.localhost:5000` & we will still get the same output.

Now we can modify our code littile bit.

    from flask import Flask

    app = Flask(__name__)
    app.config['SERVER_NAME'] = "localhost:5000"

    @app.route('/')
    def hello_world():
        return "<p>Hello, World!</p>"

    @app.route('/', subdomain="<subdomain>")
    def home(subdomain="default"):
        return f'<p>Hello, World from {subdomain}</p>'

Now visit the `http://localhost:5000` in your browser & we can see the old `hello world` text. Now it is the time to check with a sub domain - `http://app.localhost:5000` & we can see the different output.

The first change we made is to add the 'SERVER_NAME' config value. Without this value Flask will not be able to differentiate which part of the URL is subdomain and which part is the domain.

The second change is adding extra `@app.route('/', subdomain="<subdomain>")` this will match all the url with pattern `http://*.localhost:5000` and pass the subdomain value as parameter for route function as given name subdomain.

If we visit a URL without the subdomain, the first route function will catch that URL and the subdomain value will be the default value. If we have a subdomain value the second route will catch that request and the subdomain value will be whatever value we used as subdomain.
