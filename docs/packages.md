---
title: Linux Software Repository for Microsoft Products
description: Learn how to install Microsoft products on Linux using the packages.microsoft.com (PMC) service and how this service supports various package managers.
author: mattwojo 
ms.author: mattwoj 
manager: jken
ms.topic: article
ms.date: 10/01/2025
---

# Linux Software Repository for Microsoft Products

Linux versions of many Microsoft software products are supported and hosted on the "Linux software repository for Microsoft products": [https://packages.microsoft.com](https://packages.microsoft.com).

Packages.microsoft.com is a public repository meant to be consumed programmatically by Linux packaging clients, including apt (for Linux distributions like Ubuntu or Debian) dnf / yum (for RPM-based distributions like RedHat Enterprise, Fedora, CentOS, or Oracle Enterprise), or zypper (for SUSE Linux). In addition to the Linux packaging client directories, it includes related config files and keys.

You can learn more about the PMC service (packages.microsoft.com), file issues or pull requests, or report a security vulnerability on the affiliated GitHub repo: [Microsoft Linux Package Repositories](https://github.com/microsoft/linux-package-repositories).

## How to install Microsoft software packages using the Linux Repository

The Linux Software Repository can be configured to automatically install the Linux package that applies to your Linux distribution and version. Each Microsoft product may require a slightly different installation process. The package install includes the repository configuration, along with the GPG public key used to validate the signed packages and/or repository metadata.

> [!NOTE]
> Optionally, if you prefer manual configuration, the Linux Software Repository configuration files are available at [https://packages.microsoft.com/config](https://packages.microsoft.com/config/). The name and location of these files can be located using the following URI naming convention:
`https://packages.microsoft.com/config/<Distribution>/<Version>/prod.(repo|list)`

### Directory structure

At the root of packages.microsoft.com, you’ll see folders like:

- `/config/<distro>/<version>/prod.list`: Contains repo configuration files for each supported distribution.
- `/repos/`: Contains product-specific repositories (for example, edge, azure-cli, microsoft-prod).
- `/ubuntu/`: Contains distribution-specific repos for Microsoft packages that integrate with Ubuntu’s APT system.

A few things to keep in mind regarding the packages.microsoft.com repo structure:

- The packages.microsoft.com repository is public and designed for programmatic consumption by package managers, not for manual browsing, though directory listing is enabled for convenience.
- The repos tree is product-centric, not distribution-centric. For example: `repos/edge/`, `repos/azure-cli/`, repos/microsoft-prod/', etc. Each contains metadata for multiple distributions, so the same product repo can serve Ubuntu, Debian, etc.
- This differs from Ubuntu’s pool/main structure, which is strictly tied to Debian policy and archive layout.Ubuntu’s main pool is controlled by Canonical and only includes open-source or vetted packages, so proprietary software, such as Microsoft Edge, cannot be included there. This separation ensures Microsoft is able to directly provide updates and signing keys, as well as compliance with licensing (Microsoft Edge is closed-source). It also enables faster delivery of new versions without waiting for Ubuntu’s release cycle.
- Microsoft uses a centralized model rather than duplicating packages under each `distro` folder. This avoids redundancy and simplifies publishing across multiple Linux distributions.
- When you install the Microsoft repo config (packages-microsoft-prod.deb), it adds the correct deb `[arch=amd64] https://packages.microsoft.com/repos/edge` stable main line for your Linux distribution. APT then uses Microsoft’s metadata (Release, Packages.gz) to resolve dependencies. The actual `.deb` files live under `repos/edge/pool/main/...`, but you should never hardcode those paths because the APT package manager handles it.

### Examples of available Microsoft products in the Linux Repository

The following Microsoft products are a few examples that offer Linux versions supported for install using the Linux Repository (package.microsoft.com). See the associated documentation link for more specific installation steps.

- [.NET on Linux](/dotnet/core/install/linux)
- [PowerShell on Linux](/powershell/scripting/install/installing-powershell-on-linux)
- [Microsoft Defender for Endpoint on Linux](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-linux): ([Manual deployment guide](/microsoft-365/security/defender-endpoint/linux-install-manually))
- [SQL Server on Linux](/sql/linux/sql-server-linux-overview): ([Offline install guidance](/sql/linux/sql-server-linux-setup#offline))
- [Microsoft Intune for Linux](/mem/intune/user-help/microsoft-intune-app-linux)

> [!IMPORTANT]
> Packages in the Linux Software Repository are subject to the license terms located in each package. Please read the license terms prior to using the package. Your installation and use of the package constitutes your acceptance of these terms. If you do not agree with the license terms, do not use the package.

### Network Policy and DNS Considerations

The majority of Linux Software Repository users will be able to access [https://packages.microsoft.com](https://packages.microsoft.com) without issue. However, if your scenario requires SQL packages, and if you work in an environment using network policy to restrict access to certain domains, you will also need to enable access to `https://pmc-geofence.trafficmanager.net`.

SQL is a paid product, so to comply with regional tax laws, a geofence was enabled specifically for these packages. When your package client tries to download a SQL package, for example `mssql-server-ha.deb`, packages.microsoft.com will redirect your client to `https://pmc-geofence.trafficmanager.net` to fulfill the request. This secondary domain ensures the packages are delivered to you from a server within your geographic area.

## How to use the GPG Repository Signing Key

Linux Software Repository for Microsoft Products uses the GPG (GNU Privacy Guard) enabling users to verify the authenticity of files and to check the signatures of downloaded packages.

- Microsoft's GPG public key may be downloaded here: [https://packages.microsoft.com/keys/microsoft.asc](https://packages.microsoft.com/keys/microsoft.asc)
- Public Key ID: Microsoft (Release signing) `gpgsecurity@microsoft.com`
- Public Key Fingerprint: `BC52 8686 B50D 79E3 39D3 721C EB3E 94AD BE12 29CF`

## Snapshot support [Preview]

Preview support for [repository snapshots](https://packages.microsoft.com/snapshot) is now available on PMC (packages.microsoft.com). With PMC Snapshots, you can explore historical versions of specific Ubuntu repositories. The snapshot feature allows users to view and install packages as they existed at specific points in time, enabling reproducible deployments and helping to identify changes in package behavior over time. By using snapshots, you can recreate environments from any given date and time, which is particularly useful for tracking down when changes or regressions were introduced. Snapshots ensure that a validated environment can be consistently replicated across different stages of development and production, supporting a structured update workflow. This feature is similar to [snapshot.debian.org](https://snapshot.debian.org/) and [snapshot.ubuntu.com](https://snapshot.ubuntu.com/).

### How to create snapshots

Snapshots are created automatically when a repository is updated, provided the previous snapshot is at least 7 days old. Repository administrators can also manually create snapshots as needed. 

Index of Packages.microsoft.com snapshots:[https://packages.microsoft.com/snapshot/](https://packages.microsoft.com/snapshot/).

To access repository snapshots, go to the repository's snapshot path (like `https://packages.microsoft.com/snapshot/ubuntu/24.04/prod/`). Snapshots are identified by a UTC timestamp in their URL, representing the time it was created, such as `https://packages.microsoft.com/snapshot/ubuntu/24.04/prod/20250501T193230Z/` for the 2025-05-01T19:32:30Z UTC state. Snapshots can be accessed using an arbitrary timestamp. When requesting a snapshot with a specific timestamp, if an exact match isn't found, you'll be redirected to the latest snapshot created before that time. Requesting a future or pre-first-snapshot timestamp will return a 404 error.

This feature is **currently in preview and is not recommended for production workloads**. Currently, there is no ETA for moving beyond preview status or for expanding support to additional repositories. For more information, check [Pulp's checkpoint documentation](https://pulpproject.org/pulpcore/docs/user/guides/checkpoint/) which is the basis of the snapshot support in PMC.

As of May 2025, a new key has been introduced. This is primarily to support RHEL 10 and similar releases, which have strict requirements around signing keys. This change in policy does not indicate a lack of trust in the existing key, which will continue to be used for existing repositories.

- The new public key may be downloaded here: [https://packages.microsoft.com/keys/microsoft-2025.asc](https://packages.microsoft.com/keys/microsoft-2025.asc)
- Public Key ID: Microsoft (Release signing) `Microsoft Corporation - General GPG Signer <gpgsign@microsoft.com>`
- Public Key Fingerprint: `AA86 F75E 427A 19DD 3334 6403 EE4D 7792 F748 182B`

## Command examples for using the Linux repository service

The following commands will configure your Linux OS to install packages from packages.microsoft.com. There are instructions for deb-based systems (e.g. Debian, Ubuntu) and rpm-based systems (e.g. Fedora, RHEL).

If you're unsure what distribution and version you are currently running, you can try entering `lsb_release -a` (for any distro that includes the “lsb-release" package) or `cat /etc/os-release` (for any distro that uses systemd).

### Debian-based Linux distributions

- Download the repo config package:
> [!IMPORTANT]
>Make sure to replace the distribution and version with the appropriate strings.
````bash
curl -sSL -O https://packages.microsoft.com/config/<distribution>/<version>/packages-microsoft-prod.deb
````
- Install the repo config package:
````bash
sudo dpkg -i packages-microsoft-prod.deb
````
- Delete the repo config package after installing:
````bash
rm packages-microsoft-prod.deb
````
- Update package index files:
````bash
sudo apt-get update
````
- To install the Microsoft product package you're after using this Linux repository (packages.microsoft.com): `sudo apt-get install <package-name>`

See [packages.microsoft.com](https://packages.microsoft.com/) to find the list of supported Linux distributions and versions. 

In this example, entering `cat /etc/os-release` shows that Ubuntu, version 20.04, is running. Visiting [packages.microsoft.com](https://packages.microsoft.com/), we can see Ubuntu 20.04 on the list. To download the packages.microsoft.com repo, cURL is used to download with the command:
````bash
curl -sSL -O https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb
````
The repo config package is then installed with the command:
````bash
sudo dpkg -i packages-microsoft-prod.deb
````
And then deleted as not to take up space.

The list of packages is then updated with the apt package manager using the command:
````bash
sudo apt-get update
````

To search what Microsoft packages are available after installing, change to the root directory of your Linux distribution: `cd /` and look in the directory: `/var/lib/apt/lists`. You will see a list of files with titles something like: `packages.microsoft.com_ubuntu_20.04_prod_dists_focal_main_binary-all_Packages`. You can open this file in a text editor (for example, `nano <file-name>`) to see a list of the available packages.

### Red Hat-based Linux distributions

The Red Hat Package Manager (rpm) instructions assume that the package management client command is `dnf` but some rpm-based Linux distributions might be using other package managers, such as `yum` or `tdnf`.

- Download the repo config package:
> [!IMPORTANT]
>Make sure to replace the distribution and version with the appropriate strings.
````bash
curl -sSL -O https://packages.microsoft.com/config/<distribution>/<version>/packages-microsoft-prod.rpm
````
- Install the repo config package:
````bash
sudo rpm -i packages-microsoft-prod.rpm
````
- Delete the repo config package after installing:
````bash
rm packages-microsoft-prod.rpm
````
- Update package index files:
````bash
sudo dnf update
````
- To install the Microsoft product package you're after using this Linux repository (packages.microsoft.com):
````bash
sudo dnf install <package-name>
````
As an example of a pckage client that uses `yum`, the steps may be slightly different.

- Download the repo config package:
> [!IMPORTANT]
>Make sure to replace the distribution and version with the appropriate strings.
````bash
curl -sSL -O https://packages.microsoft.com/config/<distribution>/<version>/packages-microsoft-prod.rpm
````
- Install the repo config package:
````bash
sudo rpm -i packages-microsoft-prod.rpm
````
- Update package index files:
````bash
sudo yum update
````
- To install the Microsoft product package you're after using this Linux repository (packages.microsoft.com):
````bash
sudo yum install <package-name>
````
See [packages.microsoft.com](https://packages.microsoft.com/) to find the list of supported Linux distributions and versions. Once the packages.microsoft.com repo has been installed an updated, you can use the package manager to list the packages available from Microsoft.

For example:
````bash
dnf repository-packages packages-microsoft-com-prod list
````
or
````bash
yum repo-pkgs packages-microsoft-com-prod list
````
## Recommendations for client package resources supported by a static interface

Recommendations for using the resources on packages.microsoft.com include:

- The metadata for each package should be considered the source of truth for a given package path if and when a change occurs.
- When possible, use the config files located under `/config` and use standard Linux package managers.
- If you need to programmatically "find" a given package, without using a package manager, be sure to parse the metadata, *not* the html.
- Avoid depending on individual metadata files (such as `primary.sqlite.gz` or `Packages.bz2`), as these are subject to change.
- Packages on packages.microsoft.com may incorporate material from third parties. License information for third party material may be found in the packages themselves or associated documentation. Source code for certain third party material may be available in an associated source directory. Alternatively, you may obtain corresponding source code for certain packages or material by sending an email to Opensource@microsoft.com, including the package name and version information.

### Static vs subject to change

When a Linux packaging client is referred to as “static”, it means that the client is designed to work with a fixed set of libraries. A static client will not dynamically link to any libraries outside of its own set and will instead use only the libraries that are included in the client itself. "Static" resources are typically more safe to depend on, but can still be subject to change.

Static resources on packages.microsoft.com include:

- The path to each repo's metadata, such as the `repomd.xml` or Release/Packages for Debian files. These metadata files are used by the client to determine which packages are available for installation and what their dependencies are.
- The paths to config files located under `/config`.
- The paths to the key files located under `/keys`.

Resources that are subject to change include:

- Paths to individual packages.
- The HTML/directory browsing interface is enabled only for interactive web browsing and is not a stable or supported API. This includes the underlying structure of the HTML, as well as, the timestamp and filesize presented.
- Package repositories often contain multiple copies of the same data in different formats. There's no guarantee that each format will be supported. For example,  Debian repositories *may* include `Packages`, `Packages.bz2`, `Packages.gz`, etc. Rpm repositories *may* include `primary.xml.gz` or `primary.sqlite.bz2`, etc. Package managers will generally prefer one of these formats, but accept an array of format options.
- Clamav signatures located under `/clamav` will no longer be supported, with deprecation scheduled in 2023.

## Deprecated Support for Legacy Domain Names

Historically, packages.microsoft.com content was available on a second domain name: apt-mo.trafficmanager.net.
This is a historical artifact from a time when packages.microsoft.com was not yet an official public offering.
In May of 2025, we will be deprecating support for this domain name.
Requests sent to this domain will be redirected to packages.microsoft.com to prevent impact.
Customers using apt-mo.trafficmanager.net are encouraged to update their repo references to prevent any future issues.
This change will bring performance improvements, including better cache efficiency and faster cache purging operations.

## How to file an issue, request a feature, or report a security vulnerability

We want to ensure that our Linux customers are well-supported. The following communication channels are available to users of the PMC service:

- [Report an issue](https://github.com/microsoft/linux-package-repositories/issues/new?assignees=&labels=&template=report-an-issue.md&title=Report+an+issue): Help us improve the PMC service by reporting any issues you are experiencing.

- [Request a feature](https://github.com/microsoft/linux-package-repositories/issues/new?assignees=&labels=enhancement&template=request-a-feature.md): Request a new feature or enhancement to the PMC service.

- [Report a security vulnerability](https://github.com/microsoft/linux-package-repositories/security/policy): Help us to identify any potential security vulnerabilities by reviewing our security policy and reporting any issues.
