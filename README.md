# Apache Lucene, Apache Solr and Elasticsearch comparison on AEM 6.4

Goal of this project is to explore capabilities of ***search engines*** mentioned in title on different types of content and with different technical cases, together with their behaviour on AEM's technology stack.

This project is practical part of Master's Thesis "***Implementing Search Engines in Adobe Experience Manager***" on Faculty of Organization and Informatics.

Since proper testing of search engine's capabilities, the one needs large amount of data. To avoid thinking and planing of all of the content on site,
decision was made to use existing AEM reference site - We Retail.

The whole Master's Thesis will be published here as soon as the project is done.

Copy of original readme file of ***We Retail*** project follows:

# We.Retail
[![Build Status](https://travis-ci.org/Adobe-Marketing-Cloud/aem-sample-we-retail.png?branch=master)](https://travis-ci.org/Adobe-Marketing-Cloud/aem-sample-we-retail)

This is an AEM 6.4 reference implementation for the retail industry.

## Modules

The main parts of the template are:

* core: Java bundle containing all core functionality like OSGi services, listeners or schedulers, as well as component-related Java code such as servlets or request filters.
* ui.apps: contains the /apps (and /etc) parts of the project, ie JS&CSS clientlibs, components, templates, runmode specific configs as well as Hobbes-tests
* ui.content: contains sample content using the components from the ui.apps
* it.tests: Java bundle containing JUnit tests that are executed server-side. This bundle is not to be deployed onto production.
* it.launcher: contains glue code that deploys the ui.tests bundle (and dependent bundles) to the server and triggers the remote JUnit execution
* all: additional module to build a single package embedding ui.apps and ui.content

## How to build

To build all the modules run in the project root directory the following command with Maven 3:

    mvn clean install

If you have a running AEM instance you can build and package the whole project and deploy into AEM with  

    mvn clean install -PautoInstallPackage
    
Or to deploy it to a publish instance, run

    mvn clean install -PautoInstallPackagePublish
    
Or to deploy only the bundle to the author, run

    mvn clean install -PautoInstallBundle

To build a single package

    mvn clean install -PbuildSinglePackage

To install single package on an AEM instance

    mvn clean install -PbuildSinglePackage -PautoInstallSinglePackage
    

### UberJar

This project relies on the unobfuscated AEM 6.2 cq-quickstart. This is not publicly available from http://repo.adobe.com and must be 
manually 
downloaded from https://daycare.day.com/home/products/uberjar.html. After downloading the file (_cq-quickstart-6.2.0-apis.jar_), you must install it into your local Maven repository with this command:

    mvn install:install-file -Dfile=cq-quickstart-6.2.0-apis.jar -DgroupId=com.day.cq -DartifactId=cq-quickstart -Dversion=6.2.0 -Dclassifier=apis -Dpackaging=jar

## Testing

There are three levels of testing contained in the project:

* unit test in core: this show-cases classic unit testing of the code contained in the bundle. To test, execute:

    mvn clean test

* server-side integration tests: this allows to run unit-like tests in the AEM-environment, ie on the AEM server. To test, execute:

    mvn clean integration-test -PintegrationTests

* client-side Hobbes.js tests: JavaScript-based browser-side tests that verify browser-side behavior. To test:

    in the navigation, go the 'Operations' section and open the 'Testing' console; the left panel will allow you to run your tests.


## Maven settings

The project comes with the auto-public repository configured. To setup the repository in your Maven settings, refer to:

    http://helpx.adobe.com/experience-manager/kb/SetUpTheAdobeMavenRepository.html
