---
title: Set di parametri del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365900"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="9598d-102">Set di parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="9598d-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="9598d-103">PowerShell usa i set di parametri per consentire la scrittura di un singolo cmdlet che può eseguire diverse azioni per diversi scenari.</span><span class="sxs-lookup"><span data-stu-id="9598d-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="9598d-104">I set di parametri consentono di esporre parametri diversi all'utente.</span><span class="sxs-lookup"><span data-stu-id="9598d-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="9598d-105">Per restituire informazioni diverse in base ai parametri specificati dall'utente.</span><span class="sxs-lookup"><span data-stu-id="9598d-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="9598d-106">Esempi di set di parametri</span><span class="sxs-lookup"><span data-stu-id="9598d-106">Examples of parameter sets</span></span>

<span data-ttu-id="9598d-107">Ad esempio, il cmdlet `Get-EventLog` di PowerShell restituisce informazioni diverse a seconda che l'utente specifichi il parametro **List** o **logName** .</span><span class="sxs-lookup"><span data-stu-id="9598d-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="9598d-108">Se viene specificato il parametro **List** , il cmdlet restituisce le informazioni sui file di log, ma non le informazioni sull'evento contenute.</span><span class="sxs-lookup"><span data-stu-id="9598d-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="9598d-109">Se viene specificato il parametro **logName** , il cmdlet restituisce informazioni sugli eventi in un registro eventi specifico.</span><span class="sxs-lookup"><span data-stu-id="9598d-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="9598d-110">I parametri **List** e **logName** identificano due set di parametri distinti.</span><span class="sxs-lookup"><span data-stu-id="9598d-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="9598d-111">Parametro univoco</span><span class="sxs-lookup"><span data-stu-id="9598d-111">Unique parameter</span></span>

<span data-ttu-id="9598d-112">Ogni set di parametri deve avere un parametro univoco usato dal runtime di PowerShell per esporre il set di parametri appropriato.</span><span class="sxs-lookup"><span data-stu-id="9598d-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="9598d-113">Se possibile, il parametro Unique deve essere un parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="9598d-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="9598d-114">Quando un parametro è obbligatorio, l'utente deve specificare il parametro e il runtime di PowerShell usa tale parametro per identificare il set di parametri.</span><span class="sxs-lookup"><span data-stu-id="9598d-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="9598d-115">Il parametro Unique non può essere obbligatorio se il cmdlet è progettato per essere eseguito senza specificare alcun parametro.</span><span class="sxs-lookup"><span data-stu-id="9598d-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="9598d-116">Set di parametri multipli</span><span class="sxs-lookup"><span data-stu-id="9598d-116">Multiple parameter sets</span></span>

<span data-ttu-id="9598d-117">Nella figura seguente la colonna sinistra mostra tre set di parametri validi.</span><span class="sxs-lookup"><span data-stu-id="9598d-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="9598d-118">Il **parametro a** è univoco per il primo set di parametri, il **parametro B** è univoco per il secondo set di parametri e il **parametro C** è univoco per il terzo set di parametri.</span><span class="sxs-lookup"><span data-stu-id="9598d-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="9598d-119">Nella colonna a destra i set di parametri non hanno un parametro univoco.</span><span class="sxs-lookup"><span data-stu-id="9598d-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="9598d-121">Requisiti per i set di parametri</span><span class="sxs-lookup"><span data-stu-id="9598d-121">Parameter set requirements</span></span>

<span data-ttu-id="9598d-122">I requisiti seguenti si applicano a tutti i set di parametri.</span><span class="sxs-lookup"><span data-stu-id="9598d-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="9598d-123">Ogni set di parametri deve avere almeno un parametro univoco.</span><span class="sxs-lookup"><span data-stu-id="9598d-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="9598d-124">Se possibile, rendere questo parametro un parametro obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="9598d-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="9598d-125">Un set di parametri che contiene più parametri posizionali deve definire posizioni univoche per ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="9598d-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="9598d-126">Non è possibile specificare la stessa posizione per due parametri posizionali.</span><span class="sxs-lookup"><span data-stu-id="9598d-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="9598d-127">Solo un parametro in un set può dichiarare la parola chiave `ValueFromPipeline` con un valore di `true`.</span><span class="sxs-lookup"><span data-stu-id="9598d-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="9598d-128">Più parametri possono definire la parola chiave `ValueFromPipelineByPropertyName` con un valore di `true`.</span><span class="sxs-lookup"><span data-stu-id="9598d-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="9598d-129">Se per un parametro non è specificato alcun set di parametri, il parametro appartiene a tutti i set di parametri.</span><span class="sxs-lookup"><span data-stu-id="9598d-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="9598d-130">Per un cmdlet o una funzione, è previsto un limite di 32 set di parametri.</span><span class="sxs-lookup"><span data-stu-id="9598d-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="9598d-131">Set di parametri predefiniti</span><span class="sxs-lookup"><span data-stu-id="9598d-131">Default parameter sets</span></span>

<span data-ttu-id="9598d-132">Quando vengono definiti più set di parametri, è possibile usare la parola chiave `DefaultParameterSetName` dell'attributo **cmdlet** per specificare il set di parametri predefinito.</span><span class="sxs-lookup"><span data-stu-id="9598d-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="9598d-133">PowerShell usa il set di parametri predefinito se non è in grado di determinare il set di parametri da usare in base alle informazioni fornite dal comando.</span><span class="sxs-lookup"><span data-stu-id="9598d-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="9598d-134">Per ulteriori informazioni sull'attributo **cmdlet** , vedere [dichiarazione dell'attributo del cmdlet](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9598d-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="9598d-135">Dichiarazione di set di parametri</span><span class="sxs-lookup"><span data-stu-id="9598d-135">Declaring parameter sets</span></span>

<span data-ttu-id="9598d-136">Per creare un set di parametri, è necessario specificare la parola chiave `ParameterSetName` quando si dichiara l'attributo del **parametro** per ogni parametro nel set di parametri.</span><span class="sxs-lookup"><span data-stu-id="9598d-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="9598d-137">Per i parametri che appartengono a più set di parametri, aggiungere un attributo di **parametro** per ogni set di parametri.</span><span class="sxs-lookup"><span data-stu-id="9598d-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="9598d-138">Questo attributo consente di definire il parametro in modo diverso per ogni set di parametri.</span><span class="sxs-lookup"><span data-stu-id="9598d-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="9598d-139">È ad esempio possibile definire un parametro come obbligatorio in un unico set e facoltativo in un altro.</span><span class="sxs-lookup"><span data-stu-id="9598d-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="9598d-140">Tuttavia, ogni set di parametri deve contenere un parametro univoco.</span><span class="sxs-lookup"><span data-stu-id="9598d-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="9598d-141">Per altre informazioni, vedere [dichiarazione dell'attributo Parameter](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="9598d-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="9598d-142">Nell'esempio seguente il parametro **username** è il parametro Unique del set di parametri `Test01`, mentre il parametro **ComputerName** è il parametro Unique del set di parametri `Test02`.</span><span class="sxs-lookup"><span data-stu-id="9598d-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="9598d-143">Il parametro **SharedParam** appartiene a entrambi i set ed è obbligatorio per il set di parametri `Test01` ma facoltativo per il set di parametri `Test02`.</span><span class="sxs-lookup"><span data-stu-id="9598d-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;
```