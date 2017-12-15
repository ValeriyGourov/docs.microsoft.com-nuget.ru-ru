---
title: "Локальные переменные команду NuGet CLI | Документы Microsoft"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 7f672c7c-74c9-4296-bc27-4d47882b541c
description: "Ссылка для команды локальные nuget.exe"
keywords: "Справочник по NuGet локальные переменные, локальные команды"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 8cc06eedc20507e2bdd210e40c471ff551b89563
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2017
---
## <a name="locals-command-nuget-cli"></a><span data-ttu-id="c38f5-104">Команда локальные переменные (NuGet CLI)</span><span class="sxs-lookup"><span data-stu-id="c38f5-104">locals command (NuGet CLI)</span></span>

<span data-ttu-id="c38f5-105">**Применяется к:** пакета потребления &bullet; **поддерживаемые версии:** 3.3 +</span><span class="sxs-lookup"><span data-stu-id="c38f5-105">**Applies to:** package consumption &bullet; **Supported versions:** 3.3+</span></span>

<span data-ttu-id="c38f5-106">Очищает или перечисляет локальные ресурсы NuGet кэша HTTP-запроса, пакеты кэша и папке пакеты глобального уровня компьютера.</span><span class="sxs-lookup"><span data-stu-id="c38f5-106">Clears or lists local NuGet resources such as the http-request cache, packages cache, and the machine-wide global packages folder.</span></span> <span data-ttu-id="c38f5-107">`locals` Команда также может использоваться для отображения списка из этих расположений.</span><span class="sxs-lookup"><span data-stu-id="c38f5-107">The `locals` command can also be used to display a list of those locations.</span></span> <span data-ttu-id="c38f5-108">Дополнительные сведения см. в разделе [Управление кэшем NuGet](../consume-packages/managing-the-nuget-cache.md).</span><span class="sxs-lookup"><span data-stu-id="c38f5-108">For more information, see [Managing the NuGet Cache](../consume-packages/managing-the-nuget-cache.md).</span></span>

## <a name="usage"></a><span data-ttu-id="c38f5-109">Использование</span><span class="sxs-lookup"><span data-stu-id="c38f5-109">Usage</span></span>

```
nuget locals <cache> [options]
```

<span data-ttu-id="c38f5-110">где `<cache>` является одним из `all`, `http-cache`, `packages-cache`, `global-packages`, и `temp` *(3.4 +)*.</span><span class="sxs-lookup"><span data-stu-id="c38f5-110">where `<cache>` is one of `all`, `http-cache`, `packages-cache`, `global-packages`, and `temp` *(3.4+)*.</span></span>

## <a name="options"></a><span data-ttu-id="c38f5-111">Параметры</span><span class="sxs-lookup"><span data-stu-id="c38f5-111">Options</span></span>

| <span data-ttu-id="c38f5-112">Параметр</span><span class="sxs-lookup"><span data-stu-id="c38f5-112">Option</span></span> | <span data-ttu-id="c38f5-113">Описание</span><span class="sxs-lookup"><span data-stu-id="c38f5-113">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c38f5-114">Clear</span><span class="sxs-lookup"><span data-stu-id="c38f5-114">Clear</span></span> | <span data-ttu-id="c38f5-115">Удаляет указанный кэш.</span><span class="sxs-lookup"><span data-stu-id="c38f5-115">Clears the specified cache.</span></span> |
| <span data-ttu-id="c38f5-116">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="c38f5-116">ConfigFile</span></span> | <span data-ttu-id="c38f5-117">Файл конфигурации NuGet вступили в силу.</span><span class="sxs-lookup"><span data-stu-id="c38f5-117">The NuGet configuration file to apply.</span></span> <span data-ttu-id="c38f5-118">Если не указан, *%AppData%\NuGet\NuGet.Config* используется.</span><span class="sxs-lookup"><span data-stu-id="c38f5-118">If not specified, *%AppData%\NuGet\NuGet.Config* is used.</span></span> |
| <span data-ttu-id="c38f5-119">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="c38f5-119">ForceEnglishOutput</span></span> | <span data-ttu-id="c38f5-120">*(3.5 +)*  Принудительно nuget.exe выполняется с использованием инвариантных, на основе английского языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="c38f5-120">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="c38f5-121">Справка</span><span class="sxs-lookup"><span data-stu-id="c38f5-121">Help</span></span> | <span data-ttu-id="c38f5-122">Отображает справку по команде.</span><span class="sxs-lookup"><span data-stu-id="c38f5-122">Displays help information for the command.</span></span> |
| <span data-ttu-id="c38f5-123">Список</span><span class="sxs-lookup"><span data-stu-id="c38f5-123">List</span></span> | <span data-ttu-id="c38f5-124">Выводит расположение указанного кэша или расположение всех кэшей, при использовании с *все*.</span><span class="sxs-lookup"><span data-stu-id="c38f5-124">Lists the location of the specified cache, or the locations of all caches when used with *all*.</span></span> |
| <span data-ttu-id="c38f5-125">Неинтерактивные</span><span class="sxs-lookup"><span data-stu-id="c38f5-125">NonInteractive</span></span> | <span data-ttu-id="c38f5-126">Подавление для ввода данных и подтверждений.</span><span class="sxs-lookup"><span data-stu-id="c38f5-126">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="c38f5-127">Уровень детализации</span><span class="sxs-lookup"><span data-stu-id="c38f5-127">Verbosity</span></span> | <span data-ttu-id="c38f5-128">Указывает объем сведений в выходных данных: *обычного*, *тихий*, *подробные*.</span><span class="sxs-lookup"><span data-stu-id="c38f5-128">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

<span data-ttu-id="c38f5-129">См. также [переменные среды](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="c38f5-129">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

## <a name="examples"></a><span data-ttu-id="c38f5-130">Примеры</span><span class="sxs-lookup"><span data-stu-id="c38f5-130">Examples</span></span>

```
nuget locals all -list
nuget locals http-cache -clear
```