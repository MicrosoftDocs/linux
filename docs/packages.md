---
title: Linux Software Repository for Microsoft Products
description: Learn how to install Microsoft products on Linux using the packages.microsoft.com (PMC) service and how this service supports various package managers.
author: mattwojo 
ms.author: mattwoj 
manager: jken
ms.topic: article
ms.date: 08/07/2023
---

# Linux Software Repository for Microsoft Products

Microsoft builds and supports a variety of software products for Linux systems and makes them available via Linux packaging clients (apt, dnf, yum, etc). These Linux software packages are hosted on the "Linux software repository for Microsoft products": [https://packages.microsoft.com](https://packages.microsoft.com). You can file issues or pull requests on the affiliated GitHub repo: [Microsoft Linux Package Repositories](https://github.com/microsoft/linux-package-repositories).

This page offers guidance on how to download and install the "Linux software repository for Microsoft products" (https://packages.microsoft.com) to your Linux system, so you can then install and upgrade Microsoft software that is built for Linux using your distribution's standard package management tools.

## How to install Microsoft software packages using the Linux Repository

The Linux Software Repository can be configured to automatically install the Linux package that applies to your Linux distribution and version. Each Microsoft product may require a slightly different installation process. The package install includes the repository configuration, along with the GPG public key used to validate the signed packages and/or repository metadata.

> [!NOTE]
> Optionally, if you prefer manual configuration, the Linux Software Repository configuration files are available at [https://packages.microsoft.com/config](https://packages.microsoft.com/config). The name and location of these files can be located using the following URI naming convention:
`https://packages.microsoft.com/config/<Distribution>/<Version>/prod.(repo|list)`

### Examples of available Microsoft products in the Linux Repository

The following Microsoft products are a few examples that offer Linux versions supported for install using the Linux Repository (package.microsoft.com). See the associated documentation link for more specific installation steps.

- [.NET on Linux](/dotnet/core/install/linux)
- [PowerShell on Linux](/powershell/scripting/install/installing-powershell-on-linux)
- [Microsoft Defender for Endpoint on Linux](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-linux): ([Manual deployment guide](/microsoft-365/security/defender-endpoint/linux-install-manually))
- [SQL Server on Linux](/sql/linux/sql-server-linux-overview): ([Offline install guidance](/sql/linux/sql-server-linux-setup#offline))
- [Microsoft InTune for Linux](/mem/intune/user-help/microsoft-intune-app-linux)

> [!IMPORTANT]
> Packages in the Linux Software Repository are subject to the license terms located in each package. Please read the license terms prior to using the package. Your installation and use of the package constitutes your acceptance of these terms. If you do not agree with the license terms, do not use the package.

## How to use the GPG Repository Signing Key

Linux Software Repository for Microsoft Products uses the GPG (GNU Privacy Guard) enabling users to verify the authenticity of files and to check the signatures of downloaded packages.

- Microsoft's GPG public key may be downloaded here: [https://packages.microsoft.com/keys/microsoft.asc](https://packages.microsoft.com/keys/microsoft.asc)
- Public Key ID: Microsoft (Release signing) `gpgsecurity@microsoft.com`
- Public Key Fingerprint: `BC52 8686 B50D 79E3 39D3 721C EB3E 94AD BE12 29CF`

## Command examples for using the Linux repository service

The following commands will configure your Linux OS to install packages from packages.microsoft.com. There are instructions for deb-based systems (e.g. Debian, Ubuntu) and rpm-based systems (e.g. Fedora, RHEL).

If you're unsure what distribution and version you are currently running, you can try entering `lsb_release -a` (for any distro that includes the “lsb-release" package) or `cat /etc/os-release` (for any distro that uses systemd).

### Debian-based Linux distributions

- Download the repo config package: `curl -sSL -O https://packages.microsoft.com/config/<distribution>/<version>/packages-microsoft-prod.deb`

- Install the repo config package: `sudo dpkg -i packages-microsoft-prod.deb`

- Delete the repo config package after installing: `rm packages-microsoft-prod.deb`

- Update package index files: `sudo apt-get update`

- To install the Microsoft product package you're after using this Linux repository (packages.microsoft.com): `sudo apt-get install <package-name>`

### Red Hat-based Linux distributions

The Red Hat Package Manager (rpm) instructions assume that the package client command is `dnf` but some rpm-based Linux distributions might be using other package managers, such as `tdnf`.

- Download the repo config package: `curl -sSL -O https://packages.microsoft.com/config/<distribution>/<version>/packages-microsoft-prod.rpm`

- Install the repo config package: `sudo rpm -i packages-microsoft-prod.rpm`

- Delete the repo config package after installing: `rm packages-microsoft-prod.rpm`

- Update package index files: `sudo dnf update`

- To install the Microsoft product package you're after using this Linux repository (packages.microsoft.com): `sudo dnf install <package-name>`

See [packages.microsoft.com](https://packages.microsoft.com/) find the list of supported Linux distributions and versions.

## How to file an issue, request a feature, or report a security vulnerability

We want to ensure that our Linux customers are well-supported. The following communication channels are available to users of the PMC service:

- [Report an issue](https://github.com/microsoft/linux-package-repositories/issues/new?assignees=&labels=&template=report-an-issue.md&title=Report+an+issue): Help us improve the PMC service by reporting any issues you are experiencing.

- [Request a feature](https://github.com/microsoft/linux-package-repositories/issues/new?assignees=&labels=enhancement&template=request-a-feature.md): Request a new feature or enhancement to the PMC service.

- [Report a security vulnerability](https://github.com/microsoft/linux-package-repositories/security/policy): Help us to identify any potential security vulnerabilities by reviewing our security policy and reporting any issues.
