---
title: Postman Installation
description: Install Postman and get familiar with its collections, environments, and workspace interface before making API calls in later labs.
doc-type: article
solution: Experience Platform
exl-id: c277edb5-f758-4955-bcd7-b15a9b9ab949
---

# Objective

By the end of this lab, you will be able to install Postman, configure a basic workspace and environment so that you can make subsequent api calls needed by future labs.

>[!WARNING]
>
>Postman is required for various labs in this course.  Even if you have already installed Postman, you will need to complete this lab to ensure that you have the Environment Files and API Collection installed and properly set up.



## Install Postman

Navigate to the Postman website and either download the Postman app or utilize the Web Version --> [https://www.postman.com/download/](https://www.postman.com/download/)

![Postman download](assets/postman-download.png)

## Create a Postman Workspace (Optional)

If you are *new to Postman* and this is your first installation, then you don't need to create a new workspace. On first launch, choose to continue without signing in, and you'll be using the lightweight client that doens't require a workspace.

If you are *already familiar with Postma*n and have it installed, then you likely were already signed in and have several workspaces. If this is the case, we'd recommend you create a new workspace for this bootca*mp*. Instructions can be found on the [Postman Website.](https://learning.postman.com/docs/collaborating-in-postman/using-workspaces/create-workspaces/)

## Postman Interface

Open Postman and quickly familiarize yourself with a few areas of the application. For the purposes of working with Experience Platform, we really only need to focus on a few key areas of the application.

![YgYaHPl2 rf7z54bXfsj image.png "Postman Interface"](assets/_ygYaHPl2_rf7z54bXfsj_image.png "Postman Interface")

## Sidebar

The sidebar is what allows you to navigate quickly across the different Postman elements. During the labs, you will only use the two items below:

**Collections **- groups of saved requests that can be imported from an external location or created by yourself.

**Environments **- a set of variables that you can reference in your Postman requests. In Experience Platform, you can think of Postman Environments as synonymous with Adobe Sandboxes within an IMS Org. We will use the Environment's function in Postman



## Header

Workspaces - enable you to organize your work into various groupings (i.e. projects, teams, etc.)



## Main work area

The main work area is where you will perform the majority of your work when working in Postman. All API requests are exposed in a specific tab within the main work area.

**Right sidebar** - provides additional access to tools based on the current tab selected. Examples are documentation for the request, comments, and code snippets, to name a few features.

**Environment selector** - allows you to quickly switch between different environments to access pre-configured variables when working with APIs. When working with Experience Platform, you will leverage this when working with a specific AEP Sandbox within your assigned IMS org.



### Footer

At the very bottom of the Postman application, you will find a set of functions that allow you to quickly see the logs for the calls you made, quick access to find and replace, and various other functions.



## Recap

You should now have Postman installed and understand some basics of the UI
