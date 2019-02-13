---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682989"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4cb04-103">Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4cb04-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4cb04-104">Invia il documento di configurazione in modo asicrono al nodo gestito e usa l'agente di configurazione per applicare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4cb04-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="4cb04-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4cb04-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="4cb04-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="4cb04-106">Parameters</span></span>

<span data-ttu-id="4cb04-107">*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4cb04-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="4cb04-108">*force* \[in\] **true** per forzare l'arresto della configurazione.</span><span class="sxs-lookup"><span data-stu-id="4cb04-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="4cb04-109">*jobId* \[in\] ID del processo per cui inviare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="4cb04-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4cb04-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4cb04-110">Return value</span></span>

<span data-ttu-id="4cb04-111">In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="4cb04-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4cb04-112">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4cb04-112">Remarks</span></span>

<span data-ttu-id="4cb04-113">Si tratta di un metodo statico.</span><span class="sxs-lookup"><span data-stu-id="4cb04-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4cb04-114">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4cb04-114">Requirements</span></span>

<span data-ttu-id="4cb04-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4cb04-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4cb04-116">**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4cb04-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4cb04-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4cb04-117">See also</span></span>

[<span data-ttu-id="4cb04-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4cb04-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)