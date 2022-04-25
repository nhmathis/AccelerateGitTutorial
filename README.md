# Table of Contents
1. [Accelerate](#accelearate-out-of-the-box)
2. [What is Value Stream Management](#why-value-stream-management)
3. [Git Hub](#github-set-up)
4. [Integration ](#integration-set-up)
5. [Reports](#reports)


# Accelearate out of the box.

HCL Accelerate is DevOps tool that gathers information across the release lifecycle frome different sources. By mapping the movement of tasks it can provide insight on important metrics such as lead time, cycle time, and bottlenecking across your team.

Accelerate suports multiple integrations: Jenkins, GitLab, GitHub, etc. This flexibility allows teams to customize their experience as they see fit. In {urbancode/velicity/accelerate} we understan that some of our clients are looking for an out of the box experience, this is why we have created this series of templates to help teams integrate accelerate the smothest way possible.

In this tutorial we will focus on a github only integration.

## Why Value Stream Management?

Before we begin, lets have some motivation. Why is Value Stream Management important (VSM). VSM is rooted in the concepts of mapping your organizational processes. This involves working with all major contributing business units (design, development, product management, release engineers, quality assurance, security, etc).

Thanks to the plethora of DevOps tools already in the market, we can levarage their information to give insights on the performance of our team, and lifecyle of our product.

In laymen terms, we take breakdown your product into units you can easily track and understan without having to log in to each github/jira/jenkins dashboard.


## GitHub set up

For this tutorial you will need an active github repository and a personal token with a minimum of write priority. If you have trouble creating a personal token follow this [tutorial](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

Accelerate uses pattern matching to identify which issues are related to wich prs. Since different teams might have different standards, or none at all, I have suggested to use github issue templates to take care of it. In this case we will be using prefix DOC and BUG to identify what kind of issue we are dealing with.

## Integration set up.

Once you have your api key you can go to integrations an add the following information to github.

Integration Name: This integration name will be used later on the linking rules, lets keep it consistent.

API URL: The current API URL used by github is https://api.github.com

Owner: when you copy the repository this will be your username, the repositories you want to observe, and the branches should stay as is.

## Linking rules.
Accelerate uses linking rules to connect each tool. In this scenario for github we will used them to link the issues and pull requests. We only have one link rule in this tutorial, since we are connecting issues and pr within github.


## Reports.


by Daniel Barrera | HCL Accelerate
