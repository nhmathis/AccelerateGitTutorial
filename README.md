# Table of Contents
1. [Accelerate](#accelearate-out-of-the-box)
2. [What is Value Stream Management](#why-value-stream-management)
3. [Git Hub](#github-set-up)
4. [Integration ](#integration-set-up)
5. [VSM](#vsm-set-up)
6. [Good to go!](#congrats-you-are-all-set)



<p align="center">
  <img width="800" alt="Screen Shot 2022-04-24 at 23 56 12" src="https://user-images.githubusercontent.com/49797284/165023336-eb80f276-d25c-42f5-a6d5-d1fea2df7aea.png">
</p>


# Accelearate out of the box.

HCL Accelerate is a tool that gathers information across the release lifecycle from other DevOps tools. By mapping the movement of tasks, it can provide managers important metrics such as lead time, cycle time, and bottle-necking across their team.

Accelerate supports multiple integrations: Jenkins, GitLab, GitHub, etc. This flexibility allows teams to customize their experience as they see fit. We understand that some of our clients are looking for an out of the box experience, this is why we have created this series of templates to help teams integrate accelerate the smoothest and fastest way possible.

In this tutorial we will focus on a **github only** integration.

## Why Value Stream Management?

Before we begin, lets have some motivation. Why is Value Stream Management important (VSM)? VSM is rooted in the concepts of mapping your organizational processes. This involves working with all major contributing business units (design, development, product management, release engineers, quality assurance, security, etc).


With all so many DevOps tools already in the market, we can leverage their information and help identify pain points, create greater visibility/traceability throughout the life cycle, or eliminate redundant and wasteful processes.

In laymen terms, we breakdown your product into units you can easily track in a linear way without having to log in to each devops tools.

# Installing Accelerate

## Prerequisites

## Docker
If you have not installed Docker into your machine you can follow this [docker installation guide](https://docs.docker.com/get-docker/). For the resource allocation we recommend:
* CPUs: 4
* Memory: 9 GB
* Swap: 4 GB
* Disk image size: > 100 GB

## Access key
Head to the HCL Accelerate [web portal]() to obtain your key.

## Installation file. 

Choose the appropriate installation depending on your OS.
* Linux: https://hcl-velocity-binaries.s3.amazonaws.com/accelerate-hcl-install-latest-linux
* Windows: https://hcl-velocity-binaries.s3.amazonaws.com/accelerate-hcl-install-latest-win.exe
* Mac OS: https://hcl-velocity-binaries.s3.amazonaws.com/accelerate-hcl-install-latest-macos

For linux and mac users rememeber to give the appropriate permissions before running the file.
If your default folder for downloads is Downloads you can follow the next commands.
```shell
cd
cd Downloads
chmod +x accelerate-hcl-install-{latest-version-number}
./accelerate-hcl-install-{latest-version-number};
```

This should lead you to the installation process were you will be asked to provide you access key.

After the installation is complete you will see the Accelerate application in the default folder you provided in the installation prompt.
From here hop on to the terminal once more and use docker compose to finish the set up.

```shell
cd path_where_you_installed_accelerate
ls //you should see a docker-compose.yml file
docker-compose up -d
```

From here you can access the Accelerate UI trhough the https://hostname:port where hsotanme and port are the values you set during the installation prompt.

# GitHub Set Up

For this tutorial you will need an active github repository and a personal token with a minimum of write priority. If you have trouble creating a personal token follow this [tutorial](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


Accelerate uses pattern matching to identify which issues are related to which pull request. Since different teams might have different standards, or none at all, I have suggested to use github issue templates to take care of this consistency. In this case we will be using prefix DOC and BUG to identify what kind of issue we are dealing with.

If you are not familiar with issue templates, you can clone this repository and uses the templates already defined under: [ISSUE_TEMPLATE](https://github.com/danielbarr3ra/AccelerateGitTutorial/tree/main/.github/ISSUE_TEMPLATE)

# Integration Set Up

Integrations give Accelerate access to your development tools. They are stored under: Setting -> Plugins.
<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 8 26 19" src="https://user-images.githubusercontent.com/49797284/165099448-fe26da9e-0151-436d-8a32-09db890d4e4f.png">
</p>

<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 8 27 18" src="https://user-images.githubusercontent.com/49797284/165099459-8c579cf0-bb79-4d4e-8598-c5026eee8623.png">
</p>
<p align="center">
 <img width="700" alt="Screen Shot 2022-04-25 at 8 27 57" src="https://user-images.githubusercontent.com/49797284/165099470-bba07045-d608-40ff-9868-d31e866b509d.png">
</p>

Each integration will have different parameters for github we have:

* Integration Name: This integration name will be used later on the linking rules, lets keep it consistent.
* API URL: The current API URL used by github is https://api.github.com
* Owner: when you copy the repository this will be your username.
* Personal access token: the token obtained during github setup.
* repositories: you can add multiple repositories, in this case its only one.
* branches: you can also observe multiple branches, in this case we are only observing main.

Here is a sample of what the integration set up will look like, if its different you might be on an older version of the release, you can update by clicking on the "check for upgrades button"


<p align="center">
  <img height="300" alt="Screen Shot 2022-04-24 at 23 58 24" src="https://user-images.githubusercontent.com/49797284/165023554-6c9c2813-daef-41b1-8c4b-16231dd0c52b.png"> <img height="300" alt="Screen Shot 2022-04-24 at 23 58 00" src="https://user-images.githubusercontent.com/49797284/165023559-de8cd373-a93d-4a88-9c3a-6c98ebbe555f.png">
</p>



# VSM Set Up

Creating a value stream in Accelerate is simple, in the main dashboard you can select "Create New Value Stream Management" and add the title, description and default team:


<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 8 42 14" src="https://user-images.githubusercontent.com/49797284/165101649-a983e4c3-bb5b-4926-b328-f2f82a3f20a0.png">
</p>
<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 8 42 43" src="https://user-images.githubusercontent.com/49797284/165101730-b46011e3-d9eb-4cc7-8839-303a147a1030.png">
</p>

This will bring up the default VSM look which we will modify in the following section.


## JSON

The vsm json file is the rule book for accelerate, in this file you assign all the different stages, linking rules, and integrations.
When edited correctly your VSM dashboard its updated and the right task will appear and be tracked throughout your process.

The JSON file has the following tree structure:
* VSM
  * phases
      * stages
  * leadTime
  * cyleTime
  * mappings
  * integrations
  * linkRules
  * metrics
  * metricsBar


## Phases and Stages

Each phase has the following structure:
```json
"phases": [
    {
      "name": "Name of the first phase",
      "description": "What does this phase accomplish, planning, development?",
      "stages": [
        {
          "name": "Name of the first phase on this stage",
          "query": "This query will pull information from integration",
          "description": "what are the tasks on this stage",
          "targets": [
            "Name of the following stage"
          ],
          "wipLimit": 3,   /*there is a limit of three work in progress items*/
          "gates": null
        },
        {
          "name": "Queue",
          "query": "",
          "description": "",
          "targets": [
            "In Progress"
          ],
          "wipLimit": null,
          "gates": null
        }
      ]
    },
```

## Integrations
After setting up the integration, you can include it ont your vsm file by simply adding the following under integration

```json
"integrations": [
   {
    "name":"name used on the integration"
   }
  ],
```

## Queries and Linking Rules.
As noted in the previous section, stages have a query pattern. This query pattern uses DQL fields to search and filter the different tasks from the data provided by your integration. You can find a full list of these queries [here](https://devops.hcldoc.com/accelerate/3.0.x/#com.uvelocity.doc/topics/dots_query/#devops-query-language-dql). An example of the queies used in our vsm are the following:


```json
        {
          "name": "Assigned",
          "query": "issue.owner != \"unknown\" and issue.status = \"Open\"  ",
          "description": "These issues have been assigned to a team member",
          "targets": [
            "In Progress"
          ],
          "wipLimit": null,
          "gates": null
       }
        ....
        {
          "name": "In Review",
          "query": "pr.status = open and pr.assignees.count != 0",
          "description": "These pull request have been submitted and are actively being looked at by other team members",
          "targets": [
            "Merged"
          ],
          "wipLimit": 5,
          "gates": null
        },
```
Since pull requests and issues are different items, we need to find a way to link them together and track their process. Accelerate achieves this with linking rules. To define a link rule, specify a field in the linked-from tool that you want to associate with a field in the linked-to tool, and a regular expression that defines the matching pattern. 

For github we have the following link rules:
```json
"linkRules": [
    {
      "fromIntegrationName": "SingleGitIntegration",
      "toIntegrationName": "SingleGitIntegration",
      "fromField": "pr.name",
      "toField": "issue.name",
      "pattern": "([A-Z]+-[0-9]+)"
    }
  ],
```
You might recall we previously set up issue templates to adhere to the pattern: "([A-Z]+-[0-9]+)"

## Uploading JSON
We understand setting up everything for the first time can be tedious, if you are on a rush you can upload the vsm file attached in this repo to you value stream. 

Edit Value Stream Map -> Import JSON -> select file to upload.
<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 9 52 03" src="https://user-images.githubusercontent.com/49797284/165115897-d5a09455-b203-41ad-9bbe-7acc13cd37d5.png">
</p>
<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 9 52 23" src="https://user-images.githubusercontent.com/49797284/165115865-ac9c5a83-e9b2-4c19-b62e-fb1be0588752.png">
</p>
<p align="center">
 <img width="278" alt="Screen Shot 2022-04-25 at 9 52 53" src="https://user-images.githubusercontent.com/49797284/165115997-d0d76a57-db5d-4ce8-a7be-001f2f1393a3.png">
</p>

after it has been submitted your Value Stream Map should look something like this.

<p align="center">
 <img width="700" alt="Screen Shot 2022-04-28 at 10 01 40" src="https://user-images.githubusercontent.com/49797284/165783128-3783fe2c-0886-42a4-88c9-f5233a6f8726.png">

</p>

# What to do next?

## Immplement another integration
Now that you have set up github a great idea will be to implement Jira into the planning stage of your pipeline, this way you can pull stories and link them to their repective pull request. The integration set up is similar. The only change will be in the linkrule, sine now the from.Integration will be Jira instead of githu. 

## Implement different streams
You 

Daniel Barrera | HCL Accelerate
