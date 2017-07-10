---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Publish-Script
ms.openlocfilehash: 0d2fd87645d2286e87e68198844adce8909739cb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="publish-script" class="xliff"></a>
# Publish-Script

Il cmdlet Publish-Script pubblica lo script specificato nella raccolta in linea.

<a id="description" class="xliff"></a>
## Descrizione

Il cmdlet Publish-Script consente di pubblicare il file di script con metadati validi come Version, Guid, Author, Description e così via. Il parametro opzionale Force nel cmdlet Publish-Script avvia il file NuGet.exe senza chiedere conferma.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintassi del cmdlet

```powershell
Get-Command -Name Publish-Script -Module PowerShellGet -Syntax
```

<a id="cmdlet-online-help-reference" class="xliff"></a>
## Riferimento per la Guida online sui cmdlet

[Publish-Script](http://go.microsoft.com/fwlink/?LinkId=619788)

<a id="example-commands" class="xliff"></a>
## Comandi di esempio

```powershell
# Publish the really basic script file with required metadata

Publish-Script -Path C:\ScriptSharingDemo\Demo-Script.ps1 -Repository GalleryINT -NuGetApiKey cad91af7-a49c-4026-9570-a4c16564e785 -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you
want PowerShellGet to install NuGet.exe now?
[Y] Yes [N] No [S] Suspend [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: GET http://go.microsoft.com/fwlink/?LinkID=690216&clcid=0x409 with 0-byte payload
VERBOSE: received 1686528-byte response of content type application/octet-stream
VERBOSE: Performing the operation "Publish-Script" on target "Version '1.0' of script 'Demo-Script'".
VERBOSE: Successfully published script 'Demo-Script' to the publish location 'https://customgallery.cloudapp.net/api/v2/package/'. Please allow few minutes for 'Demo-Script' to show up in the search results.

Find-Script -Repository GalleryINT -Name Demo-Script

Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script GalleryINT Script file description goes here

Find-Script -Repository GalleryINT -Name Demo-Script | Format-List * -Force

Name : Demo-Script
Version : 1.0
Type : Script
Description : Script file description goes here
Author : manikb
CompanyName : manikb
Copyright :
PublishedDate : 11/16/2015 6:46:28 PM
LicenseUri :
ProjectUri :
IconUri :
Tags : {PSScript}
Includes : {Function, DscResource, Cmdlet, Workflow...}
PowerShellGetFormatVersion :
ReleaseNotes :
Dependencies : {}
RepositorySourceLocation : https://customgallery.cloudapp.net/api/v2/
Repository : GalleryINT
PackageManagementProvider : NuGet
AdditionalMetadata : {description, developmentDependency, tags, PackageManagementProvider...}

```

