# Basic Auth Lift Module

Provides Basic Auth into a [Lift](http://www.liftweb.net) application.

## Using this module

1. Add the following repository to your SBT project file:

    For SBT 0.10:

        resolvers += "liftmodules repository" at "http://repository-liftmodules.forge.cloudbees.com/release/"

    For SBT 0.7:

        lazy val liftModulesRelease = "liftmodules repository" at "http://repository-liftmodules.forge.cloudbees.com/release/"

2. Include this dependency:

         "net.liftmodules" %% "basic-auth" % (liftVersion+"-1.1")

3. In your application's Boot.boot code:

          net.liftmodules.basicauth.lib.BasicAuth.init
          
          BasicAuth.auth
          
4. Finally, add the following properties to the properties files you wish to have basic authentication.   For example, add the following to `src/main/resources/production.default.props` 
If you want all run modes to have authentication put them in default.props 

         
         liftmodules.basic.title=Protected Site
         liftmodules.basic.username=hello
         liftmodules.basic.password=hello
   

If there are paths you wish to exclude from authentication use the 
`liftmodules.basic.paths` property. This is a comma separated list of paths. We only match on the first part of the context path, e.g `liftmodules.basic.paths=moose` will give unauthorized access to any URL with the context path starting with moose e.g. http://localhost:8080/moose/id/123
  
