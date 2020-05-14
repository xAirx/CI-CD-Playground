# CI-CD-Playground


# Setup 
		
			     
			     ## Git setup with branches etc.


                              ## Pre hooks ->  
                              
                              
                               # Simple git hooks

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
			
			
					
					


#### Deploy to Heroku
				
			    	   https://medium.com/jeremy-gottfrieds-tech-blog/tutorial-how-to-deploy-a-production-react-app-to-heroku-c4831dfcfa08
			   	   https://blog.heroku.com/deploying-react-with-zero-configuration
			 	   https://dev.to/smithmanny/deploy-your-react-app-to-heroku-2b6f
			 	   https://medium.com/@prestonwallace/deploy-your-react-node-app-to-heroku-in-15-minutes-or-less-3-steps-134c766d8d9a
			    
			    
			    
				
				
#### Sentry and Heroku 
				
					https://elements.heroku.com/addons/sentry
					https://sentry.io/integrations/heroku/
					https://devcenter.heroku.com/articles/sentry
							    
							    
			    
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
	
# Github Actions

	 https://dev.to/heroku/deploying-to-heroku-from-github-actions-29ej


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
		
	  	  
# Travis CI (free)  same procedure as gitlab below	  
	  
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

						    ![](https://imgur.com/g7hIa18.png)
						    ![](https://imgur.com/g7hIa18.png)


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

