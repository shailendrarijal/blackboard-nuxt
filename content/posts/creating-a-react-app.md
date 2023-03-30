---
title: Creating a react app
subtitle: Create your first react app
category:
  - Technology
author: Shailendra Rijal
date: 2023-03-26T10:18:15.985Z
featureImage: /uploads/inside-glacier-cave-2.jpg
---
T﻿his document provides information on how to create a react app. This will only focus on how to create a basic starter app rather than focusing on how to add features to the app.

## N﻿ode installation:

A﻿t first, we need to make sure that we have node and npm installed on our machine. Follow the steps depending your machine is a mac or windows. N﻿ode is needed for a lot of development work including running applications on your machine.

#### W﻿indows installation:

To install Node:

1. C﻿lick on the link: <https://nodejs.org/en/download/>
2. D﻿ownload and install the NodeJS installer
3. L﻿eave the folder location as default and click Next
4. I﻿n the next screen, select 'npm package manager' - not the default option of NodeJS
5. C﻿lick on Next and then click on Install

T﻿o verify Node is installed:

1. I﻿n search bar, search for Command Prompt
2. In Command Prompt, type node -v and press enter to confirm the node installation
3. I﻿n Command Prompt, type npm -v and press enter to confirm the node installation

### M﻿ac installation:

T﻿o install Node in Mac,

1. C﻿lick on the link: <https://nodejs.org/en/download>
2. D﻿ownload the .pkg installer for macOS
3. O﻿pen the installer and follow the prompts to complete the installer
4. Open terminal by entering cmd + space and then typing terminal. When terminal opens, type node -v and press enter
5. If correctly installed, it will display node version
6. Then we need to update the npm version.
7. To update the npm version, in the terminal type sudo npm install npm –global. This updates the npm CLI client
8. Last step is to ensure that the node is in right path in your machine.
9. To do that, in your root folder, create a file called .bash_profile
10. Open the file and type echo ‘export PATH=/usr/local/bin:$PATH’ >>~/.bash\_profile
11. Save the file and close it
12. In the terminal type source ~/.bashrc and press enter. This ensures the right PATH is setup

## Creating a react app:

Now when the Node is installed, next step is to create the app in react. For that, first create a folder where you want to do all your dev work.

In terminal, navigate into that folder.

Then, type npx create-react-app <app-name>

* Change the <app-name> with the actual app name that you want to give to your app.
* This command will create an app with your desired name

Next step is to go into the folder. So,

In terminal, type cd <app-name>. This takes you inside of that folder

Then run npm start. 

This will start your app.