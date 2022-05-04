# Heroku Deployment Demo

## Requirements
1. Node.js v14+
2. NPM v6+

## Project Dependencies
- `dotenv` for loading in environment variables
- `express` for creating the web server
- `heroku` for interacting with and pushing to Heroku
- `nodemon` for running server in development mode

### Steps
1. Create application in [Heroku Dashboard](https://dashboard.heroku.com/apps)
![Heroku Apps Dashboard](./docs/assets/heroku_apps_dashboard.png)
2. Add config vars in Heroku under the **Settings** tab
![Heroku Config Vars Dashboard](./docs/assets/heroku_config_vars.png)
    - PORT
    - NODE_ENV
3. `npx heroku login`
4. `npx heroku git:remote -a replace-with-app-name`
    - Example: `npx heroku git:remote -a pt-3-heroku-demo`
5. `git push heroku main`

### Gotchas

Running `git push heroku main` results in the following error:
```
error: src refspec main does not match any
error: failed to push some refs to 'https://git.heroku.com/pt-3-heroku-demo.git'
```

This simply means that your default branch is not named `main`. To fix this, we need to figure out what your default branch is named. Run `git branch` to list all the branches on your machine. You will probably only have one, but on the off chance you have more than one branch, the branch with a `*` next to it is your current branch. Hit `q` on your keyboard to exit out of the branch list. 

Now rerun `git push heroku main`, but replace `main` with the branch name that had the `*` next to it. IE: `git push heroku master` if `master` was the name of the branch that had the `*` next to it.
