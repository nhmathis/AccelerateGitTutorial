# Table of Contents
1. [HCL Accelerate](#hcl-accelerate)
2. [What is Value Stream Management](#why-value-stream-management)
3. [Install HCL Accelerate](#install-hcl-accelerate)
4. [GitHub Integration Set Up](#github-integration-set-up)
5. [Value Stream Construction](#value-stream-construction)
6. [Future Improvements](#what-to-do-next)



<p align="center">
  <img width="800" alt="Screen Shot 2022-04-24 at 23 56 12" src="https://user-images.githubusercontent.com/49797284/165023336-eb80f276-d25c-42f5-a6d5-d1fea2df7aea.png">
</p>


# HCL Accelerate

HCL Accelerate is a DevOps-focused product that gathers information from various SDLC sources and beyond to draw clear relationships, highlight hidden bottlenecks, and drive customer value. For example, by mapping the movement of tasks it can provide insight on important metrics, such as lead time, cycle time, and bottlenecking, across your team and help drive flow.

HCL Accelerate supports multiple integrations: Jenkins, GitLab, GitHub, HCL Launch, etc. This flexibility allows teams to customize their experience as they see fit. We understand that some of our clients are looking for an out of the box experience, which is why we have created this series of templates to help teams integrate HCL Accelerate the smoothest and fastest way possible.

In this tutorial, we will focus on the [GitHub integration](https://plugins.hcltechsw.com/github/).

## Why Value Stream Management?

Before we begin, lets have some motivation. Why is Value Stream Management (VSM) important? VSM is rooted in the optimization of cleanly and quickly producing stakeholder value. Most often, this begins with the mapping of your end-to-end pre-, mid-, and post-development. processes. All major contributing business units are included, such as design, development, product management, release engineers, quality assurance, security, etc.

With the plethora  of DevOps tools likely implemented in your product's SDLC, we can quickly leverage their information to give insights on the performance of our team and lifecycle of our product.

In laymen terms, we breakdown your product's silos and construct a single-pane-of-glass solution to help drive increased customer value.

# Installing Accelerate

Full directions can be found on our [installation documentation](https://devops.hcldoc.com/accelerate/3.0.x/#com.uvelocity.doc/topics/c_install_se_roadmap/). We recommend the Docker Compose installation path for PoCs and this tutorial. The shorthand directions are below.


## Docker Desktop
If you have not installed Docker into your machine, you can follow this [Docker Desktop installation guide](https://docs.docker.com/desktop/). 

## PoC System Requirements
For resource allocation, we recommend:
* CPUs: 4
* Memory: 12 GBs
* Available storage for download, images, and database: 20 GB

## Access key
Head to the HCL Accelerate [web portal](https://hclsw.co/getaccelerate) and complete the form to obtain your key.

## Installation file 

Choose the appropriate installation depending on your OS.
* Linux: https://hcl-velocity-binaries.s3.amazonaws.com/accelerate-hcl-install-latest-linux
* Windows: https://hcl-velocity-binaries.s3.amazonaws.com/accelerate-hcl-install-latest-win.exe
* Mac OS: https://hcl-velocity-binaries.s3.amazonaws.com/accelerate-hcl-install-latest-macos

For Linux and Mac users remember to give the appropriate permissions before running the file.
If your default folder for downloads is Downloads you can follow the next commands.
```shell
cd
cd Downloads
chmod +x accelerate-hcl-install-latest-<OS>
./accelerate-hcl-install-latest-<OS>
```

This should lead you to the installation process were you will be asked to provide you access key.

After the installation is complete you will see the HCL Accelerate application in the default folder you provided in the installation prompt.
From here hop on to the terminal once more and use Docker compose to finish the set up.

```shell
cd path_where_you_installed_accelerate
ls //you should see a docker-compose.yml file
docker-compose up -d
```

From here, you can access the HCL Accelerate UI through the https://hostname:port where hostname and port are the values you set during the installation prompt.

# GitHub Integration Set Up
## GitHub
For this tutorial you will need to clone [this GitHub repository](https://github.com/danielbarr3ra/AccelerateGitTutorial) and a personal token with a minimum of `repo` priorities. If you have trouble creating a personal token follow this [tutorial](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

HCL Accelerate uses pattern matching to identify which issues are related to which pull request. Since different teams might have different standards, or none at all, I have suggested to use GitHub issue templates to take care of it. In this case we will be using prefix DOC and BUG to identify what kind of issue we are dealing with.


If you are not familiar with issue templates, you can clone this repository and uses the templates already defined under: [ISSUE_TEMPLATE](https://github.com/danielbarr3ra/AccelerateGitTutorial/tree/main/.github/ISSUE_TEMPLATE)



## Integration
Integrations give HCL Accelerate access to a variety of tools. They are stored within the product under: Settings -> Integrations -> Plugins. 

<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 8 26 19" src="https://user-images.githubusercontent.com/49797284/165099448-fe26da9e-0151-436d-8a32-09db890d4e4f.png">
</p>

<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 8 27 18" src="https://user-images.githubusercontent.com/49797284/165099459-8c579cf0-bb79-4d4e-8598-c5026eee8623.png">
</p>
<p align="center">
 <img width="700" alt="Screen Shot 2022-04-25 at 8 27 57" src="https://user-images.githubusercontent.com/49797284/165099470-bba07045-d608-40ff-9868-d31e866b509d.png">
</p>

Each integration requires different input fields. For example, the GitHub integration contains:

* Integration Name: This integration name will be used later on the linking rules, lets keep it consistent.
* API URL: The current API URL used by GitHub is https://api.github.com
* Owner: When you copy the repository, this will be your username.
* Personal access token: The token obtained during GitHub setup.
* Repositories: You can add multiple repositories. In this case, its only one.
* Branches: You can also observe multiple branches. In this case, we are only observing main.

Here is a sample of what the integration set up will look like. If it's different you might be on an older version of the plugin release.  You can update by clicking on the "Upgrade" after integration configuration.


<p align="center">
  <img height="300" alt="Screen Shot 2022-04-24 at 23 58 24" src="https://user-images.githubusercontent.com/49797284/165023554-6c9c2813-daef-41b1-8c4b-16231dd0c52b.png"> <img height="300" alt="Screen Shot 2022-04-24 at 23 58 00" src="https://user-images.githubusercontent.com/49797284/165023559-de8cd373-a93d-4a88-9c3a-6c98ebbe555f.png">
</p>

If you are interested in every available plugin, [visit our plugins website.](https://plugins.hcltechsw.com)

# Value Stream Construction

Creating a value stream in HCL Accelerate is simple. In the main dashboard, you can select "Create value stream" and add the title, description, and team:

<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 8 42 14" src="https://user-images.githubusercontent.com/49797284/165101649-a983e4c3-bb5b-4926-b328-f2f82a3f20a0.png">
</p>
<p align="center">
  <img width="700" alt="Screen Shot 2022-04-25 at 8 42 43" src="https://user-images.githubusercontent.com/49797284/165101730-b46011e3-d9eb-4cc7-8839-303a147a1030.png">
</p>

This will bring up the default value stream look which we will modify in the following section.


## JSON

The vsm json file is the rule book for HCL Accelerate. In this file, you assigning all the different stages, linking rules, and integrations.
When configured correctly, your VSM view is automatically synced, tasks will appear, and changes will be tracked throughout your defined flow.

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

After setting up the integration, you can include it on your vsm file by simply adding the following under integration:


```json
"integrations": [
   {
    "name":"name used on the integration"
   }
  ],
```

## Queries and Linking Rules.

As noted in the previous section, stages have a query parameter. This query parameter uses DQL fields to search and filter the different tasks from the data provided by your integration. You can find a full list of these queries [here](https://devops.hcldoc.com/accelerate/3.0.x/#com.uvelocity.doc/topics/dots_query/#devops-query-language-dql). An example of the queries used in our vsm json are the following:


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

Since pull requests and issues are different items, we need to find a way to link them together and track their process. HCL Accelerate achieves this with link rules. To define a link rule, specify two integrations, the two fields that will be monitored, and a regular expression that monitored for.

For GitHub, we have the following link rule:
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
In this scenario, the link rule will look at the data that the `SingleGitIntegration` integration provides, analyze the `pr.name` for a value that matches `([A-Z]+-[0-9]+)`, and then _link it_ to the `issue.name` field. You might recall we previously set up issue templates to adhere to the pattern: "([A-Z]+-[0-9]+)"

## Uploading JSON
We understand setting up everything for the first time can be tideous. If you are on a rush you can upload the [vsm file in this repository](https://github.com/nhmathis/AccelerateGitTutorial/blob/main/GitTutorial-vsm.json) to you value stream. 


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

A successful value stream should look something like this!

<p align="center">
 <img width="700" alt="Screen Shot 2022-04-28 at 10 01 40" src="https://user-images.githubusercontent.com/49797284/165783128-3783fe2c-0886-42a4-88c9-f5233a6f8726.png">

</p>

# What to do next?

## Implement another integration
Now that you have set up GitHub, a great idea will be to implement Jira into the planning stage of your value stream. You can pull stories and link them to their repective pull request. The integration set up is similar. The only change will be in the link rule, since now the "from.Integration" will be Jira instead of github.



Add the new integration:
```json
"integrations": [
   {
    "name":"SingleGitIntegration"
   },
   {
   "name": "JiraIntegration"
   }
  ],
```

The queries are similar
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
```

The link rule needs to specify a different fromIntegration value.

```json
"linkRules": [
    {
      "fromIntegrationName": "JiraIntegration",
      "toIntegrationName": "SingleGitIntegration",
      "toField": "pr.name",
      "fromField": "issue.name",
      "pattern": "([A-Z]+-[0-9]+)"
    }
  ],
```


Daniel Barrera | HCL Accelerate
