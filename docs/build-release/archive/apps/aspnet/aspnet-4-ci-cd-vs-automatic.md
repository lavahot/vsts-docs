---
title: Deploy a CI/CD pipeline ASP.NET web app to Azure
description: Use Visual Studio to automatically generate a CI/CD pipeline to deploy your ASP.NET web app to Azure in VSTS or Microsoft Team Foundation Server (TFS)
ms.prod: vs-devops-alm
ms.technology: vs-devops-build
ms.assetid: 498BF7D8-2932-46FB-BD38-E8EBD1C5CABA
ms.manager: douge
ms.author: alewis
ms.date: 02/10/2017
---

# Use Visual Studio to automatically generate a CI/CD pipeline to deploy your ASP.NET web app to Azure

[!INCLUDE [include](../../../_shared/version.md)]

In this walkthrough we'll show how to use Visual Studio to automatically define a continuous integration (CI) and continuous deployment (CD) process to deploy an ASP.NET web application project to [Azure](https://azure.microsoft.com/). 

[!INCLUDE [include](../../../apps/aspnet/_shared/ci-cd-description.md)]

> [!TIP]
> If you don't yet have an app but want to try this out, then see the [Q&A below](#new_solution).

[!INCLUDE [include](../../../apps/aspnet/_shared/setup.md)]

## Install the Continuous Delivery Tools extension

The quickest way to create a continuous delivery process is with the Continuous Delivery Tools for Visual Studio (2017 RC.3 and newer), which automate the creation of build and release definitions. The tools assume that you have an existing VSTS account, and that your project has been added to source control in a Team Project.

To install the extension within Visual Studio, select **Tools > Extensions and Updates...** and search for **Continuous Delivery Tools for Visual Studio**. Alternatively, you can download the installer from the [Visual Studio Gallery](http://aka.ms/CD4VS).

## Create the build and release definitions automatically

To create both the build (CI) and release (CD) definitions for a project, in Visual Studio, right-click the Solution node in Solution Explorer and select **Configure Continuous Delivery....** In the dialog that appears, choose the appropriate repository branch, Azure subscription, and target App Service, and click OK. You'll see details in the Output pane during the process.

[!INCLUDE [include](../../../apps/aspnet/_shared/commit-build-release.md)]

## Q&A

<!-- BEGINSECTION class="md-qanda" -->

<h3 id="new_solution">How do I create an ASP.NET 4 web app?</h3>

1. In Visual Studio, [connect to your team project](../../../../user-guide/connect-team-projects.md#visual-studio).

1. On the Team Explorer home page (Keyboard: Ctrl + 0, H), under **Solutions**, click **New**.

1. Select the **Web** category under **Visual C#**.

1. Select **ASP.NET Web Application** and click **OK**.

1. Select **MVC** from the template list.

1. Click **Change Authentication**, select **No Authentication**, and click **OK**.

1. Optionally, set **Add unit tests** to create a unit test project for the application. Unit tests can be run automatically with every build as part of a release pipeline.

1. Clear **Host in the cloud** and click **OK**.

1. [Commit and push (Git)](../../../../git/share-your-code-in-git-vs.md) or [check in (TFVC)](../../../../tfvc/share-your-code-in-tfvc-vs.md) your code.

### I got a file not found error message. How do I fix it?

All solution files must be checked into the server to run a build. One known cause of missing files is in cases where you populate an empty repo by creating a new project in Visual Studio 2015 Update 3. We recommend that you update your [.gitignore file](../../../../git/tutorial/ignore-files.md) with the latest copy from [GitHub: VisualStudio.gitignore](https://github.com/github/gitignore/blob/master/VisualStudio.gitignore).

[!INCLUDE [temp](../../../_shared/qa-versions.md)]

<!-- ENDSECTION -->

[!INCLUDE [rm-help-support-shared](../../../_shared/rm-help-support-shared.md)]
