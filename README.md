# Overview
 
This document outlines multiple methods to create or use existing service url.
 
# Approaches to use/create Constellation Service
=========================================================
 
<!--ts-->
   * [Method 1 : via docker image](#method-1--via-docker-image)
   * [Method 2 : via git code base](#method-2--via-git-code-base)
   * [Method 3 : via constellation service URL (**Recommended**)](#method-3--via-constellation-service-url-recommended)
<!--te-->
 
## Method 1 : via docker image
 
For users who are not merging Constellation code changes back to the repos, use this method to obtain and run Constellation via docker containers.
 
### Steps
 
1. Get the latest build:
    -   docker pull meshbincam.pega.com:7000/constellationui/service
 
2. Start the constellation service with reference to your Pega Platform instance (SSOT or SLS):
    -   docker run -p 3000:3000 --name constellation-service meshbincam.pega.com:7000/constellationui/service port=3000 infinity=http://lu-85-cam.eng.pega.com/prweb/ logLevel=info
    Replace lu-85-cam.eng.pega.com (or lu-84-cam.eng.pega.com) with the url (including port) for your Infinity service. On Mac do not use localhost, use your real ip.
 
## Method 2 : via git code base
 
For users who are not merging Constellation code changes back to the repos, use this method to obtain and run Constellation via docker containers.
 
### Steps
 
1. Retrieve the code from git using the following commands:
    -   git clone https://git.pega.io/scm/ps/constellationui.git
    -   cd constellationui 
 
2. Edit the configuration file that points to your Pega Platform instance (SSOT or SLS):
    -   Edit the url in the file npm-cli/config.json (if necessary)
        if the url is using https, make sure that the hostname matches the cert certificate
        Adjust checkAuthCookie setting (if want something other than the checked in current default)
        (0: No validation; 1: Validate All Requests; 2: Validate All Requests with Pega-AAT cookies; 3: Validate but ignore all errors)
 
3. Install NPM and NodeJS
    -   First install NPM and then node. You can do both using this npm package called n (node js version manager) with a          little "bootstrapping" to install both in one go. Make sure these tools are up-to-date as older versions might not         work.
        Ref:  https://www.npmjs.com/package/n
    
        If on a Linux environment you can follow the instructions in the package to install the LTS version of doing the following commands:
            curl -L https://raw.githubusercontent.com/tj/n/master/bin/n -o n
            bash n lts
 
4. Set your npm registry
    -   Important note: this is a one time only for your machine - skip if already done
        npm set registry https://meshbincam.pega.com/artifactory/api/npm/npmjs-dev
 
5. To build and start npm server
    -   constellationui > npm run clean (see constellation UI's README.md for a description & more scripts for build)
 
6. If want to Publish schema and configs
    -   constellationui> cd npm-nebula
        npm-nebula> npm run publishschema  (run only once on fresh SSOT server)
        npm-nebula> npm run sync-all  (needs to run every time you change a component definition)
 
## Method 3 : via constellation service URL (**Recommended**)
 
For users who are not merging Constellation code changes back to the repos & not creating any custom components, use this method to obtain and run Constellation via updating DSS setting in respective infinity system.
 
### Steps
 
1. Get lastet working Service URL from agile document(https://agilestudio.pega.com/prweb/AgileStudio/app/agilestudio/doc/DOC-39208) pulse comment.
    -   URL must be like "https://gloolb20200401094737987700000007-1100728290.us-east-1.elb.amazonaws.com"
 
2. Edit the DSS in your respective infinity system:
    -   Open Dynamic System Setting named as "ConstellationSvcURL" of class "Pega-UIEngine".
    -   Replace default value(http://localhost:3000/prweb/constellation) to URL from DOC-39208.
 

## For More Reference
 
https://agilestudio.pega.com/prweb/AgileStudio/app/agilestudio/doc/DOC-6087
 
 
