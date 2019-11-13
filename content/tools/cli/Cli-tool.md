<!--
title: "CLI Tool"
description: "Instructions for installing the CLI tool for library analysis"
tags: "tools cli library install"
-->
  
Use Contrast's command line interface (CLI) tool to gather and send information for your applications to the Contrast UI. 

## How It Works

The Contrast CLI tool performs software composition analysis (SCA) on your application to show you where vulnerabilities were introduced, such as code from an open-source library. The SCA CLI tool gathers data on your application during its development phase that's typically not available until your application is in the deployment phase. Using the data captured by the tool, Contrast can provide a more detailed view of your applications in the Contrast UI.

For the CLI tool to work in tandem with the UI, it must identify itself with a set of credentials, and also identify the application of which it's providing analysis.  


## Before You Start 

Before you install and use Contrast's SCA CLI tool, verify that you've completed the following requirements.  

* All applications must have with the appropriate Contrast agent installed. For information on how to instrument your application with a Contrast agent, see the following instructions: 

 * [Java agent](installation-javastandard.html) 
 * [.NET agent](installation-netinstall.html) 
 * [.NET Core agent](installation-netcoreinstall.html) 
 * [Node agent](installation-nodeinstall.html)
 
* Source code for Java, .NET and Node applications must be available locally to be examined by the CLI tool: 

 * Java applications must have *Maven* installed with the [dependency plugin](https://maven.apache.org/plugins/maven-dependency-plugin/). 
 * .NET and .NET Core applications must have a *package.lock.json* file present.
 * Node applications must have a *package-lock.json* file present.
 
* Node.js must be installed. (The Contrast SCA CLI tool is executed as a Node.js package.) For information on how to install Node.js, please refer to their [documentation](https://nodejs.org/en/download/). 

### Credentials
 
* Gather the following Contrast credentials: 

 * API key
 * Organization ID
 * Contrast URL

To identify your credentials, see the [Profile Settings](user-account.html#profile) article.  

* Identify the [application ID](user-appsmanage.html) of the application you want to analyze. 


## Install 

Install the tool with the following command: 

```
npm install -g @contrast/contrast-sca 
```

Or, you can install the tool with Yarn with the following command: 

```
yarn global add @contrast/contrast-sca 
```

## Authenticate and Analyze 

Once the CLI tool is installed, you can analyze applications and see the results in the Contrast UI. Contrast recommends that SCA is invoked as part of a CI pipeline so that running the SCA is automated as part of your build process. 

Use the commands shown in the following example to analyze an application: 

```
contrast-sca \ 

 --api-key someAPIKey \ 

 --authorization someAuthorizationCredentials \ 

 --application-id someApplicationID \ 

 --organization-id someOrganizationID \ 

 --project-path applicationRootDirectory

```

<!-- 
### Review 

After you see a SUCCESS message you are now ready to view your dependency tree. (link to library hierarchy) 
-->

### Help 

The tool includes command line help, including the glossary of commands shown below, which you display with the `--h` option. 


| Command                   | Description                                                                               |
|---------------------------|-------------------------------------------------------------------------------------------|
| --api-key string          | An agent API key provided by Contrast UI (**required**)                                 |
| --authorization string    | Agent Authorization credentials provided by Contrast UI (**required**)                |
| --organization-id string  | The ID of your organization in Contrast UI (**required**)                                 |
| --application-id string   | The ID of the application cataloged by Contrast UI (**required**)                          |
| --host string             | The name of the host and (optionally) the port expressed as `<host>:<port>`; defaults to *app.contrastsecurity.com* (**optional**)|
| --project-path string     | The directory root of a project/application that you want to analyze; defaults to the current directory (**optional**) |
| --help                    | Display this usage guide                                                   	 			|
