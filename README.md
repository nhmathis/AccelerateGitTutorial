# Table of Contents
1. [Accelerate](#accelearate-out-of-the-box)
2. [What is Value Stream Management](#why-value-stream-management)
3. [Git Hub](#github-set-up)
4. [Integration ](#integration-set-up)
5. [Reports](#reports)

<img width="1402" alt="Screen Shot 2022-04-24 at 23 56 12" src="https://user-images.githubusercontent.com/49797284/165023336-eb80f276-d25c-42f5-a6d5-d1fea2df7aea.png">

# Accelearate out of the box.

HCL Accelerate is DevOps tool that gathers information across the release lifecycle from different sources. By mapping the movement of tasks it can provide insight on important metrics such as lead time, cycle time, and bottlenecking across your team.

Accelerate suports multiple integrations: Jenkins, GitLab, GitHub, etc. This flexibility allows teams to customize their experience as they see fit. We understan that some of our clients are looking for an out of the box experience, this is why we have created this series of templates to help teams integrate accelerate the smothest and fastest way possible.

In this tutorial we will focus on a github only integration.

## Why Value Stream Management?

Before we begin, lets have some motivation. Why is Value Stream Management important (VSM)? VSM is rooted in the concepts of mapping your organizational processes. This involves working with all major contributing business units (design, development, product management, release engineers, quality assurance, security, etc).


With DevOps tools already in the market, we can levarage their information to give insights on the performance of our team, and lifecyle of our product.

In laymen terms, we breakdown your product into units you can easily track and understan without having to log in to each github, jira,or jenkins dashboard.


## GitHub set up

For this tutorial you will need an active github repository and a personal token with a minimum of write priority. If you have trouble creating a personal token follow this [tutorial](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).


Accelerate uses pattern matching to identify which issues are related to wich pull request. Since different teams might have different standards, or none at all, I have suggested to use github issue templates to take care of it. In this case we will be using prefix DOC and BUG to identify what kind of issue we are dealing with.

If you are not familiar with issue templates, you can clone this repository and uses the templates already defined under: [ISSUE_TEMPLATE](https://github.com/danielbarr3ra/AccelerateGitTutorial/tree/main/.github/ISSUE_TEMPLATE)

## Integration set up.

Integrations give Accelerate access to your development tools. They are stored under: Setting -> Plugins.

<images>
<images>
<images>

Each integration will have different patt


<img width="300" alt="Screen Shot 2022-04-24 at 23 58 24" src="https://user-images.githubusercontent.com/49797284/165023554-6c9c2813-daef-41b1-8c4b-16231dd0c52b.png"> <img width="300" alt="Screen Shot 2022-04-24 at 23 58 00" src="https://user-images.githubusercontent.com/49797284/165023559-de8cd373-a93d-4a88-9c3a-6c98ebbe555f.png">

Once you have your api key you can go to integrations an add the following information to github.

Integration Name: This integration name will be used later on the linking rules, lets keep it consistent.

API URL: The current API URL used by github is https://api.github.com

Owner: when you copy the repository this will be your username, the repositories you want to observe, and the branches should stay as is.

## Linking rules.
Accelerate uses linking rules to connect each tool. In this scenario for github we will used them to link the issues and pull requests. We only have one link rule in this tutorial, since we are connecting issues and pr within github.


## Reports.

## VSM JSON FILE

The vsm json file is the rule book for accelerate, in this file you assing all the different stages, linking rules, and integrations.
The format is the following: 

by Daniel Barrera | HCL Accelerate
