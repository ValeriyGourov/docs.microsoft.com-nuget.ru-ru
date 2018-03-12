---
title: "NuGet CLI проверьте команду | Документы Microsoft"
author: dtivel
ms.author: dtivel
manager: doronm
ms.date: 03/06/2018
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Справочник по nuget.exe проверьте команды"
keywords: "NuGet проверить ссылку, проверьте команды"
ms.reviewer:
- karann
- rmpablos
ms.openlocfilehash: 2747491eb35d8685a44e86fcc1b572013982c754
ms.sourcegitcommit: 8f26d10bdf256f72962010348083ff261dae81b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="verify-command-nuget-cli"></a><span data-ttu-id="d32ff-104">Проверьте команду (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="d32ff-104">verify command (NuGet CLI)</span></span>

<span data-ttu-id="d32ff-105">**Применяется к:** пакета потребления &bullet; **поддерживаемые версии:** 4.6 +</span><span class="sxs-lookup"><span data-stu-id="d32ff-105">**Applies to:** package consumption &bullet; **Supported versions:** 4.6+</span></span>

<span data-ttu-id="d32ff-106">Проверка пакета.</span><span class="sxs-lookup"><span data-stu-id="d32ff-106">Verifies a package.</span></span>

## <a name="usage"></a><span data-ttu-id="d32ff-107">Использование</span><span class="sxs-lookup"><span data-stu-id="d32ff-107">Usage</span></span>

```cli
nuget verify <package(s)> [options]
```

<span data-ttu-id="d32ff-108">где `<package(s)>` одной или нескольких `.nupkg` файлов.</span><span class="sxs-lookup"><span data-stu-id="d32ff-108">where `<package(s)>` is one or more `.nupkg` files.</span></span>

## <a name="options"></a><span data-ttu-id="d32ff-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="d32ff-109">Options</span></span>

| <span data-ttu-id="d32ff-110">Параметр</span><span class="sxs-lookup"><span data-stu-id="d32ff-110">Option</span></span> | <span data-ttu-id="d32ff-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="d32ff-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="d32ff-112">Все</span><span class="sxs-lookup"><span data-stu-id="d32ff-112">All</span></span> | <span data-ttu-id="d32ff-113">Указывает, что все проверки на возможные должна быть выполнена на пакетов.</span><span class="sxs-lookup"><span data-stu-id="d32ff-113">Specifies that all verifications possible should be performed on the package(s).</span></span> |
| <span data-ttu-id="d32ff-114">CertificateFingerprint</span><span class="sxs-lookup"><span data-stu-id="d32ff-114">CertificateFingerprint</span></span> | <span data-ttu-id="d32ff-115">Указывает один или несколько отпечатки сертификата SHA-256, какие знаком должен быть подписан с помощью сертификатов (s).</span><span class="sxs-lookup"><span data-stu-id="d32ff-115">Specifies one or more SHA-256 certificate fingerprints of certificates(s) which signed packages must be signed with.</span></span> <span data-ttu-id="d32ff-116">Отпечаток сертификата SHA-256 является хэш сертификата SHA-256.</span><span class="sxs-lookup"><span data-stu-id="d32ff-116">A certificate SHA-256 fingerprint is a SHA-256 hash of the certificate.</span></span> <span data-ttu-id="d32ff-117">Несколько входов должно быть разделенных точкой с запятой.</span><span class="sxs-lookup"><span data-stu-id="d32ff-117">Multiple inputs should be semicolon separated.</span></span> |
| <span data-ttu-id="d32ff-118">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="d32ff-118">ConfigFile</span></span> | <span data-ttu-id="d32ff-119">Файл конфигурации NuGet вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="d32ff-119">The NuGet configuration file to apply.</span></span> <span data-ttu-id="d32ff-120">Если не указан, *%AppData%\NuGet\NuGet.Config* используется.</span><span class="sxs-lookup"><span data-stu-id="d32ff-120">If not specified, *%AppData%\NuGet\NuGet.Config* is used.</span></span> |
| <span data-ttu-id="d32ff-121">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="d32ff-121">ForceEnglishOutput</span></span> | <span data-ttu-id="d32ff-122">Принудительно nuget.exe выполняется с использованием инвариантных, на основе английского языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="d32ff-122">Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="d32ff-123">Справка</span><span class="sxs-lookup"><span data-stu-id="d32ff-123">Help</span></span> | <span data-ttu-id="d32ff-124">Отображает справку по команде.</span><span class="sxs-lookup"><span data-stu-id="d32ff-124">Displays help information for the command.</span></span> |
| <span data-ttu-id="d32ff-125">Неинтерактивные</span><span class="sxs-lookup"><span data-stu-id="d32ff-125">NonInteractive</span></span> | <span data-ttu-id="d32ff-126">Подавление для ввода данных и подтверждений.</span><span class="sxs-lookup"><span data-stu-id="d32ff-126">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="d32ff-127">Сигнатуры</span><span class="sxs-lookup"><span data-stu-id="d32ff-127">Signatures</span></span> | <span data-ttu-id="d32ff-128">Указывает, что должна быть выполнена проверка подписи пакета.</span><span class="sxs-lookup"><span data-stu-id="d32ff-128">Specifies that package signature verification should be performed.</span></span> |
| <span data-ttu-id="d32ff-129">Уровень детализации</span><span class="sxs-lookup"><span data-stu-id="d32ff-129">Verbosity</span></span> | <span data-ttu-id="d32ff-130">Указывает объем сведений в выходных данных: *обычного*, *тихий*, *подробные*.</span><span class="sxs-lookup"><span data-stu-id="d32ff-130">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

## <a name="examples"></a><span data-ttu-id="d32ff-131">Примеры</span><span class="sxs-lookup"><span data-stu-id="d32ff-131">Examples</span></span>

```cli
nuget verify -Signatures .\..\MyPackage.nupkg -CertificateFingerprint "CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039;5F874AAF47BCB268A19357364E7FBB09D6BF9E8A93E1229909AC5CAC865802E2" -Verbosity detailed

nuget verify -Signatures c:\packages\MyPackage.nupkg -CertificateFingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039

nuget verify -Signatures MyPackage.nupkg -Verbosity quiet

nuget verify -Signatures .\*.nupkg
```