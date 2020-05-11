# CI-CD-Playground




# Test setup 

                             ## Create empty project https://www.freecodecamp.org/news/how-to-deploy-a-react-app-with-an-express-server-on-heroku-32244fe5a250/


                            ## Pre hooks ->  
                              
                              
                                    # Simple git hooks

                                    https://medium.com/better-programming/simple-git-hooks-with-create-react-app-eslint-and-husky-6983806dba5c


                            ## Gitlab -> 
                              
                                    # Setup Gitlab
			
		                              	https://medium.com/@mikenoethiger/setup-ci-cd-environment-with-gitlab-a00d7343fb1d
			

                             ## Staging-> Unit-testing(Storybook.js)-> 


                                        ## StoryBook Component Stories and Snapshot testing

                                        ## Storybook spec file for test stage.

                                              https://www.youtube.com/watch?v=va-JzrmaiUM
                                              https://www.youtube.com/watch?v=9B-IB2U3qSI
                                              https://www.youtube.com/watch?v=q248uxiicwY
                                              https://blog.logrocket.com/react-storybook/


                                        ##Gitlab and Unit testing integration

                                               https://medium.com/faun/integrate-unit-testing-with-gitlab-pipelines-basics-4c85e47ae608


                              
                              ##SSH -> Production    
                              
                                     # https://medium.com/swlh/how-do-i-deploy-my-code-to-heroku-using-gitlab-ci-cd-6a232b6be2e4	
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




			

# Ecommerce Project ------------------------------

			https://dev.to/kodekloud/things-to-consider-while-building-a-ci-cd-pipeline-1419	
			
			
			Arhitecture flow:

			Dev -> 

			pre hook ->   

			Github -> 

			CI/CD (gitlab) ->

			Staging (unit tests) (Storybook stories + component testing) -> 

			(Project build (minifying etc happens here)) ->  

			Deployed to Heroku // Firebase -> (Live in production)

			implemented (Sentry and Logrocket monitoring)
			
			
			
## CI/CD 
			
			
