---
title: Creazione del file Web. config per un servizio Web OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359790"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a><span data-ttu-id="e7449-102">Creazione del file Web.config per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="e7449-102">Authoring the Web.config file for a Management OData web service</span></span>

<span data-ttu-id="e7449-103">Prima di poter distribuire il servizio Web OData di gestione, è necessario configurare il file Web. config in modo che punti ai file di XML Schema e alle DLL che implementano [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) e [ Interfacce System. Management. Automation. Remoting. PSSessionConfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) .</span><span class="sxs-lookup"><span data-stu-id="e7449-103">Before you can deploy your Management OData web service, you must configure the web.config file to point to the XML schema files and the DLLs that implement the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) and  [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.</span></span>

## <a name="sample-config-file"></a><span data-ttu-id="e7449-104">File di configurazione di esempio</span><span class="sxs-lookup"><span data-stu-id="e7449-104">Sample config file</span></span>

<span data-ttu-id="e7449-105">Di seguito è riportato un esempio di come appare il file Web. config per il servizio Web.</span><span class="sxs-lookup"><span data-stu-id="e7449-105">The following is an example of what the web.config file for your web service looks like.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a><span data-ttu-id="e7449-106">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e7449-106">See Also</span></span>

[<span data-ttu-id="e7449-107">Implementazione dell'autorizzazione personalizzata per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="e7449-107">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[<span data-ttu-id="e7449-108">Implementazione di SessionConfiguration per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="e7449-108">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[<span data-ttu-id="e7449-109">Creazione del file di schema MOF per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="e7449-109">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="e7449-110">Creazione del file di XML Schema per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="e7449-110">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="e7449-111">Creazione di un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="e7449-111">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)