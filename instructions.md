Get started with Book Club
-----------------------------------
Welcome to Globalization Service Starter application!

This sample application demonstrates how to use the Globalization service in a Java Web application (powered by WebSphere Liberty) and deploy it on Bluemix.

1. [Install the cf command-line tool](${doc-url}/#starters/BuildingWeb.html#install_cf).
2. [Download the starter application package](${ace-url}/rest/apps/${app-guid}/starter-download).
3. Extract the package and `cd` to it.
4. Connect to Bluemix:

		cf api ${api-url}

5. Log into Bluemix:

		cf login -u ${username}
		cf target -o ${org} -s ${space}
		
6. Create a new WebSphere Liberty based application in the Bluemix dashboard and select 
a name and route for the application. The name and route that you seect 
will be used to access the application.

7. Create and bind the Globalization, Watson Machine Translation, and IBM Insights for Twitter services
to the application that you just created. The names you select for the services will be used in the
deploy script.
   

8. Obtain api keys for the New York Times Best Sellers, iDreamBooks, and AlchemyAPI services:

		http://developer.nytimes.com
		http://idreambooks.com/api
		http://www.alchemyapi.com
	 
9. Add a Stage from the "Build & Deploy" tab with a Build job type using the maven builder. Use the default archive directory of target.

10. Add a Stage from the "Build & Deploy" tab wih a Deploy job type. Fill in the fields for your Bluemix organization, space, and application name.

11. Edit the deploy script and fill in your credentials for 
the New York Times, iDreamBooks, and IBM AlchemyAPI services and names that you have used for the 
Watson MT, Globalization, and Insights for Twitter services.

		cf push "${CF_APP}" -p BookClub-1.0-SNAPSHOT.war -m 768M --no-start
		cf bind-service "${CF_APP}" "Watson Machine Translation service name"
		cf bind-service "${CF_APP}" "Globalization service name"
		cf bind-service "${CF_APP}" "Insights for Twitter service name"
		cf set-env "${CF_APP}" NY_TIMES_URL api.nytimes.com
		cf set-env "${CF_APP}" NY_TIMES_API_KEY "api key"
		cf set-env "${CF_APP}" DREAM_BOOKS_URL idreambooks.com
		cf set-env "${CF_APP}" DREAM_BOOKS_API_KEY "api key"
		cf set-env "${CF_APP}" ALCHEMY_API_KEY "api key" 
		cf start "${CF_APP}"

12. Access your app: [http://${route}](http://${route})
