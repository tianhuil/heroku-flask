Heroku-Flask
============

Minimialist example of a Heroku app on flask.

**To recreate**:

1. Setup
   ```python
cd heroku-flask
virtualenv venv
. venv/bin/activate
  ```
1. Coding: write the contents of hello.py.  Notice that the `PORT` environement variable is set by Heroku in production and we default to 5000 for localhost.
1. `pip freeze > requirements.txt` to generate the requirements file for heroku provisioning.
1. `echo 'web: python hello.py' > Procfile` to generate a procfile which tells heroku what to run on server start.
1. To view in local mode, run either `python hello.py` or `foreman start web` (recommended).
1. Deploy to production (note that you'll need to [get a heroku account](https://www.heroku.com/) and [install heroku tools](https://toolbelt.heroku.com/):
   ```python
git init
git add hello.py requirements.txt Procfile
git commit -m "Initial commit"
heroku create
heroku apps:rename proj
git push heroku master
    ```
1. `heroku open` to view in production

This is based on [these](http://virantha.com/2013/11/14/starting-a-simple-flask-app-with-heroku/) (slightly) flawed instructions.
