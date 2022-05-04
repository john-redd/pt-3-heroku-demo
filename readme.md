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

Success should result in an output similar to this in your terminal.

```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 317 bytes | 317.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Compressing source files... done.
remote: Building source:
remote: 
remote: -----> Building on the Heroku-20 stack
remote: -----> Using buildpack: heroku/nodejs
remote: -----> Node.js app detected
remote:        
remote: -----> Creating runtime environment
remote:        
remote:        NPM_CONFIG_LOGLEVEL=error
remote:        NODE_VERBOSE=false
remote:        NODE_ENV=production
remote:        NODE_MODULES_CACHE=true
remote:        
remote: -----> Installing binaries
remote:        engines.node (package.json):  unspecified
remote:        engines.npm (package.json):   unspecified (use default)
remote:        
remote:        Resolving node version 16.x...
remote:        Downloading and installing node 16.15.0...
remote:        Using default npm version: 8.5.5
remote:        
remote: -----> Restoring cache
remote:        - node_modules
remote:        
remote: -----> Installing dependencies
remote:        Installing node modules
remote:        
remote:        added 870 packages, and audited 871 packages in 31s
remote:        
remote:        40 packages are looking for funding
remote:          run `npm fund` for details
remote:        
remote:        21 vulnerabilities (9 moderate, 12 high)
remote:        
remote:        To address issues that do not require attention, run:
remote:          npm audit fix
remote:        
remote:        To address all issues (including breaking changes), run:
remote:          npm audit fix --force
remote:        
remote:        Run `npm audit` for details.
remote:        
remote: -----> Build
remote:        
remote: -----> Caching build
remote:        - node_modules
remote:        
remote: -----> Pruning devDependencies
remote:        
remote:        up to date, audited 815 packages in 2s
remote:        
remote:        40 packages are looking for funding
remote:          run `npm fund` for details
remote:        
remote:        20 vulnerabilities (8 moderate, 12 high)
remote:        
remote:        To address issues that do not require attention, run:
remote:          npm audit fix
remote:        
remote:        To address all issues (including breaking changes), run:
remote:          npm audit fix --force
remote:        
remote:        Run `npm audit` for details.
remote:        
remote: -----> Build succeeded!
remote: -----> Discovering process types
remote:        Procfile declares types     -> (none)
remote:        Default types for buildpack -> web
remote: 
remote: -----> Compressing...
remote:        Done: 48.3M
remote: -----> Launching...
remote:        Released v7
remote:        https://pt-3-heroku-demo.herokuapp.com/ deployed to Heroku
remote: 
remote: Verifying deploy... done.
To https://git.heroku.com/pt-3-heroku-demo.git
   e1c4b73..453ac5f  main -> main
```

### Gotchas

Running `git push heroku main` results in the following error:
```
error: src refspec main does not match any
error: failed to push some refs to 'https://git.heroku.com/pt-3-heroku-demo.git'
```

This simply means that your default branch is not named `main`. To fix this, we need to figure out what your default branch is named. Run `git branch` to list all the branches on your machine. You will probably only have one, but on the off chance you have more than one branch, the branch with a `*` next to it is your current branch. Hit `q` on your keyboard to exit out of the branch list. 

Now rerun `git push heroku main`, but replace `main` with the branch name that had the `*` next to it. IE: `git push heroku master` if `master` was the name of the branch that had the `*` next to it.
