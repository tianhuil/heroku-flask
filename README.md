Heroku-Flask
============

Minimialist example of a Heroku app on flask.

**To recreate**:

1. Setup
````python
cd heroku-flask
virtualenv venv
. venv/bin/activate
````
2. Coding: write the contents of `hello.py`.  Notice that the `PORT` environment variable is set by Heroku in production and we default to 5000 for localhost.
3. `pip freeze > requirements.txt` to generate the requirements file for heroku provisioning.
4. `echo 'web: python hello.py' > Procfile` to generate a procfile which tells heroku (foreman) what to run on server start.
5. By default, foreman looks at `.env` to determine what environment variables to set in localhost but this file is not checked into source so that it is not deployed in production.  Here are the contents of `.env`
```
PYTHONPATH=''
DEVELOPMENT=True
```
Don't forget to add `.env` to `.gitignore`.
1. To view in local mode, run either `python hello.py` or `foreman start web` (recommended).

7. Deploy to production (note that you'll need to [get a heroku account](https://www.heroku.com/) and [install heroku tools](https://toolbelt.heroku.com/):
````python
git init
git add hello.py requirements.txt Procfile
git commit -m "Initial commit"
heroku create
git push heroku master
````

8. `heroku open` to view in production

This is based on [these](http://virantha.com/2013/11/14/starting-a-simple-flask-app-with-heroku/) (slightly) flawed instructions.
