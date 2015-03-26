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

7. Enter your credentials and api keys into the environment variables in pom.xml:


7. Compile the Java code and generate the war package using Maven:

		mvn package

8. Deploy your app:

		mvn -P deploy package

		or

		cf push ${app} -p BookClub-1.0.war

9. Access your app: [http://${route}](http://${route})
