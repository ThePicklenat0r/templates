# Azure Pipeline Templates for Hass.io Add-Ons

Copy the azure-pipelines.yml file into the add-on repository and update the three parameters.

In the add-on repository, create a folder that matches the slug of the addon, all of your addon files should be here, except for the README.md file. Keep any other files (such as the azure-pipelines.yml) in the root of the repository.

**_IMPORTANT:_** _The addon parameter, slug in config.json, and folder in the addon repository should all match._

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
  gitAddonRepo | GitHub repository that contains your repository.json file. These templates will probably not work if it is in the same file as your addon's code. This should be the name only.
  gitAddonRepoBeta | GitHub repository used for beta builds. This will be used if the release has a "b" in the name. (e.g. 1.0b0) (Optional: if not set, all releases will be published to the repository defined in gitAddonRepo.
  gitAddonRepoShort | Just the name of the repository used in gitAddonRepo and gitAddonBeta
  githubToken | Personal Access token for GitHub (create a new one for each project)
  gitUserEmail | The email associated with your GitHub account
  gitUser | Your GitHub username
  gitUserName | Your name in friendly format e.g. John Doe


Then create a pipeline and point it to azure-pipelines.yml in your addon's GitHub repository.

The addon should automatically build when a tag is created. The tag/release name will be used as the version number, so limit these to just the version e.g 1.1, v1.1, 1.1b0, etc.
