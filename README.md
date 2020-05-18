# CI-CD-Playground


# Setup 
		
			     
			     ## Git setup with branches etc.


                              ## Pre hooks ->  
                              
                              
                               # Simple git hooks ( eslint running fixing everything)

                                    https://medium.com/better-programming/simple-git-hooks-with-create-react-app-eslint-and-husky-6983806dba5c
				    

			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;

## Heroku


### Standard project deploy to heroku
			
			https://dev.to/smithmanny/deploy-your-react-app-to-heroku-2b6f

			    heroku login (Enter your Heroku credentials)
			    git init
			    git add .
			    git commit -m “initial commit”
			    heroku create (You should see two links after running this command. Copy the second one)
			    git remote add heroku PASTE THE LINK YOU JUST COPIED
			    git push heroku master



&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 

### Understanding Buildpack and Heroku


		---------- IMPORTANT DETAIL WITH HEROKU AND GIT + PACKAGE.JSON + BUILDPACK-----------
			    
			     Create git folder, then CRA
			     move contents out of the CRA folder into the "ROOT" git folder. else heroku wont see the package.json
			     			     
				FOLDER STRUCTURE HAS TO LOOK LIKE THIS:
<img src="https://imgur.com/FGTnAb9.png" width="200">
			     
			     The buildpack has to be set to the following: 
			     https://github.com/mars/create-react-app-buildpack
			     https://buildpack-registry.s3.amazonaws.com/buildpacks/mars/create-react-app.tgz
			     
			     The buildpack is the docker image that builds your setup on heroku.
			     
			    
![](https://imgur.com/Wb0PMz2.png)
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
			
## Github Actions

	 https://dev.to/heroku/deploying-to-heroku-from-github-actions-29ej


<img src="https://imgur.com/6gS3c4e.png" width="200">
<img src="https://imgur.com/ncDNpeW.png" width="200">


&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 



## Fix gitub to heroku git link ("couldnt find that app")

Read article and understand setup with remotes git push heroku master.

https://apassionatechie.wordpress.com/2018/01/24/heroku-couldnt-find-that-app/
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 

## Deploying to Heroku


Ymlfile within github actions.
https://github.com/xAirx/WebShopApp/blob/master/.github/workflows/nodejs.yml


				
			    	   https://medium.com/jeremy-gottfrieds-tech-blog/tutorial-how-to-deploy-a-production-react-app-to-heroku-c4831dfcfa08
			   	   https://blog.heroku.com/deploying-react-with-zero-configuration
			 	   https://dev.to/smithmanny/deploy-your-react-app-to-heroku-2b6f
			 	   https://medium.com/@prestonwallace/deploy-your-react-node-app-to-heroku-in-15-minutes-or-less-3-steps-134c766d8d9a
			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;			    
## Setup Github actions Production and Development workflow			

	https://spin.atomicobject.com/2020/01/20/github-actions-react-node/
	
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;	
	
#### Handling ENV variables, so they arent local to each step...	

		https://github.com/marketplace/actions/set-env
	
	
	yml file: 
	
		
		name: Push Container to Heroku to Development

				on:
				  push:
				    branches:
				      - development
				      - master

				jobs:
				  build:
				    runs-on: ubuntu-latest

				    if: github.event_name == 'push' && (github.ref == 'refs/heads/master' || github.ref == 'refs/heads/development')
				    env:
				      HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}

				    steps:
				      - uses: actions/checkout@v1
				      - name: Login to Heroku Container registry
					env:
					  HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
					run: heroku container:login
				      - name: Install Dependencies - yarn install
					run: yarn install
				      - name: Unit tests - yarn test
					run: yarn test

				      - name: Set Dev Environment
					if: github.ref == 'refs/heads/development'
					uses: allenevans/set-env@v1.0.0
					with:
					  ENVIRONMENT: "development"
					  BRANCH: "development"

				      - name: Printdevenv
					if: github.ref == 'refs/heads/development'
					run: |
					  echo "ENVIRONMENT=${ENVIRONMENT}"
					  printenv
				      - name: Printdevbranchenv
					if: github.ref == 'refs/heads/development'
					run: |
					  echo "BRANCH=${BRANCH}"
					  printenv
				      - name: Set Production Environment
					if: github.ref == 'refs/heads/master'
					uses: allenevans/set-env@v1.0.0
					with:
					  ENVIRONMENT: "production"
					  BRANCH: "master"

				      - name: Printproductionenv
					if: github.ref == 'refs/heads/master'
					run: |
					  echo "ENVIRONMENT=${ENVIRONMENT}"
					  printenv
				      - name: Printprodbranchenv
					if: github.ref == 'refs/heads/master'
					run: |
					  echo "BRANCH=${BRANCH}"
					  printenv
				      - name: Push to Heroku

					run: git push --force https://heroku:$HEROKU_API_KEY@git.heroku.com/webshopproject-$ENVIRONMENT.git origin/$BRANCH:master

