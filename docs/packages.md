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

Microsoft builds and supports a variety of software products for Linux systems and makes them available via Linux packaging clients (apt, dnf, yum, etc) hosted on the Linux software repository for Microsoft products (https://packages.microsoft.com).

This guide outlines the configuration steps for downloading the Linux software repository for Microsoft products (https://packages.microsoft.com) to your Linux system, so that you can then install and upgrade Microsoft software that is built for Linux using your distribution's standard package management tools.

## How to install Microsoft software packages using the Linux Repository

The Linux Software Repository will be configured automatically by installing the Linux package that applies to your Linux distribution and version. Each Microsoft product may require a slightly different installation process. The package will install the repository configuration, along with the GPG public key used by tools such as apt, yum, or zypper to validate the signed packages and/or repository metadata.

> [!NOTE]
> Optionally, if you prefer manual configuration, the Linux Software Repository configuration files are available at [https://packages.microsoft.com/config](https://packages.microsoft.com/config). The name and location of these files can be located using the following URI naming convention:
`https://packages.microsoft.com/config/<Distribution>/<Version>/prod.(repo|list)`

### Examples of available Microsoft products in the Linux Repository

The following Microsoft products are a few examples that offer Linux versions supported for install using the Linux Repository (package.microsoft.com). See the associated documentation link for more specific installation steps.

- [.NET on Linux](/dotnet/core/install/linux)
- [PowerShell on Linux](/powershell/scripting/install/installing-powershell-on-linux)
- [Microsoft Defender for Endpoint on Linux](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-linux) ([Manual deployment guide](/microsoft-365/security/defender-endpoint/linux-install-manually))
- [SQL Server on Linux](/sql/linux/sql-server-linux-overview) ([Offline install guidance](/sql/linux/sql-server-linux-setup#offline))
- [Microsoft InTune for Linux](/mem/intune/user-help/microsoft-intune-app-linux)

> [!IMPORTANT]
> Packages in the Linux Software Repository are subject to the license terms located in each package. Please read the license terms prior to using the package. Your installation and use of the package constitutes your acceptance of these terms. If you do not agree with the license terms, do not use the package.

## How to use the GPG Repository Signing Key

Linux Software Repository for Microsoft Products uses the GPG (GNU Privacy Guard) tool to secure apt to sign files and check their signatures in order to authenticate downloaded packages.

- Microsoft's GPG public key may be downloaded here: [https://packages.microsoft.com/keys/microsoft.asc](https://packages.microsoft.com/keys/microsoft.asc)
- Public Key ID: Microsoft (Release signing) `gpgsecurity@microsoft.com`
- Public Key Fingerprint: `BC52 8686 B50D 79E3 39D3 721C EB3E 94AD BE12 29CF`

## Example of using the packages.microsoft.com service

- Install a repository configuration: `curl -sSL https://packages.microsoft.com/config/<distribution>/<version>/prod.list | sudo tee /etc/apt/sources.list.d/microsoft-prod.list` (replacing `<distribution>` and `<version>` with the name of the supported Linux distribution and version you wish to use). If you're unsure what distribution and version you are currently running, you can try entering `lsb_release -a` (for any distro that includes the “lsb-release" package) or `cat /etc/os-release` (for any distro that uses systemd).

- Download the Microsoft repository GPG public key: `curl -sSL https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc`

- Register the Microsoft repository GPG public key: `sudo dpkg -i packages-microsoft-prod.deb`

- Delete the the Microsoft repository GPG public keys file after registering: `rm packages-microsoft-prod.deb`

- Update package index files: `sudo <apt-get> update` (replacing `<apt-get>` with the appropriate command for the package manager used with your Linux distribution).

- To install the Microsoft product package you're after using this Linux repository (packages.microsoft.com): `sudo <apt-get> install <product-name>` (replacing `<apt-get>` with the appropriate command for the package manager used with your Linux distribution and `<product-name>` with the name of the Microsoft software that you want to install). 

See [packages.microsoft.com](https://packages.microsoft.com/) find the list of supported Linux distributions and versions.

## How to file an issue, request a feature, or report a security vulnerability

We want to ensure that our Linux customers are well-supported. The following communication channels are available to users of the PMC service:

- [Report an issue](https://github.com/microsoft/linux-package-repositories/issues/new?assignees=&labels=&template=report-an-issue.md&title=Report+an+issue): Help us improve the PMC service by reporting any issues you are experiencing.

- [Request a feature](https://github.com/microsoft/linux-package-repositories/issues/new?assignees=&labels=enhancement&template=request-a-feature.md): Request a new feature or enhancement to the PMC service.

- [Report a security vulnerability](https://github.com/microsoft/linux-package-repositories/security/policy): Help us to identify any potential security vulnerabilities by reviewing our security policy and reporting any issues.
