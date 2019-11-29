# Azure Pipeline Templates for Hass.io Add-Ons

Copy the azure-pipelines.yml file into the add-on repository and update the three parameters.

Create a project on Azure DevOps and create two variable groups:

## docker

  **var** | **Description**
  --- | ---
  dockerRepo | The Docker Hub repository to publish builds to
  dockerToken | Your Docker Hub Access Token (create a new one for each project)
  dockerUser | The Docker Hub user used to authenticate

## github

  **var** | **Description**
  --- | ---
  gitAddonRepo | URL to the github repository that contains your repository.json file. These templates will probably not work if it is in the same file as your addon's code.
  gitAddonRepoShort | Just the name of the repository used in gitAddonRepo
  githubToken | Personal Access token for GitHub (create a new one for each project)
  gitUserEmail | The email associated with your GitHub account
  gitUserName | Your name in friendly format e.g. John Doe


Then create a pipeline and point it to azure-pipelines.yml in your addon's GitHub repository.

The addon should automatically build when a tag is created. The tag/release name will be used as the version number, so limit these to just the version e.g 1.1, v1.1, version 1.1, etc.