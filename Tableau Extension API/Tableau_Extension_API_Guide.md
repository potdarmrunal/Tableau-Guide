<h3>Tableau Extension API</h3>
<hr/>

Offical website - https://www.tableau.com/developer/extensions#reveal-162758

Tableau extension API is an object provided in tableau dashboaard.It will be nothing but an web application which user can integrate in tableau dashboard. 

Tableau has Web Page object but that is differnet from extension, using tableau extension user can interact with tableau dashboard/worksheet data,filters,parameters,etc.

Exetnsion API provide access to intract with tableau insights.

To start with extension api user must need tableau extension api lib. Here is link for latest [version 1.10] - https://github.com/tableau/extensions-api/blob/main/lib/tableau.extensions.1.latest.min.js
And you need any server to host your application like npm or tomcat or any which you prefer.

Structure of source code of tableau extension api : It contains 3 main files
1. UI file where user will render it's view 
2. Busniess Logic file where user will add logic for application
3. Trex file where url of hosted web will be mentioned and this .trex file is needed to add extension on tableau dashboard

Explaining sample here for simple web application using tomcat server
a)Sample.html
<html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Sample</title>

    <!-- jQuery -->
    <script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>

    <!-- Extensions Library -->
    <script src="https://github.com/tableau/extensions-api/blob/main/lib/tableau.extensions.1.latest.min.js"></script>

    <!-- business logic -->
    <script src="./sample.js"></script>
  </head>
  <body>
    
  </body>
</html>

b)Sample.js
tableau.extensions.initializeAsync().then(function () { 
    console.log("Hello ExtensionAPI");
 });

c)Sample.trex
<?xml version="1.0" encoding="utf-8"?>
<manifest manifest-version="0.1" xmlns="http://www.tableau.com/xml/extension_manifest">
  <dashboard-extension id="com.tableau.extensions.samples.formatting" extension-version="0.6.0">
    <default-locale>en_US</default-locale>
    <name resource-id="name"/>
    <description>Tableau Sample</description>
    <author name="tableau" email="projectfrelard@tableau.com" organization="tableau" website="https://www.tableau.com"/>
    <min-api-version>1.1</min-api-version>
    <source-location>
      <url>http://localhost:8080/extension/sample.html</url>
    </source-location>
    <icon>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</icon>
  </dashboard-extension>
  <resources>
    <resource id="name">
      <text locale="en_US">Tableau Sample</text>
    </resource>
  </resources>
</manifest>

host this application on server and drag extension object in tableau analytic pane configer .trex file and that's it you can see your web app in tableau dashboard.

Details of .trex files by Andre de Vries are attached here - https://www.theinformationlab.co.uk/2018/08/07/whats-this-new-trex-filetype/

Method References - https://tableau.github.io/extensions-api/docs/globals.html

Offical Extension Samples - https://github.com/tableau/extensions-api/tree/main/Samples

Article By Keshia - https://sliceofkeesh.com/post/snippets-popular-extensions-api-patterns
