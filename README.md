# Fitbit Java Client API OpenShift #

**NOTE.** This OpenShift quick start project is based on [Fitbit's Java Client API example project] (https://github.com/Fitbit/fitbit4j). I only added stuff needed for OpenShift. For more info about Fitbit4J and Fitbit API check the original [Fitbit's Java Client API example project] (https://github.com/Fitbit/fitbit4j) and [wiki.fitbit.com](http://wiki.fitbit.com)

**NOTE.** Fitbit4j client API cannot be found (at the time of writing this README) from any public Maven repo, so I included it as system scoped dependency from WEB-INF/lib dir. If you need to change Fitbit4j version, update file in WEB-INF/lib and make nessessary modifications to pom.xml

# What you need to get started #

You need [dev.fitbit.com](http://dev.fitbit.com) account and also [OpenShift Online](http://www.openshift.com) account. I you have both accounts, just skip this chapter.

## dev.fitbit.com ##
1. Go to [dev.fitbit.com](http://dev.fitbit.com)
2. Create account and follow instructions
3. Register new app (tab on the top of the page)
4. After app is registed api keys will be displayed to you. Copy to to notepad, textedit, etc. for later user
5. Fitbit part is done

## OpenShift online ##
1. Go to [OpenShift Online](http://www.openshift.com)
2. Sign up (top right corner)
3. After account is created and email vefified check [Getting started guide ](https://developers.openshift.com/en/getting-started-overview.html) to get started with OpenShift

# Create application to Openshift #

Here is only command line example for creating new Fitbit example on Openshift. You can also use Openshift's web interface or for example Eclipse (with JBoss Tools)

1. Open terminal, cmd etc (do 'rhc setup' if not yet done!)
2. cd /tmp (or what ever u like)
3. rhc app create fitbit jbossews-2.0 --from-code https://github.com/tahonen/openshift-fitbit-java-client-example
4. Check that URL from rhc app create response. That is the url where your app will be running.

Abobe steps will create OpenShift gear with Tomcat 7 installed and also git repo for your code. It will also clone newly created repo to you machine.

We are not ready yet. We have to setup API keys so that app can connect to Fitbit API server.

1. cd fitbit (assume that you are still in /tmp/fitbit)
2. edit file /src/main/resources/config.properties
3. Set Client (Consumer) Key to clientConsumerKey
4. Set Client (Consumer) Secret to clientSecret
5. save config.properties
6. change exampleBaseUrl to match you OpenShift app url and add /app at the end of the url. e.g. http://fitib-yournamespace.rhcloud.com/app
6. deploy application with git
7. git add .
8. git commit -am 'foobar'
9. git push

Wait for push to finish and the test your Fitbit integration. 

