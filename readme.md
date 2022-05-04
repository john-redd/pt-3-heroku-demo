# Heroku Deployment Demo

## Requirements
1. Node.js v14+
2. NPM v6+
3. Heroku CLI v7+

### Heroku CLI

Use one of the installation methods documented [here](https://devcenter.heroku.com/articles/heroku-cli)

### Steps
1. Create application in [Heroku Dashboard](https://dashboard.heroku.com/apps)
![Heroku Apps Dashboard](./docs/assets/heroku_apps_dashboard.png)
2. Add config vars in Heroku under the **Settings** tab
  - PORT
  - NODE_ENV
![Heroku Config Vars Dashboard](./docs/assets/heroku_config_vars.png)
3. `heroku login`
4. `heroku git:clone -a replace-with-app-name`
  - Example: `heroku git:clone -a pt-3-heroku-demo`
5. `git push heroku main`