<img src="https://imgur.com/6DikZ7l.png" width="200">
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;


## RENDER COMPONENT CONDITIONALLY - Handling ENV variables, Locally and Remotely on heroku server


			Setup ENV's with DOTenv Express VS react lccal and production.

			We want to render a component based on env variables set to dev or production.


			### Setting it up locally first:


						App.js 


						require('dotenv').config();

						  {process.env.REACT_APP_SERVER_MODE === 'development' ? <SentryComponent /> : ''}


						Doing it The express way

							In express you do not prefix with REACT_APP_*******

							so the env can simply just be SERVER_MODE and be accessed by process.env.SERVERMODE


						Doing it The react way

							Prefixing .env variables with REACT_APP

							React only includes variables with that prefix, so you if you have malicious dependencies, or just a public build, you don't expose things like local keys and stuff


							“in .env SERVER_MODE=development should be REACT_APP_SERVER_MODE=development”


			&nbsp;
			&nbsp; 
			&nbsp;     
			&nbsp; 
			&nbsp;
			&nbsp;
			&nbsp; 
			&nbsp;  
			&nbsp; 
			&nbsp;
			&nbsp; 			    
			&nbsp;

			### Setting up env variable to work on development and production server


						Doing it The Express way

							 Heroku will normally populate our process.env for us, with the environment variables set in its own dashboard, just like how github has its secrets.

							This applies to when we work with express.



						Doing it The react way

							if we were working with REACT we would just add these to heroku  in the dashboard like this:

							On heroku when deployed the react app is already built, this means the env vars will be set to whatever they were on build time.

							Once you build the react app all referenced variables are built in to the outputted code.

							Heroku populates the process.env with its env's defined in the dashboard.


<img src="https://imgur.com/eYl0L0I.png" width="200">

<img src="https://imgur.com/qJUFzAZ.png" width="200">

<img src="https://imgur.com/UZLurFl.png" width="200">

&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;

## TERRAFORM - Browser Basic auth - Adding password protection to static react app on heroku

Buildpack to add to dev server: 

https://buildpack-registry.s3.amazonaws.com/buildpacks/mars/crak.tgz


Securing Static Heroku React Site with Password and Admin login.

https://github.com/mars/crak-buildpack#user-content-quick-start


