# Manage Repository Profiles

* Adding a Repository Type
  * Adding a Github Repository
    * 1\. Create a New Github Repository or Use an Existing Repository
    * 2\. Create a Personal Access Token from Github Developer Settings
    * 3\. Add Repository Profile in ASM
  * Adding Other Repository Types
    * HTTP
    * Bitbucket
    * Azure DevOps

Postman collections and Scripted Check scripts are not uploaded to the ASM platform. Instead, they are managed through a repository which is created by the end user. This repository is set up from within the “Manage > Repository Profiles” page:



Users can view and add new Repository Profiles from this page. A Repository Profile holds a repository URL and authentication details to the repository so users do not have to add that information every time they set up a check.

To create a new Repository Profile, click on the “New Profile” button, select a Type, and click “Create Profile”:



## Adding a Repository Type <a href="#managerepositoryprofiles-addingarepositorytype" id="managerepositoryprofiles-addingarepositorytype"></a>

Add your project’s base Repository URL when you create a Repository Profile. You will have the option to add a more specific file path when you create a check which utilizes the repository.

### Adding a Github Repository <a href="#managerepositoryprofiles-addingagithubrepository" id="managerepositoryprofiles-addingagithubrepository"></a>

In order to set up a GitHub repository, you will need to create a GitHub Personal Access Token from within Github itself. Perform the following steps to create and add a Github repository as a repository profile.

#### 1. Create a New Github Repository or Use an Existing Repository <a href="#managerepositoryprofiles-1.createanewgithubrepositoryoruseanexistingrepository" id="managerepositoryprofiles-1.createanewgithubrepositoryoruseanexistingrepository"></a>

The repository can be public or private. It is recommended that you use a private repository as it will provide a higher GitHub token rate limit.



#### 2. Create a Personal Access Token from Github Developer Settings <a href="#managerepositoryprofiles-2.createapersonalaccesstokenfromgithubdevelopersettings" id="managerepositoryprofiles-2.createapersonalaccesstokenfromgithubdevelopersettings"></a>

The Personal Access Token will grant ASM permission to access scripts which you’ve hosted on GitHub.



Click "**Generate new token**” and enter your GitHub password if prompted. It is recommended that you add a note to describe that you are using the personal access token for an Apica integration:



For this example, only we'll set no expiration because we don't want this token to expire, but you can set a token expiration date as your security policy requires.

The token only requires the “repo” scope!

Finally, click **Generate token**.

Make sure to copy your personal access token now. You won't be able to see it again!

#### 3. Add Repository Profile in ASM <a href="#managerepositoryprofiles-3.addrepositoryprofileinasm" id="managerepositoryprofiles-3.addrepositoryprofileinasm"></a>

From within the “Manage Profiles” page, add the repository URL, your Username, and your Personal Access Token:



As the screenshot indicates above, the Repository URL consists of a string formatted in the following structure:

`https://github.com/{username}/{repositoryName`}

If the repository contains a subfolder, such as /postmanChecks, you will reference that when you create a Scripted or Postman check later. Just enter the base repository URL here.

Paste the Personal Access Token you created above in the “Github Personal Access Token” field.

### Adding Other Repository Types <a href="#managerepositoryprofiles-addingotherrepositorytypes" id="managerepositoryprofiles-addingotherrepositorytypes"></a>

| <h4 id="managerepositoryprofiles-http">HTTP</h4><p>It is possible to store files on an HTTP server and retrieve them with HTTP Basic authentication. Enter the base path to the repository within the repository profile; you will add a more specific file path when you create a Postman or Scripted check.</p> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <h4 id="managerepositoryprofiles-bitbucket">Bitbucket</h4><p>For Bitbucket Cloud/DC/Server Users enter the Bitbucket:</p><ul><li><strong>Repository URL</strong></li><li><strong>Username</strong></li><li><strong>App Password</strong></li></ul>                                                                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| <h4 id="managerepositoryprofiles-azuredevops">Azure DevOps</h4><p>For Azure DevOps Users enter the Azure DevOps:</p><ul><li><strong>Repository URL</strong></li><li><strong>Username</strong></li><li><strong>Personal Access Token</strong></li></ul>                                                            | <p></p><p>The DevOps Repository URL might look different depending on the configuration or the installation of the Azure DevOps server. Some typical valid TFS project URLs are:</p><ul><li><a href="http://myserver:8080/tfs/project-name">http://myserver:8080/tfs/project-name</a> -- on premises Azure DevOps installation (Azure DevOps Server / Team Foundation Server)</li><li><a href="https://myserver/tfs/project-name">https://myserver/tfs/project-name</a> -- on premises Azure DevOps installation with HTTPS</li><li><a href="http://myserver:8080/tfs/DefaultCollection/project-name">http://myserver:8080/tfs/DefaultCollection/project-name</a> -- on premises Azure DevOps installation with a project collection</li><li><a href="http://myserver:8080/tfs/project%20name">http://myserver:8080/tfs/project name</a> -- space in the project name (project name)</li><li><a href="https://myorganization.visualstudio.com/MyProject">https://myorganization.visualstudio.com/MyProject</a> -- Azure DevOps project created earlier</li><li><a href="https://dev.azure.com/myorganization/MyProject">https://dev.azure.com/myorganization/MyProject</a> -- Azure DevOps project created recently</li></ul> |
