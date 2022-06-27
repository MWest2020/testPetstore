# Pet Store API

[![Automated Testing](https://github.com/CommonGateway/PetStore/actions/workflows/tests.yml/badge.svg)](https://github.com/CommonGateway/PetStore/actions/workflows/tests.yml)


This repository is an example of a [Common Gateway](https://github.com/CommonGateway) configuration for generating an [API](https://www.howtogeek.com/343877/what-is-an-api/). This example has been specifically set up to use as a template to create and use a repository which holds a API definiton as a OpenAPI Specification or setup and use a existing OpenAPI Specification as API. 

This repository is named the PetStoreAPI because its a standard scenario many people use to design their first API/datamodel.

To start with creating or setting up a repository with a OpenAPI Specification start with [creating your repository from this template](#creating-your-repository-from-this-template). This step will start and guide you through the process.

Quick links about this repository:

- [API Documentation (redocly is a API documentation generator)](https://redocly.github.io/redoc/?url=https://raw.githubusercontent.com/CommonGateway/PetStore/main/OAS.yaml&nocors)
- [API Definition (yaml or json file)](https://github.com/CommonGateway/PetStore/blob/main/OAS.yaml)
- [Public Code (file about this API and makes it searchable)](https://github.com/CommonGateway/PetStore/blob/main/publiccode.yaml)
- [Stoplight.io (OAS editing tool)](https://conduction.stoplight.io/docs/pet-store)


It is also possible to [use this repository with its API with the skeleton-app](#running-the-api-with-the-skeleton-app).

## Requirements

- A [stoplight.io account](https://stoplight.io/login/).
- A [GitHub account](https://github.com/login).
- [Git](https://git-scm.com/download/win) or any [Git GUI](https://git-scm.com/downloads/guis) (we recommend [GitKraken](https://www.gitkraken.com).
- A code editor (notepad or any IDE).
- [Docker desktop](https://www.docker.com/products/docker-desktop/).

## Creating your repository from this template

To use this repository as a template, you will need a [GitHub account](https://github.com/login). Make sure you have a GitHub account and are logged in on GitHub. When you are logged in you can [use this template](https://github.com/CommonGateway/PetStoreAPI/generate), select the owner and fill in a nice name for your new repository. After creating your new repository, please follow these steps:

- Go to your new created GitHub repository.
- Replace the OAS.yaml (or .json) file in the repository root with [your own OpenAPI Specification](#your-openapi-specification).
- [Add your Open API Specification (OAS) to your repository](#adding-your-oas-to-your-repository).
- Open the `publiccode.yaml` file.
- Press the `edit icon` (pencil) in the top right of the code viewer.
- Change the following in the file:
    1. `name` to the name of your API.
    2. `url` to the url of this GitHub repository. 
    3. `description` to the description of your API.
    4. `releaseDate` to a earlier date if already released or TBA (to be announced).
    5. Scroll down to `description`
    6. Change both for `en` and `nl` the `shortDescription`, the `documentation` to `https://redocly.github.io/redoc/?url=https://raw.githubusercontent.com/{yourOrganizationOrUserName}/{yourRepositoryName}/main/OAS.yaml&nocors` and the `apiDocumentation` to `https://raw.githubusercontent.com/{yourOrganizationOrUserName}/{yourRepositoryName}/main/OAS.yaml`
    7. Change `OAS.yaml` to `OAS.json` if your OAS is a json file.
    8. Enter a nice commit message and press `Commit changes` below the code viewer.
- Open the README.md file and alter it to suit your project (don't forget to update the URL of the status badge)
- If you want your API to be downloadable through the Common Gateway API store make sure that your repository is set to public
- Open the publiccode.yaml in your repository on GitHub.
- Click the `raw` button on the top right of the code viewer.
- Copy the url from your browser.
- Open .env from your repository and press the `edit icon` (pencil) in the top right of the code viewer.
- Scroll to the bottom and find `PUBLICCODE`.
- Overwrite the url with your publiccode url.

After following these steps your repository should be set up properly.
To test your repository locally read [running the api locally](#running-the-api-locally).
If you want to have your API set up online read [running the api online](#running-the-api-online).

## Your OpenAPI Specification

What is a OpenAPI Specification

The OpenApi Specification(OAS) defines a standard, language-agnostic interface to RESTful APIs, allowing humans and computers to discover and understand the service's capabilities without access to source code, documentation, or network traffic inspection. When properly defined, a consumer can understand and interact with the remote service with minimal implementation logic.

Documentation generation tools can then use an OpenAPI definition to display the API, code generation tools to generate servers and clients in various programming languages, testing tools, and many other use cases.

This template uses the OAS as an API definition for the reasons above.

If you don't have a Open API Specification yet you can continue with [creating your oas](#creating-your-oas), if you already have a Open API Specification but you want to edit you can go to [editing your oas](#editing-your-oas). If you already have a Open API Specification, you can go to continue to [adding your OAS to your repository](#adding-your-oas-to-your-repository).

### Creating your OAS

Writing the Open API Specification standard yourself is very error-prone. We recommend using [Stoplight](https://stoplight.io) for the automatic generation of an OAS, but there's also [Postman](https://www.postman.com). For checking, there are also editors, like <https://editor.swagger.io>.

The OAS can be defined in both JSON and YAML. It shouldn't make a difference in most cases, and although we often work from a YAML-first basis, there have been times were working with JSON was superior.

To create your OAS with [Stoplight](https://stoplight.io/), follow these steps:

- Register or log in on [Stoplight](https://stoplight.io/).
- Create a workspace or use a existing one.
- Navigate to projects in the top navigation or go to yourworkspacename.stoplight.io/admin/projects.
- Create a new project with the `New Project` button in the top right corner.
- To create a new API, create a blank project with a proper name.
- Press the `API` button in the mid left window and fill in your API name, then press create.
- Go to `Overview`, find `Servers` and make sure there is 1 server with value `http://localhost/api`.
- Firstly, you can remove all standard Paths. Right click one in the bottom left and press `Delete Path`. The same should be done for `Models` except if you would like to keep the example.
- Then you should create a model (object) which we can link to a path later. Right-click on 'Models' in the bottom left window and select 'New model'. Here you can define an object.
- You can create paths (endpoints) by right-clicking on 'Paths' in the bottom left window and selecting 'New Path'. You can add multiple methods to your path by selecting one and pressing the + operation button.
- To link a path with a model, you can select a path, add or select a response, add or select `body` from that response, and then if this path is for collections, select `array` as a type with a subtype `$ref` or if this path is for a single object select `$ref` as type. You can then find your created model and link it.
- If you are satisfied with your created API you can save it by selecting `Publish` in the top left of the page. Next, we want to export this OpenAPI Specification by righting clicking your .yaml file in the top left section of the page and selecting `Export`. Choose the format YAML and press `Save to file`.

You have now downloaded your OpenAPI Specification (OAS). Continue to [adding your OAS to your repository](#adding-your-oas-to-your-repository).

### Editing your OAS

To edit your OAS with [Stoplight](https://stoplight.io/), follow these steps:

- Register or log in on Stoplight.
- Create a workspace or use a existing one.
- Navigate to projects in the top navigation or go to yourworkspacename.stoplight.io/admin/projects.
- Create a new project with the `New Project` button in the top right corner.
- To edit an already existing Open API Specification and you have that file, you can choose to `Import OpenAPI file`.
- Go to `Overview`, find `Servers` and make sure there is 1 server with value `http://localhost/api`.
- Firstly, you should create a model (object) which we can link to a path later. Right-click on 'Models' in the bottom left window and select 'New model'. Here you can define an object.
- You can create paths (endpoints) by right-clicking on 'Paths' in the bottom left window and selecting 'New Path'. You can add multiple methods to your path by selecting one and pressing the + operation button.
- To link a path with a model, you can select a path, add or select a response, add or select `body` from that response, and then if this path is an array of objects select `array` as type with subtype `$ref` or if this path is for a single object select `$ref` as type. In the `$ref` search box you can find and select your created models.
- If you are satisfied with your created API you can save it by selecting `Publish` in the top left of the page. Next, we want to export this OpenAPI Specification by righting clicking your .yaml file in the top left section of the page beneath `Reference` and selecting `Export`. Choose the format YAML or JSON and press `Save to file`.

You have now downloaded your OpenAPI Specification (OAS). Continue to [adding your OAS to your repository](#adding-your-oas-to-your-repository).

### Adding your OAS to your repository

Now you want to have your OAS in your repository, so that the CommonGateway can work with it.
You can add the OAS in 2 ways. The simplest is the following for those who don't have Git or a Git GUI, and are not familair with a IDE. 

- Go your repository page and open the OAS.yaml and press the `edit icon` (pencil) in the top right of the code viewer.
- Open your local OAS file and copy its content.
- Paste the copied content into the OAS.yaml you opened on GitHub, overwriting its content.
- If your OAS is a .json file make sure to change the OAS.yaml to OAS.json.
- Fill a basic commit message in the bottom of the screen like `OAS updated` and press `Commit changes`.

For those familiar with Git and their IDE, you can [clone this repository](#cloning-your-repository) and overwrite the OAS.yaml with your own OAS. Don't forget to commit push.

Your created OAS is now in your new repository. You can always view or edit it through Stoplight and export it again, then overwriting the OAS.yaml in your repository. You can continue with the other steps from [this guide](#creating-your-repository-from-this-template).

## Cloning your repository

First of all:

- Go to your GitHub repository page.
- Look for the `Code` button in the top right of the page.
- Copy the https link.

If you installed Git without GUI:

- Open a command line interface, for windows you can press `Win+R` and search for `cmd`.
- Execute the command `git clone (link you copied) (directory you want to clone the repository to`, an example: `git clone https://github.com/CommonGateway/PetStoreAPI.git C:\Users\JohnDoe\Projects`.
- Change to that directory with `cd (directory where repository is cloned to)`, an example: `cd C:\Users\JohnDoe\Projects\PetStore`.

Skip this if you already installed Git without GUI and followed the above steps, but if you installed Git with a GUI (GitKraken) and want to clone with that GUI:

- Open GitKraken.
- Select `Clone a repo`.
- Paste your copied repository link and select the preferred directory.

Now you have your repository cloned locally. You can view it with a file explorer or any IDE at you chosen directory. If you want to test your API locally you can continue with [running the API locally](#running-the-api-locally).

## Running the API locally

Running this repository with its API (as Open API Specification) can be done through various ways. Make sure you firstly have this repository [cloned to your computer](#cloning-your-repository). 
If you are familiar with Docker, Git and a http client you can execute the following commands and tests your API project on localhost/api.

```bash
git clone https://github.com/CommonGateway/PetStoreAPI.git
cd PetStoreAPI
docker-compose up
```

For those not familiar, below is a detailed walkthrough.

### Running the API with docker

You will need [Docker desktop](https://www.docker.com/) installed to run this API project dockerized. Docker will run your Open API Specification on the Common Gateway on dockerized containers so you dont have to worry about having the correct PHP version or other languages/dependencies.

- Open a command line interface, for windows you can press `Win+R` and search for `cmd`.
- Change to the chosen directory with `cd (directory where repository is cloned to)`, an example: `cd C:\Users\JohnDoe\Projects\PetStore`.

- Execute `docker-compose pull`
- Execute `docker-compose up`
- Wait for containers to finish loading.
- If the php container shows: 'Ready to handle connections' your API is accessible on localhost/api or localhost:80/api.

If there are any issues when loading the containers try to execute: `docker-compose pull` and then try `docker-compose up` again. Otherwise continue to [testing with http requests](#testing-with-http-requests).

### Testing with http requests

To test your API you will need a [http](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) request client. We recommend [Postman](https://www.postman.com) but any client will suffice. Here is a list if you want to find a client yourself: [https://rapidapi.com/blog/best-api-clients/](https://rapidapi.com/blog/best-api-clients/).

In this example we will use Postman.

- Sign up or login on [Postman](https://www.postman.com).
- [Download Postman](https://www.postman.com/downloads/).
- Open Postman.
- Postman will give you a workspace.
- Go to `APIs` in the left menu.
- Press the `Create an API` next to the left menu.
- Switch to the `Import` tab.
- Select the bottom option `Select files`.
- Choose your OAS.yaml (or .json) and upload it.
- Click `Import` in the bottom right of the modal.
- Postman has now generated a test collection for your API.
- Go to `Collections` in the left menu. 
- Open your new collection and check out some requests.
- Make sure that your requests for a single object have a proper id.
- Make sure with POST and PUT requests that the body is correct. Postman doesn't uses your example bodies, so integer properties and enums and other validations should be set accordingly.
- Hit the `Send` button in the top right of the page.
- Check the result in the bottom response body.

Based on your request the response may differ. You know now how to test your API.
If you change your API and your OAS, you can re-import that file and re-generate a collection.

## Running the API online

// TODO more explaination
To run the API on a online Gateway, the `helm` secret `PUBLICCODE` must be set with the url to the raw `publiccode.yaml`, like:
`https://raw.githubusercontent.com/CommonGateway/PetStoreAPI/main/publiccode.yaml`

If set you can run the following command in a PHP pod:

`bin/console app:load-publiccodes`

The console should show if the API has been loaded successfully, and then you can make API http requests to `[yourdomain]/api`. If you need more info about testing your API, read [testing with http requests](#testing-with-http-requests).

## Running the API with the skeleton-app

To run your created API with the [skeleton-app](https://github.com/ConductionNL/skeleton-app), make sure u have raw url of the publiccode.yaml of the API you want to use. If you followed the guide in this repository, you can use the raw url to that publiccode.yaml of the API you created.
- Go to the GitHub repository of your API.
- Open the publiccode.yaml and click the `raw` button in the top right of the code viewer.
- Copy the url in your browser.
- Go to your skeleton-app repository.
- Open .env.
- Scroll down and find `PUBLICCODE` and set the value with your copied url.
- Run the local docker-compose file from your skeleton-app project, if you don't know read [running the api with docker](#running-the-api-with-docker) but keep in mind that you are running the API in your skeleton-app repository, and not the API repository itself.


## (Unit) Testing the API

// TODO new text about unit testing in gateway (still needs to be build in gateway?)
GitHub launches an action on every commit that generates a Postman collection and tests the API. You view the action results under `Actions` on the GitHub repository page.

## About Common Gateway configuration files

// TODO ELABORATE

