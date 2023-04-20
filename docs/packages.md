---
title: Linux Software Repository for Microsoft Products
description: Learn how to install Microsoft products on Linux using the packages.microsoft.com (PMC) service and how this service supports various package managers.
author: mattwojo 
ms.author: mattwoj 
manager: jken
ms.topic: article
ms.technology: linux-resources
ms.date: 04/20/2023
---

# Linux Software Repository for Microsoft Products

Microsoft products can be packaged for installation on Linux distributions using the [packages.microsoft.com](https://packages.microsoft.com) (PMC) service.

Products supported in the PMC service currently include:

- [.NET on Linux]()
- [Microsoft Defender for Endpoint on Linux]()
- [TBD]()
- [TBD]()
- [TBD]()

This document describes how to configure the repository on your Linux system, so that you can then install/upgrade Microsoft's Linux software using your distribution's standard package management tools.

> [!NOTE]
> Packages in the Linux software repositories are subject to the license terms located in the packages. Please read the license terms prior to using the package. Your installation and use of the package constitutes your acceptance of these terms. If you do not agree with the license terms, do not use the package.

## How to use PMC

Need some basic instructions and/or common scenarios for how someone may use PMC to install Microsoft products on their Linux system. This would cover a more basic, high-level view of how the service is used, what to expect, what distributions are supported, what to do if there is a product or distribution that you are using that isn't supported, as well as a statement about how detailed instructions for installing a Microsoft product on a Linux system may vary and to see the links above or the docs for that particular product.

## How to file an issue, request a feature, or report a security vulnerability

We want to ensure that our Linux customers are well-supported. The following communication channels are available to users of the PMC service:

- [Report an issue](https://github.com/microsoft/linux-package-repositories/issues/new?assignees=&labels=&template=report-an-issue.md&title=Report+an+issue): Help us improve the PMC service by reporting any issues you are experiencing.

- [Request a feature](https://github.com/microsoft/linux-package-repositories/issues/new?assignees=&labels=enhancement&template=request-a-feature.md): Request a new feature or enhancement to the PMC service.

- [Report a security vulnerability](https://github.com/microsoft/linux-package-repositories/security/policy): Help us to identify any potential security vulnerabilities by reviewing our security policy and reporting any issues.

## Production and MsSQL server repositories

- **prods** - Production repositories (e.g. Ubuntu, Fedora, RHEL, etc.) are designated for packages intended to be used in production. These packages are commercially supported by Microsoft under the terms of the applicable support agreement or program that you have with Microsoft. The prod repositories can be located via hierarchical folder structure (e.g. https://packages.microsoft.com/fedora/36/prod/).
- **mssql-server** -  These repositories contain packages for Microsoft SQL Server on Linux - See also: SQL Server on Linux.

TO-DO: I don't understand this section or why these two categories of separation in the repository exists or are important to call out. Is this still relevant? If so, can we offer more context?

## License terms

Packages in the Linux software repositories are subject to the license terms located in the packages. Please read the license terms prior to using the package. Your installation and use of the package constitutes your acceptance of these terms. If you do not agree with the license terms, do not use the package.

## Distribution-specific configuration guidance

Repositories can be configured automatically by installing the Linux package that applies to your Linux distribution and version. The package will install the repository configuration, along with the GPG public key used by tools such as apt, yum, or zypper to validate the signed packages and/or repository metadata.

Note that not all supported distributions are listed here. See the current supported package repositories at https://packages.microsoft.com/ and the instructions for manual configuration below.

TO-DO: This intro should be updated. It's currently a bit confusing... is the purpose of this section to share the distro-specific code for each of the distro package managers that is supported? I'm going to hold off on copy-pasting anything from https://learn.microsoft.com/windows-server/administration/linux-package-repository-for-microsoft-software until there is more clarity on the modern story and what's supported.

### Debian

Do we need to maintain the current version # or name of each supported distro and the code for adding PMC with the associated package manager? How many distros are supported?

## Manual configuration

The repository configuration files are available from packages.microsoft.com/config. The name and location of these files can be located using the following URI naming convention:

`https://packages.microsoft.com/config/<Distribution>/<Version>/prod.(repo|list)`

### Package and Repository Signing Key

- Microsoft's GPG public key may be downloaded here: https://packages.microsoft.com/keys/microsoft.asc
- Public Key ID: Microsoft (Release signing) gpgsecurity@microsoft.com
- Public Key Fingerprint: BC52 8686 B50D 79E3 39D3 721C EB3E 94AD BE12 29CF

TO-DO: Is this all still relevant? If so, would be helpful to have more context around what it means to manually configure and more of a step-by-step walkthrough.

