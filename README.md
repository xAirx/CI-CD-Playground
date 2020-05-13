# CI-CD-Playground


# Setup 

                               ## Create empty project https://www.freecodecamp.org/news/how-to-deploy-a-react-app-with-an-express-server-on-heroku-32244fe5a250/


                               ## Pre hooks ->  
                              
                              
                                    # Simple git hooks

                                    https://medium.com/better-programming/simple-git-hooks-with-create-react-app-eslint-and-husky-6983806dba5c



				  ##Gitlab and Unit testing integration

					## Staging-> Unit-testing

							https://www.freecodecamp.org/news/testing-react-hooks/

							https://medium.com/faun/integrate-unit-testing-with-gitlab-pipelines-basics-4c85e47ae608
							https://www.freecodecamp.org/news/the-right-way-to-test-react-components-548a4736ab22/


						


				    ## Gitlab -> 

					    # Setup Gitlab

							https://medium.com/swlh/how-do-i-deploy-my-code-to-heroku-using-gitlab-ci-cd-6a232b6be2e4	
			    
			    
			    

				  ## Gitlab Error tracking 

				  https://sentry.io/integrations/gitlab/

				  https://about.gitlab.com/blog/2019/01/25/sentry-integration-blog-post/
	  
	  
	  
	  
	  
	  
# Extra
                               # Deploying to firebase

                                           https://medium.com/evenbit/automatically-deploy-to-firebase-with-gitlab-ci-546f194c44d8

                                    
                              

                               ## How express and react code co-exists on the server

                                              https://medium.com/jeremy-gottfrieds-tech-blog/tutorial-how-to-deploy-a-production-react-app-to-heroku-c4831dfcfa08
                                              https://www.freecodecamp.org/news/how-to-deploy-a-react-app-with-an-express-server-on-heroku-32244fe5a250/

		
    
                                     ## Monitoring tools: logrocket and sentry. 
                                    

                                     # Debugging and performance optimization

                                                Sentry acts as a bug tracker for your production code; tracking any javascript errors that may occur for users, and reporting them back to you so you can hopefully fix them

                                                logrocket appears to capture and forward logs from users browsers, and adds the ability to 'replay' the state of their browser to directly see the issue



                  ------------------ Sentry + logrocket +  Monitoring bugs & "User testing"  ---------------------


                                                    https://boredhacking.com/mock-sentry-in-jest/

                                                  https://blog.logrocket.com/extending-sentry-with-logrocket-52e2f5b67d5a/



                                                  ------------------ Github and Sentry ---------------------

                                                    https://sentry.io/integrations/github/
	
			
			
## Testing 


		There is a lot of code that exists just to connect other, more interesting code together and it can be a lot of trouble to write unit tests for all that connective tissue and you don't really get a lot of benefit from doing that.

		I think it's better to start with an integration test that covers all the connective tissue, such as rendering the entire route (so if your page renders a list of products at /products then your test does visit('/products') and renders the entire app and tests the most basic functionality). 

		Then instead of unit testing every single thing, you can just unit test the cases that aren't already covered by the integration test.


		@MrLeebo Thanks for your input. I"m still new at testing and I feel like I should be testing every piece of code I write. But what you're saying makes more sense. Thanks again, inputs like yours really help  understand the whole process.

		[don't try to achieve 100% test coverage. it's basically impossible to maintain. The time it takes to improve your test coverage gets exponentially harder the more coverage you have. From 0% coverage, if it takes you 1 day to get to 50%, it'll probably take 2-3 days to get 90%. After a week you might hit 99%, but it'll take another week to seal that remaining 1%. In that time, the code will probably change and you'll be a week out again

