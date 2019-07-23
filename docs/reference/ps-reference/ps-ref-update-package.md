---
title: Справочник по PowerShell для обновления пакета NuGet
description: Справочник по командам PowerShell Update-Package в консоли диспетчера пакетов NuGet в Visual Studio.
author: karann-msft
ms.author: karann
ms.date: 12/07/2017
ms.topic: reference
ms.openlocfilehash: 57e50ed805496b3511bc3b808f89da6f7ad413fc
ms.sourcegitcommit: efc18d484fdf0c7a8979b564dcb191c030601bb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "68327271"
---
# <a name="update-package-package-manager-console-in-visual-studio"></a><span data-ttu-id="18138-103">Update-Package (консоль диспетчера пакетов в Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="18138-103">Update-Package (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="18138-104">*Доступно только в [консоли диспетчера пакетов NuGet](../../consume-packages/install-use-packages-powershell.md) в Visual Studio в Windows.*</span><span class="sxs-lookup"><span data-stu-id="18138-104">*Available only within the [NuGet Package Manager Console](../../consume-packages/install-use-packages-powershell.md) in Visual Studio on Windows.*</span></span>

<span data-ttu-id="18138-105">Обновляет пакет и его зависимости или все пакеты в проекте до более новой версии.</span><span class="sxs-lookup"><span data-stu-id="18138-105">Updates a package and its dependencies, or all packages in a project, to a newer version.</span></span>

## <a name="syntax"></a><span data-ttu-id="18138-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18138-106">Syntax</span></span>

