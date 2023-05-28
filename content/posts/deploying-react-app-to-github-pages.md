---
title: Deploying react app to Github pages
subtitle: "#GithHubPages, #React"
category:
  - Technology
author: Shailendra Rijal
date: 2023-05-27T23:59:46.217Z
featureImage: /uploads/inside-glacier-cave-2.jpg
---


The aim here is to utilise the free feature provided by Github to its users. We can add Github Actions to one of the repositories. So, we will utilise this opportunity to deploy our portfolio so that we have a chance to show our work to the world.

In order to deploy, we need to make some changes in Github as well as some work needs to be done in the code.

1. First, let's start by creating a new repository in Github. Create a repository on GitHub
2. Then using `npx create-react-app <appname>` create a react application on your machine
3. Now, connect the react application in your machine to your GitHub repository by doing the following:

   1. In the project folder on your machine, cd to the folder where you have installed the app. If you entered the appname above as react-practice, then cd into react-practice folder
   2. Now, initialize git repository by typing `git init `
   3. We want to commit and push the react application to GitHub. We can do that using following commands:

   ```gitattributes
   git commit -m "add-react-app"
   git remote add origin <your-repository-url-from-github>
   git push -u origin master
   ```

N﻿ow, that our app is pushed to Github, we want to add a package called `gh-pages `that would deploy our application to GitHub pages.

1. Install the package `gh-pages` by typing `npm install gh-pages` . This will add the package to your package.json file
2. I﻿n the package.json file, make the following changes:

   1. A﻿dd a `homepage` property with the value of `"<github-username.github.io>"` 
   2. I﻿n the scripts section, add these scripts for deploy and predeploy:

      1. `"﻿predeploy": "npm run build",`
      2. `"﻿deploy": "gh-pages -d build"` 
   3. N﻿ow, commit the changes and push to the repo as we did above.

W﻿ith these changes pushed, you should now be able to run `npm run deploy` and that should deploy your react application to the GitHub pages.

M﻿ake sure of the following things in your GitHub account:

1. I﻿n the Settings -> Pages -> Source, `GitHub pages` is selected

E﻿verytime you deploy your changes, that will trigger a workflow in GitHub Actions. You can view that by going to Actions in your GitHub. Make changes to your application and deploy the latest version and keep your app up to date.