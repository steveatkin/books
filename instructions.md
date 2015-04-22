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

6. Obtain api keys for the New York Times Best Sellers, iDreamBooks, and AlchemyAPI services:

	 http://developer.nytimes.com
	 http://idreambooks.com/api
	 http://www.alchemyapi.com
	 
7. Add a Stage from the "Build & Deploy" tab with a Build job type using the maven builder. Use the default archive directory of target.

8. Add a Stage from the "Build & Deploy" tabe wih a Deploy job type. Fill in the fields for your Bluemix organization, space, and application name.

9. Edit the deploy script and fill in the name of your WAR file and your credentials for the New York Times, iDreamBooks, and IBM AlchemyAPI services.

	cf push "${CF_APP}" -p "put name of war file here" -m 768M --no-start
	cf bind-service "${CF_APP}" "put name of Watson Machine Translation service here"
	cf bind-service "${CF_APP}" "put name of Globalization service here"
	cf bind-service "${CF_APP}" "put name of Insights for Twitter service here"
	cf set-env "${CF_APP}" NY_TIMES_URL api.nytimes.com
	cf set-env "${CF_APP}" NY_TIMES_API_KEY "put api key here"
	cf set-env "${CF_APP}" DREAM_BOOKS_URL idreambooks.com
	cf set-env "${CF_APP}" DREAM_BOOKS_API_KEY "put api key here"
	cf set-env "${CF_APP}" ALCHEMY_API_KEY "put api key here" 
	cf start "${CF_APP}"


10. Access your app: [http://${route}](http://${route})
