---
title: Linux resources at Microsoft
description: Microsoft offers resources to get you started using Linux, install tools that run on Linux, complete Linux-related training courses, learn about the Mariner Linux distribution supported by Microsoft, and find info about Microsoft Open Source news, events, and history.
author: mattwojo 
ms.author: mattwoj 
manager: jken
ms.topic: article
ms.technology: linux
ms.date: 03/28/2023
---

# Linux resources at Microsoft

Microsoft offers a variety of resources to support Linux users, including:

- [Get started with Linux](#get-started-with-linux)
- [Microsoft tools that run on Linux](#microsoft-tools-that-run-on-linux)
- [Linux-related training at Microsoft](#linux-related-training-at-microsoft)
- [Microsoft + Linux partnerships, open source news, events, and history](#microsoft--linux-news-events-and-partnerships)

![Photo of Satya Nadela ](./images/satya.png)

## Get started with Linux

Linux is an open source operating system with many different versions due to the nature of being open source and fully customizable. The different versions of Linux are called "distributions" (sometimes shortened to “distros”). There are several different ways to install and run a distribution of the Linux operating system, including:

- Windows Subsystem for Linux (WSL) if you want a simple install that is integrated with Windows.
- Create a Virtual Machine (VM) either locally with a hypervisor or in the cloud with a service like Azure.
- Bare-metal installation if you want to run Linux alone without any other operating system (or if you want to dual-boot, which we no longer recommend).

For step-by-step guidance on how to get started, see [How to download and install Linux](./install.md).

## Microsoft tools that run on Linux

Microsoft supports Linux with a variety of different tools and services. If you’re using Linux you may be interested in some of these resources.

:::row:::
    :::column:::
        [:::image type="icon" source="images/net.png":::](/dotnet/core/install/linux)

        [**Install .NET on Linux**](/dotnet/core/install/linux)<br>
        Learn how to how to install .NET on various Linux distributions either manually, via a package manager, or via a container. .NET is a free and open-source development platform with languages, editors, and libraries to build for web, mobile, desktop, games, and IoT.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/vscode.png":::](https://code.visualstudio.com/download)

        [**Install Visual Studio Code on Linux**](https://code.visualstudio.com/download)<br>
        VS Code is a lightweight source code editor with built-in support for JavaScript, TypeScript, Node.js, a rich ecosystem of extensions (C++, C#, Java, Python, PHP, Go) and runtimes (such as .NET and Unity). [Learn how to install it on Linux and keep it up to date via package managers.](https://code.visualstudio.com/docs/setup/linux) 
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/powershell.png":::](/powershell/scripting/install/installing-powershell-on-linux)

        [**Install PowerShell on Linux**](/powershell/scripting/install/installing-powershell-on-linux)<br>
        PowerShell is a cross-platform task automation solution made up of a command-line shell, a scripting language, and a configuration management program. Learn how to install PowerShell on Linux and find the currently supported Linux distributions and package managers.
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        [:::image type="icon" source="images/mariner.png":::](/dotnet/core/install/linux)

        [**CBL-Mariner**](https://github.com/microsoft/CBL-Mariner)<br>
        Mariner is an open-source Linux distribution created by Microsoft. Mariner is now available for preview as a boot-able Linux image that can be used as a container host on Azure Kubernetes Service (AKS). [Learn more about Mariner](/azure/aks/use-mariner).
    :::column-end:::
    :::column:::
              
    :::column-end:::
    :::column:::
        
    :::column-end:::
:::row-end:::

## Linux-related training at Microsoft

A variety of Linux-related training is available from Microsoft, including:

:::row:::
    :::column:::
        [:::image type="icon" source="images/training-linux-on-azure.png":::](/training/paths/azure-linux)

        [**Linux on Azure**](/training/paths/azure-linux)<br>
        A learning path with training modules to help you deploy and manage Linux on Azure, including cloud computing concepts, Linux IaaS and PaaS solutions, and Azure cloud services.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/training-linux-on-azure-intro.png":::](/training/modules/intro-to-azure-linux)

        [**Introduction to Linux on Azure**](/training/modules/intro-to-azure-linux)<br>
        A training module on the unique benefits of running Linux on Azure, and how to run Linux-based applications and workloads in the cloud with Azure.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/training-linux-on-azure-vm.png":::](/training/modules/create-linux-virtual-machine-in-azure/)

        [**Create a Linux virtual machine in Azure**](/training/modules/create-linux-virtual-machine-in-azure/)<br>
        A training module on how to create a Linux virtual machine using the Azure portal.
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        [:::image type="icon" source="images/training-wsl-get-started.png":::](/training/modules/wsl/wsl-introduction/)

        [**Get started with Windows Subsystem for Linux (WSL)**](/training/modules/wsl/wsl-introduction/)<br>
        A training module on how to install a Linux distribution, set up a dev environment, explore recommended tools and workflows, learn what WSL can and can’t do, try some basic commands, and assess whether WSL fits your needs.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/training-linux-on-azure-intro.png":::](/windows/wsl/tutorials/gui-apps)

        [**Run Linux GUI apps with WSL**](/windows/wsl/tutorials/gui-apps)<br>
        Windows Subsystem for Linux (WSL) now supports running Linux GUI applications (X11 and Wayland) on Windows in a fully integrated desktop experience.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/tutorial-wsl-docker.png":::](/windows/wsl/tutorials/wsl-containers)

        [**Get started with Docker remote containers on Linux with WSL**](/windows/wsl/tutorials/wsl-containers)<br>
        Docker Desktop for Windows provides a development environment for building, shipping, and running dockerized apps. By enabling the WSL 2 based engine, you can run both Linux and Windows containers in Docker Desktop on the same machine.
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        [:::image type="icon" source="images/cpp.png":::](/cpp/linux/)

        [**Create and debug applications for Linux using C++ in Visual Studio**](/cpp/linux/)<br>
        Use C++ in Visual Studio to create and debug applications for a Linux-based operating system. Learn how to [Download, install, and set up the Linux workload](/cpp/linux/download-install-and-setup-the-linux-development-workload), [Connect to your target Linux system](/cpp/linux/connect-to-your-remote-linux-computer), [Create, Configure, and Deploy a Linux project](/cpp/linux/create-a-new-linux-project), and more.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/nodejs.png":::](/windows/dev-environment/javascript/nodejs-on-wsl)

        [**Install Node.js on Linux with WSL**](/windows/dev-environment/javascript/nodejs-on-wsl)<br>
        Node.js is an open-source, cross-platform, server-side JavaScript runtime environment, often used for building fast, scalable web applications. Learn how to install Node.js on a Linux distribution using WSL, nvm, and npm.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/react-logo.png":::](/windows/dev-environment/javascript/react-on-wsl)

        [**Install React on Linux with WSL**](/windows/dev-environment/javascript/react-on-wsl)<br>
        React is an open-source JavaScript library for building front end user interfaces. Learn how to install React on a Linux distribution using WSL, npx, and create-react-app.
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        [:::image type="icon" source="images/python-logo.png":::](/windows/python/web-frameworks)

        [**Install Python on Linux with WSL**](/windows/python/web-frameworks)<br>
        Python is an interpreted, object-oriented, high-level programming language with dynamic semantics. It is open-source and a popular option for web development using Linux along with frameworks like Django and Flask. Learn how to install Python, Django, and Flask using WSL, pip, and venv.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/#g":::](/windows/dev-environment/javascript/vue-on-wsl)

        [**Install Vue.js on Linux with WSL**](/windows/dev-environment/javascript/vue-on-wsl)<br>
        Vue is an open-source, front end JavaScript framework for building user interfaces and single-page applications on the web. Learn how to install Vue.js, the Vue CLI, and the Node.js dependencies using WSL. 
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/docker-icon.png":::](/windows/wsl/tutorials/wsl-containers)

        [**Install Docker on Linux with WSL**](/windows/wsl/tutorials/wsl-containers)<br>
        Docker is an open platform for developing, shipping, and running applications, providing the ability to package and run an application in a loosely isolated environment called a container. Learn how to install Docker on Linux using WSL and Docker Desktop for Windows.
    :::column-end:::
:::row-end:::

## Microsoft + Linux news, events, and partnerships

Microsoft is one of the biggest contributors to open source projects in the world. Learn more about Microsoft + Linux partnerships, Open Source news, events, and history.

:::row:::
    :::column:::
        [:::image type="icon" source="images/microsoft-opensource.png":::](https://cloudblogs.microsoft.com/opensource/)

        [**Microsoft Open Source Blog**](https://cloudblogs.microsoft.com/opensource/)<br>
        Read about the latest news, events, project updates, and demos/tutorials related to Open Source at Microsoft.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/windows-commandlineblog.png":::](https://devblogs.microsoft.com/commandline/)

        [**Windows Command Line Blog**](https://devblogs.microsoft.com/commandline/)<br>
        Read the latest updates about Windows Subsystem for Linux, Windows Terminal, and Windows Package Manager.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/microsoft-canonical.png":::](https://ubuntu.com/blog/tag/microsoft)

        [**Ubuntu Blog: Microsoft**](https://ubuntu.com/blog/tag/microsoft)<br>
        Read the latest news related to the partnership between Canonical and Microsoft.
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        [:::image type="icon" source="images/microsoft-joins-linux.png":::](https://cloudblogs.microsoft.com/opensource/2016/11/17/microsoft-joins-linux-foundation/)

        [**Microsoft joins the Linux Foundation**](https://cloudblogs.microsoft.com/opensource/2016/11/17/microsoft-joins-linux-foundation/)<br>
        Original announcement about Microsoft joining the Linux Foundation from November 2016.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/microsoft-linux-consortium.png":::](https://cloudblogs.microsoft.com/opensource/2019/08/21/microsoft-partners-linux-foundation-announce-confidential-computing-consortium/)

        [**Microsoft joins partners and the Linux Foundation to create Confidential Computing Consortium**](https://cloudblogs.microsoft.com/opensource/2019/08/21/microsoft-partners-linux-foundation-announce-confidential-computing-consortium/)<br>
        Original announcement about Microsoft and Linux Foundation partnering to create the Confidential Computing Consortium, dedicated to defining and accelerating the adoption of confidential computing.
    :::column-end:::
    :::column:::
        [:::image type="icon" source="images/open3dfoundation.png":::](https://www.linuxfoundation.org/press/press-release/the-open-3d-foundation-welcomes-microsoft-as-a-premier-member-to-advance-the-future-of-open-source-3d-development)

        [**Open 3D Foundation Welcomes Microsoft**](https://www.linuxfoundation.org/press/press-release/the-open-3d-foundation-welcomes-microsoft-as-a-premier-member-to-advance-the-future-of-open-source-3d-development)<br>
        Original announcement about Microsoft joining over 25 organizations committed to democratizing 3D software development for games and simulations.
    :::column-end:::
:::row-end:::