Technologies

	 Terraform

	Kong -> postgres DB

	 Basic Browser Auth

	“the kong part is handled for us”




	Adding PSQL addon to heroku
		
		The web server is a Kong gateway that uses Heroku Postgre to store configuration of services, route, and plugins.



	Kong uses PSQL to store its information so we will add postgres addon to heroku

		heroku addons:create heroku-postgresql:hobby-dev —app webshopproject-development



	routes.tf to add in root of development branch deploy.

			resource "kong_service" "react" {
			  name     = "create-react-app"
			  protocol = "http"
			  host     = "127.0.0.1"
			  port     = 3000
			}

			resource "kong_route" "web_root" {
			  protocols  = ["https", "http"]
			  paths      = ["/"]
			  service_id = "${kong_service.react.id}"
			}
			provider "random" {
			  version = "~> 2.0"
			}

			resource "random_id" "private_access_password" {
			  byte_length = 32
			}

			output "private_access_password" {
			  value = "${random_id.private_access_password.b64_url}"
			}

			resource "kong_plugin" "react_basic_auth" {
			  name        = "basic-auth"
			  service_id  = "${kong_service.react.id}"

			  config = {
			    hide_credentials = "true"
			  }
			}

			resource "kong_consumer" "private_access" {
			  username = "private"
			}

			resource "kong_consumer_plugin_config" "private_access_credentials" {
			  consumer_id = "${kong_consumer.private_access.username}"
			  plugin_name = "basic-auth"

			  config = {
			    username = "private"
			    password = "${random_id.private_access_password.b64_url}"
			  }
			}


	Create a main.tf file 

			[
			terraform {
			  backend "pg" {}
			}

			provider "kong" {
			  version        = "~> 1.7"
			  kong_admin_uri = "http://127.0.0.1:8001"
			}

			 pg is configured during the deploy i think

			 Filled with heroku addon info

			Kong admin uri is set to local because its on the server running it



	When we want the password to login with we write: 
 
			heroku run terraform output private_access_password —app webshopproject-development



	Preventing password being echoed in github actions yaml when building…

			output "private_access_password" {
			  value = "${random_id.private_access_password.b64_url}"
			  sensitive = true
			}




	Access page if it says you are not authorized


			https://username:PASSWORD@webshopproject-development.herokuapp.com/






&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;


### Adding sentry to github oauth and setting up project



<img src="https://imgur.com/8D8BBOc.png" width="200">

<img src="https://imgur.com/aeER1dV.png" width="200">

	
	#### Viewing Sentry

	Heroku provides an easy interface for logging into the Sentry web UI:

	heroku addons:open sentry

	
	### Provisioning the add-on

	Start by adding the Sentry addon:

	heroku addons:create sentry

&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;

### Implementing Sentry into code 


		Sentry is for tracking live apps in production.

		commit -> push -> triggers build
		
		
		RNG: Which errorrs are sentry aimed at am i misunderstanding ?
		[3:11 PM] W1SH: sentry is not meant for code analysis
		[3:11 PM] W1SH: runtime errors is what it's for
		[3:12 PM] RNG: So a user does something on the site
		[3:12 PM] RNG: something breaks
		[3:12 PM] RNG: sentry gets notified
		[3:12 PM] W1SH: exactly!
		[3:12 PM] W1SH: let' say your database is down
		[3:12 PM] W1SH: server can't connect
		[3:12 PM] W1SH: boom, error
		[3:12 PM] W1SH: error 500's are great examples
		
		
		[3:14 PM] RNG: but sentry also has some JIRA feel to it as well
		[3:14 PM] W1SH: because you can assign errors you mean?
		[3:14 PM] RNG: yeaa
		[3:14 PM] RNG: overview etc etc
		[3:14 PM] W1SH: can be but again, not really it's purpose
		[3:15 PM] W1SH: it's for tracking user-generated errors



			Add the Sentry SDK as a dependency using yarn or npm:

			# Using yarn
			$ yarn add @sentry/browser

			# Using npm
			$ npm install @sentry/browser

			Connecting the SDK to Sentry

			After you’ve completed setting up a project in Sentry, Sentry will give you a value which we call a DSN or Data Source Name. It looks a lot like a standard URL, but it’s just a representation of the configuration required by the Sentry SDKs. It consists of a few pieces, including the protocol, public key, the server address, and the project identifier.

			You should init the Sentry browser SDK as soon as possible during your application load up, before initializing React:

			import React from 'react';
			import ReactDOM from 'react-dom';
			import * as Sentry from '@sentry/browser';
			import App from './App';

			Sentry.init({dsn: "https://0279e0a3aae840339f4a711848494919@o392672.ingest.sentry.io/5240589"});

			ReactDOM.render(<App />, document.getElementById('root'));

			On its own, @sentry/browser will report any uncaught exceptions triggered from your application.

			You can trigger your first event from your development environment by raising an exception somewhere within your application. An example of this would be rendering a button:
			
			function App() {
			  const methodDoesNotExist = () => {
			    console.log('wtf');
			    methodExistsNot();
			  };

			  return (
			    <div>
			      <h1>Webshop - MasterBranch</h1>
			      <Homepage />
			      <button onClick={methodDoesNotExist}>Test Sentry</button>;
			    </div>
			  );
			}

&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
### Implementing logrocket with sentry

         https://blog.logrocket.com/extending-sentry-with-logrocket-52e2f5b67d5a/    
					
					
	Integrating Sentry and LogRocket

	Integrating Sentry and LogRocket lets you see a LogRocket “session” for every error in Sentry. Here’s how it works:
				

			// if using React 16.10
			npm i logrocket-react --save
			
			1. Install thelogrocketmodule via NPM:

			npm i --save logrocket

			2. Import LogRocket and callLogRocket.initlike so:

			import LogRocket from 'logrocket';
			LogRocket.init('8ckc5m/my-master-project-dev');

			Code: 

				import * as Sentry from '@sentry/browser';
				// or using CommonJS
				import LogRocket from 'logrocket';
				import setupLogRocketReact from 'logrocket-react';
				import Homepage from './HomepageComponent';

				LogRocket.init('8ckc5m/my-master-project-dev');
				// after calling LogRocket.init()
				setupLogRocketReact(LogRocket);

				/* import TriggerSentry from './TriggerSentry'; */
				Sentry.configureScope(scope => {
				  scope.setExtra('sessionURL', LogRocket.sessionURL);
				});

				LogRocket.getSessionURL(sessionURL => {
				  Sentry.configureScope(scope => {
				    scope.setExtra('sessionURL', sessionURL);
				  });
				});
				
				
								
<img src="https://imgur.com/w6Jdvko.png" width="200">
<img src="https://imgur.com/hCBUcNg.png" width="200">
<img src="https://imgur.com/jBCi2D7.png" width="200">
<img src="https://imgur.com/c76NxPx.png" width="200">
<img src="https://imgur.com/6BK3Wij.png" width="200">
					
					
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
### Links
				
					https://elements.heroku.com/addons/sentry
					https://sentry.io/integrations/heroku/
					https://devcenter.heroku.com/articles/sentry
							    
					https://boredhacking.com/mock-sentry-in-jest/

			
			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp;
&nbsp; 			    
&nbsp; 
					
			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp;
&nbsp; 			    
&nbsp; 
					
			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp;
&nbsp; 			    
&nbsp; 
					
			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp;
&nbsp; 			    
&nbsp; 
# Dockerized apps on heroku

	https://medium.com/travis-on-docker/how-to-run-dockerized-apps-on-heroku-and-its-pretty-great-76e07e610e22

&nbsp; 
&nbsp;
&nbsp; 			    
		
	  	  
# Travis CI (free)  "same" procedure as gitlab below	  
	  
	  https://codeburst.io/ci-cd-with-github-travis-ci-and-heroku-e088a24f32ef
	  https://codeburst.io/ci-cd-with-github-travis-ci-and-heroku-e088a24f32ef
	  
	  
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp;

#### Herokus OWN CI (PAID)

https://www.heroku.com/pricing#cd-ci
				
					Heroku CI automatically runs your app’s test suite with every push to your app’s GitHub repository, enabling you to easily review test results before merging or deploying changes to your codebase. Tests execute in a disposable environment that closely resembles your staging and production environments, which helps to ensure that results are accurate and obtained safely.

					Heroku CI works seamlessly with any Heroku Pipeline.

<img src="https://imgur.com/5YzKMdV.png" width="200">
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 	

# Gitlab (abandonded PAID)
	
	
	## Learning Gitlab ( COSTS MONEY ) and Unit testing integration
              
	      ## Staging-> Unit-testing

			https://www.freecodecamp.org/news/testing-react-hooks/

			https://medium.com/faun/integrate-unit-testing-with-gitlab-pipelines-basics-4c85e47ae608
			
			https://www.freecodecamp.org/news/the-right-way-to-test-react-components-548a4736ab22/


### Setup Gitlab -> 
	
      https://medium.com/swlh/how-do-i-deploy-my-code-to-heroku-using-gitlab-ci-cd-6a232b6be2e4	
			    


##### What worked:
			    
		Setting up variables to work with heroku, worked wonderfully, it will deploy to heroku with the gitlab.yml, 
			   
		I made it run the pipeline by forcing a push in the gitlab repo, since the sync(pull) isnt working.
		
<img src="https://imgur.com/X1ntRn8.png" width="200">
<img src="https://imgur.com/VyodBif.png" width="200">

		
![](https://imgur.com/GHb4mFS.png)
			
		
		
		
##### What didnt work (pulling worked initially - for some reason bugged at the point in time of me trying this):			    
			
			   Using the external repo, I cannot get it to sync properly with the gitlab repo, as in github -> gitlab, syncing should be set up automatically  as per their documentations



<img src="https://imgur.com/Oyi9p99.png" width="200">

			    
![](https://imgur.com/g7hIa18.png)
			
		


###### Using - GitLab CI/CD for external repositories
			     
			   
			      Should setup automatic pull, and everything needed BUT ofcourse it costs money..
			      
			     -------- Tried gold membership to setup the pull feature (didnt work) ----------
			      
			     
			     
			     Circuventing pulling feature not working (NOT NEEDED) 
			     
			      
					      Tried setting up webhooks (didnt work)

						https://github.com/xAirx/WebShopApp/settings/hooks/210991692
						https://gitlab.com/xAirx/WebShopApp/hooks



					      Tried project integrations with personal access token (didnt work)

						 https://docs.gitlab.com/ee/user/project/integrations/github.html
						 https://gitlab.com/xAirx/WebShopApp/-/services/github/edit

			      
			      
  ###### Gitlab Error tracking (Not tried)

				  https://sentry.io/integrations/gitlab/

				  https://about.gitlab.com/blog/2019/01/25/sentry-integration-blog-post/			      
			      		      
			      
			      
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 	
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 			    
		
# Extra


## Deploying to firebase

                                           https://medium.com/evenbit/automatically-deploy-to-firebase-with-gitlab-ci-546f194c44d8

&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp;        	    
                              

## How express and react code co-exists on the server

                                              https://medium.com/jeremy-gottfrieds-tech-blog/tutorial-how-to-deploy-a-production-react-app-to-heroku-c4831dfcfa08
                                              https://www.freecodecamp.org/news/how-to-deploy-a-react-app-with-an-express-server-on-heroku-32244fe5a250/

		
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 		
		
    
 ## Monitoring tools: logrocket and sentry. 
                                    

                                     # Debugging and performance optimization

                                                Sentry acts as a bug tracker for your production code; tracking any javascript errors that may occur for users, and reporting them back to you so you can hopefully fix them

                                                logrocket appears to capture and forward logs from users browsers, and adds the ability to 'replay' the state of their browser to directly see the issue



                  ------------------ Sentry + logrocket +  Monitoring bugs & "User testing"  ---------------------


                                                  https://boredhacking.com/mock-sentry-in-jest/

                                                  https://blog.logrocket.com/extending-sentry-with-logrocket-52e2f5b67d5a/



                                                  ------------------ Github and Sentry ---------------------

                                                    https://sentry.io/integrations/github/
&nbsp;
&nbsp; 
&nbsp;     
&nbsp; 
&nbsp;
&nbsp;
&nbsp; 
&nbsp;  
&nbsp; 
&nbsp;
&nbsp; 	
			
			
## Testing  Notes


		There is a lot of code that exists just to connect other, more interesting code together and it can be a lot of trouble to write unit tests for all that connective tissue and you don't really get a lot of benefit from doing that.

		I think it's better to start with an integration test that covers all the connective tissue, such as rendering the entire route (so if your page renders a list of products at /products then your test does visit('/products') and renders the entire app and tests the most basic functionality). 

		Then instead of unit testing every single thing, you can just unit test the cases that aren't already covered by the integration test.


		@MrLeebo Thanks for your input. I"m still new at testing and I feel like I should be testing every piece of code I write. But what you're saying makes more sense. Thanks again, inputs like yours really help  understand the whole process.

		[don't try to achieve 100% test coverage. it's basically impossible to maintain. The time it takes to improve your test coverage gets exponentially harder the more coverage you have. From 0% coverage, if it takes you 1 day to get to 50%, it'll probably take 2-3 days to get 90%. After a week you might hit 99%, but it'll take another week to seal that remaining 1%. In that time, the code will probably change and you'll be a week out again

