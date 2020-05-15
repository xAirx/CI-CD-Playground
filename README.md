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
			
			
# Github Actions

	 https://dev.to/heroku/deploying-to-heroku-from-github-actions-29ej


<img src="https://imgur.com/6gS3c4e.png" width="200">
<img src="https://imgur.com/ncDNpeW.png" width="200">


# Setup gitub to heroki git link ("couldnt find that app")

Read article and understand setup with remotes git push heroku master.

https://apassionatechie.wordpress.com/2018/01/24/heroku-couldnt-find-that-app/



#### Deploy to Heroku


Ymlfile within github actions.
https://github.com/xAirx/WebShopApp/blob/master/.github/workflows/nodejs.yml


				
			    	   https://medium.com/jeremy-gottfrieds-tech-blog/tutorial-how-to-deploy-a-production-react-app-to-heroku-c4831dfcfa08
			   	   https://blog.heroku.com/deploying-react-with-zero-configuration
			 	   https://dev.to/smithmanny/deploy-your-react-app-to-heroku-2b6f
			 	   https://medium.com/@prestonwallace/deploy-your-react-node-app-to-heroku-in-15-minutes-or-less-3-steps-134c766d8d9a
			    
			    
			    				
				
#### Sentry and Heroku  + logrocket 



## Adding sentry to github oauth and setting up project


<img src="https://imgur.com/8D8BBOc.png" width="200">

<img src="https://imgur.com/aeER1dV.png" width="200">

	
	#### Viewing Sentry

	Heroku provides an easy interface for logging into the Sentry web UI:

	heroku addons:open sentry

	
	### Provisioning the add-on

	Start by adding the Sentry addon:

	heroku addons:create sentry



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



		https://know-thy-code.com/sentry-io-using-node-js/
		
		////// IF YOU COMMIT THIS FILE SENTRY WILL TRIGGER 
		////// THE CI BUILD WILL FAIL 150% , BUT SENTRY WILL SEND AN EMAIL.
		///// Normally you wont be commiting these errors since you can see them in your IDE (yarn start etc)


		    // send an event to Sentry
		Sentry.captureMessage('my message', 'warning');

		// sent an error - automatically sends a callstack
		try {
			functionThatFailed()
		} catch (error) {
			Sentry.captureException(error);
		}



		Getting Started

					$ npm install @sentry/node@4.4.0 // or the latest version

					// or

					$ yarn add @sentry/node@4.4.0 // or the latest version
					Copy


			In the entry point of your Node.js application, typically main.js or app.js; add the following lines:

					const Sentry = require('@sentry/node');
					Sentry.init({ dsn: 'https://whateveryourdsnis@sentry.io/123456789' });
					Copy

			Anywhere in your main file, where you have access to the object, you can call the following method:

					Sentry.captureException(error);
					Copy


#### Links
				
					https://elements.heroku.com/addons/sentry
					https://sentry.io/integrations/heroku/
					https://devcenter.heroku.com/articles/sentry
							    
					https://boredhacking.com/mock-sentry-in-jest/

### Sentry and Logrocket

                                        https://blog.logrocket.com/extending-sentry-with-logrocket-52e2f5b67d5a/    
					
					
					Integrating Sentry and LogRocket

					Integrating Sentry and LogRocket lets you see a LogRocket “session” for every error in Sentry. Here’s how it works:
				
				
<img src="https://imgur.com/c76NxPx" width="200">
<img src="https://imgur.com/hCBUcNg" width="200">
<img src="https://imgur.com/Oyi9p99.png" width="200">
<img src="https://imgur.com/jBCi2D7.png" width="200">
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

