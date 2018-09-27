Spring Security OAuth2 Azure Plugin
======================================

Add a Azure OAuth2 provider to the [Spring Security OAuth2 Plugin](https://github.com/MatrixCrawler/grails-spring-security-oauth2).

Installation
------------
Add the following dependencies in `build.gradle`
```
dependencies {
...
    compile 'org.grails.plugins:spring-security-oauth2:1.1+'
    compile 'org.grails.plugins:spring-security-oauth2-twitter:1.0.0'
...
}
```

Usage
-----
Add this to your application.yml
```
grails:
    plugin:
        springsecurity:
            oauth2:
                providers:
                    azure:
                        api_key: 'azure-app-id'                #needed
                        api_secret: 'azure-app-key'            #needed
                        successUri: "/oauth2/azure/success"    #optional
                        failureUri: "/oauth2/azure/failure"    #optional
                        callback: "/oauth2/azure/callback"     #optional
```
You can replace the URIs with your own controller implementation.

In your view you can use the taglib exposed from this plugin and from OAuth plugin to create links and to know if the user is authenticated with a given provider:
```xml
<oauth2:connect provider="azure" id="azure-connect-link">Twitter</oauth2:connect>

Logged with Azure?
<oauth2:ifLoggedInWith provider="azure">yes</oauth2:ifLoggedInWith>
<oauth2:ifNotLoggedInWith provider="azure">no</oauth2:ifNotLoggedInWith>
```
License
-------
Apache 2