```ps
Update-Package [-Id] <string> [-IgnoreDependencies] [-ProjectName <string>] [-Version <string>]
    [-Safe] [-Source <string>] [-IncludePrerelease] [-Reinstall] [-FileConflictAction]
    [-DependencyVersion] [-ToHighestPatch] [-ToHighestMinor] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="18138-107">В NuGet 2.8 + `Update-Package` можно использовать для понижения уровня существующего пакета в проекте.</span><span class="sxs-lookup"><span data-stu-id="18138-107">In NuGet 2.8+, `Update-Package` can be used to downgrade an existing package in your project.</span></span> <span data-ttu-id="18138-108">Например, при наличии установленного Microsoft. AspNet. MVC 5.1.0-RC1 Следующая команда понизить ее до 5.0.0:</span><span class="sxs-lookup"><span data-stu-id="18138-108">For example, if you have Microsoft.AspNet.MVC 5.1.0-rc1 installed, the following command would downgrade it to 5.0.0:</span></span>

```ps
Update-Package Microsoft.AspNet.MVC -Version 5.0.0.
```

## <a name="parameters"></a><span data-ttu-id="18138-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="18138-109">Parameters</span></span>

|  <span data-ttu-id="18138-110">Параметр</span><span class="sxs-lookup"><span data-stu-id="18138-110">Parameter</span></span> | <span data-ttu-id="18138-111">Описание</span><span class="sxs-lookup"><span data-stu-id="18138-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="18138-112">Идентификатор</span><span class="sxs-lookup"><span data-stu-id="18138-112">Id</span></span> | <span data-ttu-id="18138-113">Идентификатор обновляемого пакета.</span><span class="sxs-lookup"><span data-stu-id="18138-113">The identifier of the package to update.</span></span> <span data-ttu-id="18138-114">Если этот параметр опущен, обновляет все пакеты.</span><span class="sxs-lookup"><span data-stu-id="18138-114">If omitted, updates all packages.</span></span> <span data-ttu-id="18138-115">Сам переключатель-ID является необязательным.</span><span class="sxs-lookup"><span data-stu-id="18138-115">The -Id switch itself is optional.</span></span> |
| <span data-ttu-id="18138-116">игноредепенденЦиес</span><span class="sxs-lookup"><span data-stu-id="18138-116">IgnoreDependencies</span></span> | <span data-ttu-id="18138-117">Пропускает обновление зависимостей пакета.</span><span class="sxs-lookup"><span data-stu-id="18138-117">Skips updating the package's dependencies.</span></span> |
| <span data-ttu-id="18138-118">ИмяПроекта</span><span class="sxs-lookup"><span data-stu-id="18138-118">ProjectName</span></span> | <span data-ttu-id="18138-119">Имя проекта, содержащего пакеты для обновления, по умолчанию — для всех проектов.</span><span class="sxs-lookup"><span data-stu-id="18138-119">The name of the project containing the packages to update, defaulting to all projects.</span></span> |
| <span data-ttu-id="18138-120">Версия</span><span class="sxs-lookup"><span data-stu-id="18138-120">Version</span></span> | <span data-ttu-id="18138-121">Версия, используемая для обновления, по умолчанию — последняя версия.</span><span class="sxs-lookup"><span data-stu-id="18138-121">The version to use for the upgrade, defaulting to the latest version.</span></span> <span data-ttu-id="18138-122">В NuGet 3.0 + значение версии должно быть одним из *самых низких, наибольших, хигхестминор*или *хигхестпатч* (эквивалентно-безопасности).</span><span class="sxs-lookup"><span data-stu-id="18138-122">In NuGet 3.0+, the version value must be one of *Lowest, Highest, HighestMinor*, or *HighestPatch* (equivalent to -Safe).</span></span> |
| <span data-ttu-id="18138-123">Потокобезопасной</span><span class="sxs-lookup"><span data-stu-id="18138-123">Safe</span></span> | <span data-ttu-id="18138-124">Ограничивает обновления только версиями с той же основной и дополнительной версией, что и текущий установленный пакет.</span><span class="sxs-lookup"><span data-stu-id="18138-124">Constrains upgrades to only versions with the same Major and Minor version as the currently installed package.</span></span> |
| <span data-ttu-id="18138-125">Source</span><span class="sxs-lookup"><span data-stu-id="18138-125">Source</span></span> | <span data-ttu-id="18138-126">URL-адрес или путь к папке для источника пакета для поиска.</span><span class="sxs-lookup"><span data-stu-id="18138-126">The URL or folder path for the package source to search.</span></span> <span data-ttu-id="18138-127">Пути к локальным папкам могут быть абсолютными или относительно текущей папки.</span><span class="sxs-lookup"><span data-stu-id="18138-127">Local folder paths can be absolute, or relative to the current folder.</span></span> <span data-ttu-id="18138-128">Если этот параметр опущен `Update-Package` , поиск выполняется в текущем выбранном источнике пакета.</span><span class="sxs-lookup"><span data-stu-id="18138-128">If omitted, `Update-Package` searches the currently selected package source.</span></span> |
| <span data-ttu-id="18138-129">инклудепререлеасе</span><span class="sxs-lookup"><span data-stu-id="18138-129">IncludePrerelease</span></span> | <span data-ttu-id="18138-130">Включает предварительные пакеты для обновлений.</span><span class="sxs-lookup"><span data-stu-id="18138-130">Includes prerelease packages for updates.</span></span> |
| <span data-ttu-id="18138-131">Переустановка</span><span class="sxs-lookup"><span data-stu-id="18138-131">Reinstall</span></span> | <span data-ttu-id="18138-132">Ресинталлс пакеты, используя установленные в настоящее время версии.</span><span class="sxs-lookup"><span data-stu-id="18138-132">Resintalls packages using their currently installed versions.</span></span> <span data-ttu-id="18138-133">Дополнительные сведения см. в разделе [Ограничение версий для обновления](../../consume-packages/reinstalling-and-updating-packages.md).</span><span class="sxs-lookup"><span data-stu-id="18138-133">See [Reinstalling and updating packages](../../consume-packages/reinstalling-and-updating-packages.md).</span></span> |
| <span data-ttu-id="18138-134">филеконфликтактион</span><span class="sxs-lookup"><span data-stu-id="18138-134">FileConflictAction</span></span> | <span data-ttu-id="18138-135">Действие, предпринимаемое при запросе перезаписи или пропуска существующих файлов, на которые ссылается проект.</span><span class="sxs-lookup"><span data-stu-id="18138-135">The action to take when asked to overwrite or ignore existing files referenced by the project.</span></span> <span data-ttu-id="18138-136">Возможные значения: *overwrite, ignore, None, овервритеалл*и *IgnoreAll* (3.0 +).</span><span class="sxs-lookup"><span data-stu-id="18138-136">Possible values are *Overwrite, Ignore, None, OverwriteAll*, and *IgnoreAll* (3.0+).</span></span> |
| <span data-ttu-id="18138-137">депенденциверсион</span><span class="sxs-lookup"><span data-stu-id="18138-137">DependencyVersion</span></span> | <span data-ttu-id="18138-138">Используемая версия пакетов зависимостей, которая может быть одной из следующих:</span><span class="sxs-lookup"><span data-stu-id="18138-138">The version of the dependency packages to use, which can be one of the following:</span></span><br/><ul><li><span data-ttu-id="18138-139">*Самый низкий* (по умолчанию): самая низкая версия</span><span class="sxs-lookup"><span data-stu-id="18138-139">*Lowest* (default): the lowest version</span></span></li><li><span data-ttu-id="18138-140">*Хигхестпатч*: версия с наименьшим основным, наименьшим незначительным, самым высоким исправлением</span><span class="sxs-lookup"><span data-stu-id="18138-140">*HighestPatch*: the version with the lowest major, lowest minor, highest patch</span></span></li><li><span data-ttu-id="18138-141">*Хигхестминор*: версия с наименьшим основным, наибольшим незначительным, самым высоким исправлением</span><span class="sxs-lookup"><span data-stu-id="18138-141">*HighestMinor*: the version with the lowest major, highest minor, highest patch</span></span></li><li><span data-ttu-id="18138-142">*Самый высокий* (по умолчанию для Update-Package без параметров): самая высокая версия</span><span class="sxs-lookup"><span data-stu-id="18138-142">*Highest* (default for Update-Package with no parameters): the highest version</span></span></li></ul><span data-ttu-id="18138-143">Значение по умолчанию можно задать с помощью [`dependencyVersion`](../nuget-config-file.md#config-section) параметра `Nuget.Config` в файле.</span><span class="sxs-lookup"><span data-stu-id="18138-143">You can set the default value using the [`dependencyVersion`](../nuget-config-file.md#config-section) setting in the `Nuget.Config` file.</span></span> |
| <span data-ttu-id="18138-144">тохигхестпатч</span><span class="sxs-lookup"><span data-stu-id="18138-144">ToHighestPatch</span></span> | <span data-ttu-id="18138-145">эквивалентно-Сейф.</span><span class="sxs-lookup"><span data-stu-id="18138-145">equivalent to -Safe.</span></span> |
| <span data-ttu-id="18138-146">тохигхестминор</span><span class="sxs-lookup"><span data-stu-id="18138-146">ToHighestMinor</span></span> | <span data-ttu-id="18138-147">Ограничивает обновления только версиями с той же основной версией, что и текущий установленный пакет.</span><span class="sxs-lookup"><span data-stu-id="18138-147">Constrains upgrades to only versions with the same Major version as the currently installed package.</span></span> |
| <span data-ttu-id="18138-148">WhatIf</span><span class="sxs-lookup"><span data-stu-id="18138-148">WhatIf</span></span> | <span data-ttu-id="18138-149">Показывает, что произойдет при выполнении команды без фактического выполнения обновления.</span><span class="sxs-lookup"><span data-stu-id="18138-149">Shows what would happen when running the command without actually performing the update.</span></span> |

<span data-ttu-id="18138-150">Ни один из этих параметров не принимает входные данные конвейера или подстановочные знаки.</span><span class="sxs-lookup"><span data-stu-id="18138-150">None of these parameters accept pipeline input or wildcard characters.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="18138-151">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="18138-151">Common Parameters</span></span>

<span data-ttu-id="18138-152">`Update-Package`поддерживает следующие [Общие параметры PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): Отладка, действие при ошибке, ErrorVariable, буфер, переменная, PipelineVariable, Verbose, WarningAction и WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="18138-152">`Update-Package` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

### <a name="examples"></a><span data-ttu-id="18138-153">Примеры</span><span class="sxs-lookup"><span data-stu-id="18138-153">Examples</span></span>

```ps
# Updates all packages in every project of the solution
Update-Package

# Updates every package in the MvcApplication1 project
Update-Package -ProjectName MvcApplication1

# Updates the Elmah package in every project to the latest version
Update-Package Elmah

# Updates the Elmah package to version 1.1.0 in every project showing optional -Id usage
Update-Package -Id Elmah -Version 1.1.0

# Updates the Elmah package within the MvcApplication1 project to the highest "safe" version.
# For example, if Elmah version 1.0.0 of a package is installed, and versions 1.0.1, 1.0.2,
# and 1.1 are available in the feed, the -Safe parameter updates the package to 1.0.2 instead
# of 1.1 as it would otherwise.
Update-Package Elmah -ProjectName MvcApplication1 -Safe

# Reinstall the same version of the original package, but with the latest version of dependencies
# (subject to version constraints). If this command rolls a dependency back to an earlier version,
# use Update-Package <dependency_name> to reinstall that one dependency without affecting the
# dependent package.
Update-Package ELmah –reinstall 

# Reinstall the Elmah package in just MyProject
Update-Package Elmah -ProjectName MyProject -reinstall

# Reinstall the same version of the original package without touching dependencies.
Update-Package ELmah –reinstall -ignoreDependencies
```