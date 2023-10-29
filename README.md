# Immutable-Passport-Integration-Guide
This guide will explain how to integrate Immutable Passsport into a simple application using a step by step approach.

# Step 1: Creating a simple application or git cloning a repository of the simple application 
For this step I will clone a repository I created few weeks ago. Using your preferred terminal, these are the steps to follow:
type git version 
You should see the version of git installed in your computer. If you see an error message, Install git by using the following link: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
type git clone https://github.com/biyoceju/fibonacci_app.git
go to the fibonacci_app directory
deploy this application on netlifly using the information mentioned in step 8 of the following web page: https://app.stackup.dev/quest_page/try-catch-finally-statements
after successful deployment you will get a url like https://celestin-fibonacci-app.netlify.app/ . We will use it later. 
.
# Step 2: Registering the application on Immutable Developer Hub
first go to https://hub.immutable.com/
register using your preferred email account or by using other means suggested by the website.
click add project
enter project name, the environment name and choose a type of environment (mainnet or testnet) then click create
create a passport client for your created environment by clicking the button Add client. Enter the name and the url created in step 1. Click create. The next page will display a client ID. Be sure to make a note of your application's Client ID, Callback URL and the Logout URL that you entered, as you will need these to initialise the Passport module in your application.

# Step3: Installing and initialising the Passport client
open the command line in the project directory (fibonaccy_app directory)
check if node is installed in your computer by entering: node -v. You should see the version of node installed in your computer. If you see an error message, Install node by running: nvm install --lts
install the Immutable SDK by running the following command: npm install -D @imtbl/sdk. If compications occur, kindly use the following commands: rm -Rf node_modules && npm cache clean --force && npm i
open Visual studio code and create a file called passport_init.js
initialise the passport client by copying and paste the following code in the file you just created :
import { config, passport  } from '@imtbl/sdk';

const passportInstance = new passport.Passport({
  baseConfig: new config.ImmutableConfiguration({
    environment: config.Environment.SANDBOX
  }),
  clientId: '<YOUR_CLIENT_ID>',
  redirectUri: 'https://example.com',
  logoutRedirectUri: 'https://example.com/logout',
  audience: 'platform_api',
  scope: 'openid offline_access email transact'
});
replace ClientID, redirectUri, logoutRedirectUri, by the information obtained at the end of step 2.
