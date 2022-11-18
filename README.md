# Deployment React in Github Pages

In order to learn and experince deployment and work flow process using Github, I have deployde a react base template using Github pages and added custom domain. The domain name was purchesed from domain name provider Names.com and then added to Github pages settings. 

## Goal and Objectives
The goal is to understand deployment process using Github. In order to understand the process, a react application will be configured and deployed to production, using Github pages service. Once the deployment is complited, a custom domain will be added deployed web page. 

## Reasons and justifications
A React application was selected for deployment because of extensive prior experience gained in several courses using the technology. React is a JavaScrip library ofr development of reactive web pages. During prior research, several hosting platforms were considered and a choice was made to test workflow of each of them. This document is rapport of process, results and issues experienced during the testing and configuration period. 

Names.com chosen as the domain provider because it provides free domain for student in a limited time for free. From prior experience, the provider also has a simple UI. 

### Resources 

- Tutorial: https://www.youtube.com/watch?v=K5DTIf-jWhk

## Create React Web project

This section of the rapport is describing creation of a React project that can be used for deployment. 

### Prerequesits for React application
In order to create a react  application, it is required to use Node.js interpreter and npx package manager. This can be done by downloaded from [nodejs.org](https://nodejs.org/en/download/) page. Adding and setting up react can be done by using the React documentation which can be found on [reactjs.org](https://reactjs.org/docs/getting-started.html) web page.

### Init React Application

A new React application can be initialized using the following command. 

```powershell
	npx create-react-app <APPLICATION-NAME>
```

When the command is used, configuration information will be request. For the purpose of this application, the default values were selected by pressing Enter until application configuration  and generation is complied. The next step is to enter the directory of the newly created react application. 

```powershell
	cd <APPLICATION-NAME>
```

In order to validate the newly created react web application is created and can be used further, use the following command to start development server with the react application. 

```powershell
	npm start
```

The application will start a development server, hosted on localhost, with default port number of 3000. Hence by opening a web broser and using the link [localhost:3000](http://localhost:3000/), a default react web page can be viewed now as shown below.

<img src="/read_me_images/Pasted image 20221117132436.png" alt="Alt text" title="Optional title">

Use the `Ctrl + C` command to complice and end the process of development server. 

## Documentation of the deployment process

This section is describing deployment of a react application using React pages application. In this section, a git repository will be initialized in the react working directory. Then a remote Github repository will be created and lined to the local git repository, and code with the required configurations will be pushed to remote repository and deployed to Github pages. 
### Add remove repository

A Github repository is required in order to utilize the Github pages service. A new repository can be created by using the [documentation](https://docs.github.com/en/get-started/quickstart/create-a-repo) provided by Github docs. Prerequisites for creation of a new  Github repository is to have a [Github account](https://docs.github.com/en/get-started/onboarding/getting-started-with-your-github-account).

A new repository can be created by first pressing the `new` button in the left upper corner of the Github main page. Then will out the displayed form. 

![[Pasted image 20221117142442.png |400]]

If you have access to premium features, the repository can be private and if not, make it public in order to get access to GitHub pages service. Add a description and then nothing else should be added. Press on `Create repository`. 

Then in the react web project directory use the following command to initialized the git in the repository. In order to use git on the machine, it hsa to be [installed](https://git-scm.com/downloads)  and [configured](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config).  

```bash
	git init
```

A .git file will be created that will be use for versioning control. the following step is to set the above create Github repository as the remove repository used for the project. Use the following command to set the remote repository. 

```bash
	git remove add origin <REMOTE-REPOSITORY-URL>
```

In order to create a main branch that can be used in the development of the application use the following command: 

```bash
	git branch -M main
```

Lastly the committed code can be added to the remote repository by using the following command.

```bash
	git push -u origin main
```

Now the repository will contain the code of the react base template. 

### React application configurations for deployment

The initial step step is to add a new property in the root of `package.json` file in the above created React application directory. the property is `homepage` and the value of the property will be github repository information.  

```json
	"homepage": "https://<GITHUB-USERNAME>.github.io/<REPOSITORY-NAME>"
```

In order to deploy react web project to github pages, a new branch has to be created and build files have to be added to the branch. Then, those files can be added to Github Pages by specifying the branch as the one which had to be used in deployment process.  

The process of building and adding to a specific branch can be simplified using the `gh-pages` library. In can be installed and added using the following command. 

```powershell
	npm install gh-pages
```

Two more commands have to be added to the `package.json` file. Those commands have be added in the `scripts` sub-json object. 

```json
	"predeploy": "npm run build",
    "deploy": "gh-pages -d build"
```

Then the new commands can be added and used further.  In order to deploey the project in the production build and deploy the web page to the github pages by using the following command. 

```powershell
	npm run deploy
```

In the case of success, the following terminal output will be expected. 

![[Pasted image 20221117140014.png | 500 ]]

The necessary files will build and and pushed to the branch specifically created by the library. From where they can be deployed to Github pages. The command is used a new Environment should be added in GitHub repository main page, that should look like follows. 

![[Pasted image 20221117141505.png]]

The live web page can be view by first selecting the `Settings` tab in the repository page. Then on the left select `Pages`. On the top of displayed page, a window with url, can be viewed that will be similar to the following image. 

![[Pasted image 20221117151307.png]]

By using the url in the image, the deployed web page can be viewed. The web page contains a pre make domain name defined by Github. The url can be changed by using adding custom domain. 

## Add custom domain name 

In this section will be described how to add a custom domain name to the deployed github Pages deployment. In order to follows this part of the rapport, an account has to be registered on Names.com and register a domain name which can be use later. 

In order to add a custom domain name, first a DNS records have to be configured and then it has to be added to the guthub pages settings. 

### Configure DNS records

The DNS record can be configured by first pressing `Quick Links` and then select `manage DNS records`.


![[Pasted image 20221117152144.png]]

In the displayed manu, the DNS record has to be configured as shown in the following Figure. The IP address in the `ANSWER` column are privided by the [Github documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

![[Pasted image 20221117152656.png]]

### Adding custom domain to GitHub pages

A domain name should be added in the custom domain field that can be found under `Settings` tab, left side of the menu will contain a `Pages` tab. Select in, scroll down to the custom domain section and add the above registered and configured domain. Press `Save` and Github will make DNS check before the domain can be used. 

![[Pasted image 20221117153021.png ]]

If Domain check is passed, the user may use the domain name. 

![[Pasted image 20221118083040.png]]

There are also changes in code that have to be added before the system can be deployed.  The change is in the root of `package.json` file. The property is called `homepage`, and it has to be sat to the custom domain name. 

```json
	"homepage": "https://yavorski.live",
```

The last the deployment has to updated by using the following commands. 

```powershell
	npm run deploy
```

Hence the deployment with custom domain process is complice. 

![[Pasted image 20221118083140.png]]
