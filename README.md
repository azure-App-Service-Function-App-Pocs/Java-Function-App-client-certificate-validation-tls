# Java-Function-App-client-certificate-validation-tls
Java Function App using incoming Client Certificate to authenticate user with Function App execution

---
page_type: sample
languages:
- java
products:
- function app
description: "Java Function App using incoming Client Certificate to authenticate user with Function App execution"
urlFragment: "update-this-to-unique-url-stub"
---

# Sample

<!-- 
Guidelines on README format: https://review.docs.microsoft.com/help/onboard/admin/samples/concepts/readme-template?branch=master

Guidance on onboarding samples to docs.microsoft.com/samples: https://review.docs.microsoft.com/help/onboard/admin/samples/process/onboarding?branch=master

Taxonomies for products and languages: https://review.docs.microsoft.com/new-hope/information-architecture/metadata/taxonomies?branch=master
-->

This repository shows a sample Java Function App using incoming Client Certificate to authenticate user with Function App execution.

## Contents

Outline the file contents of the repository.

| File/folder       | Description                                |
|-------------------|--------------------------------------------|
| `src/`            | Java application source folder |
| `.gitignore`      | Define what to ignore at commit time.      |
| `README.md`       | This README file.                          |
| `LICENSE`         | The license for the sample.                |

## Prerequisites

You should have the following development tools installed on your local machine.

- [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview/)
- [VS Code](https://code.visualstudio.com/)
- [Maven](https://maven.apache.org/download.cgi) (optional)

You will also need accounts for the following services

- [Microsoft Azure](https://azure.microsoft.com/)

## Running the sample

### Build and test locally

<!-- 
Outline step-by-step instructions to execute the sample and see its output. Include steps for executing the sample from the IDE, starting specific services in the Azure portal or anything related to the overall launch of the code.
-->

Before deploying to App Service, build and run the Function locally.

```shell
mvn clean package
mvn azure-functions:run
```

Open a browser to [http://localhost:7071/api/auth](http://localhost:7071/api/auth) and should display 401 - UNAUTHORIZED, which is normal because we are not making the call with calls with certificate.

### Publish the application to a Function App

Now that the Function App works locally, we will push the jar to our registry so our Function App can run the jar. First, run the below command to be login into Azure Cli and deploy to a specific Function App.

- [Deploy the function project to Azure](https://docs.microsoft.com/en-us/azure/azure-functions/create-first-function-cli-java?tabs=bash%2Cazure-cli%2Cbrowser#deploy-the-function-project-to-azure)

```shell
az login
mvn azure-functions:deploy
```

Once your Function App is deployed, you can now just simply enable Incoming Client Certificate on Azure so incoming requests are challeneged.  

- [Repo is based on this article](https://blog.neostarteon.com/tls-mutual-authentication-or-incoming-client-certificate-on-azure-app-service-function-app/)


