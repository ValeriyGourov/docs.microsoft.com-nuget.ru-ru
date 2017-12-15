---
title: "Справочник по PowerShell NuGet Install-Package | Документы Microsoft"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 6/1/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 879db0ef-6b72-4a4a-bb68-f9e3a00f64b8
description: "Справочник по команду PowerShell Install-Package в консоли диспетчера пакетов NuGet в Visual Studio."
keywords: "Пакет NuGet консоли диспетчера, команд NuGet Powershell, справочник по NuGet Powershell, Install-Package"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: d51cce6223cd2d89c555ca9d6e936eaadf3757bb
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2017
---
# <a name="install-package-package-manager-console-in-visual-studio"></a><span data-ttu-id="084e7-104">Install-Package (консоль диспетчера пакетов в Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="084e7-104">Install-Package (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="084e7-105">*В этом разделе описываются команды в [консоль диспетчера пакетов NuGet](Package-Manager-Console.md) в Visual Studio в Windows. Общая команда PowerShell Install-Package. в разделе [PowerShell PackageManagement ссылка](https://docs.microsoft.com/powershell/module/packagemanagement/?view=powershell-6).*</span><span class="sxs-lookup"><span data-stu-id="084e7-105">*This topic describes the command within the [NuGet Package Manager Console](Package-Manager-Console.md) in Visual Studio on Windows. For the generic PowerShell Install-Package command, see the [PowerShell PackageManagement reference](https://docs.microsoft.com/powershell/module/packagemanagement/?view=powershell-6).*</span></span>

<span data-ttu-id="084e7-106">Устанавливает пакет и его зависимости в проект.</span><span class="sxs-lookup"><span data-stu-id="084e7-106">Installs a package and its dependencies into a project.</span></span>

## <a name="syntax"></a><span data-ttu-id="084e7-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="084e7-107">Syntax</span></span>

```ps
Install-Package [-Id] <string> [-IgnoreDependencies] [-ProjectName <string>] [[-Source] <string>] 
    [[-Version] <string>] [-IncludePrerelease] [-FileConflictAction] [-DependencyVersion]
    [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="084e7-108">В NuGet 2.8 + `Install-Package` может понизить уровень существующий пакет в проекте.</span><span class="sxs-lookup"><span data-stu-id="084e7-108">In NuGet 2.8+, `Install-Package` can downgrade an existing package in your project.</span></span> <span data-ttu-id="084e7-109">Например при наличии 5.1.0-rc1 Microsoft.AspNet.MVC установлен следующая команда будет понизить его до 5.0.0:</span><span class="sxs-lookup"><span data-stu-id="084e7-109">For example, if you have Microsoft.AspNet.MVC 5.1.0-rc1 installed, the following command would downgrade it to 5.0.0:</span></span>

```ps
Install-Package Microsoft.AspNet.MVC -Version 5.0.0.
```

<span data-ttu-id="084e7-110">NuGet 2.7 или более ранних версий выдает ошибку, о том, что уже установлена более новая версия.</span><span class="sxs-lookup"><span data-stu-id="084e7-110">NuGet 2.7 and earlier gives an error saying that a newer version is already installed.</span></span>
  
## <a name="parameters"></a><span data-ttu-id="084e7-111">Параметры</span><span class="sxs-lookup"><span data-stu-id="084e7-111">Parameters</span></span>

| <span data-ttu-id="084e7-112">Параметр</span><span class="sxs-lookup"><span data-stu-id="084e7-112">Parameter</span></span> | <span data-ttu-id="084e7-113">Описание</span><span class="sxs-lookup"><span data-stu-id="084e7-113">Description</span></span> |
| --- | --- |
| <span data-ttu-id="084e7-114">Идентификатор</span><span class="sxs-lookup"><span data-stu-id="084e7-114">Id</span></span> | <span data-ttu-id="084e7-115">(Обязательно) Идентификатор пакета для установки.</span><span class="sxs-lookup"><span data-stu-id="084e7-115">(Required) The identifier of the package to install.</span></span> <span data-ttu-id="084e7-116">(*3.0 +*) может быть идентификатор или URL-адрес `packages.config` файл или `.nupkg` файла.</span><span class="sxs-lookup"><span data-stu-id="084e7-116">(*3.0+*) The identifier can be a path or URL of a `packages.config` file or a `.nupkg` file.</span></span> <span data-ttu-id="084e7-117">— Идентификатор коммутатора сам является необязательным.</span><span class="sxs-lookup"><span data-stu-id="084e7-117">The -Id switch itself is optional.</span></span> |
| <span data-ttu-id="084e7-118">IgnoreDependencies</span><span class="sxs-lookup"><span data-stu-id="084e7-118">IgnoreDependencies</span></span> | <span data-ttu-id="084e7-119">Установите только этот пакет, а не его зависимости.</span><span class="sxs-lookup"><span data-stu-id="084e7-119">Install only this package and not its dependencies.</span></span> |
| <span data-ttu-id="084e7-120">ИмяПроекта</span><span class="sxs-lookup"><span data-stu-id="084e7-120">ProjectName</span></span> | <span data-ttu-id="084e7-121">Проект, в который необходимо установить пакет, установка значений по умолчанию для проекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="084e7-121">The project into which to install the package, defaulting to the default project.</span></span> |
| <span data-ttu-id="084e7-122">Исходный код</span><span class="sxs-lookup"><span data-stu-id="084e7-122">Source</span></span> | <span data-ttu-id="084e7-123">Путь URL-адрес или папку источника пакета для поиска.</span><span class="sxs-lookup"><span data-stu-id="084e7-123">The URL or folder path for the package source to search.</span></span> <span data-ttu-id="084e7-124">Пути к локальной папке может быть абсолютным или относительным для текущей папки.</span><span class="sxs-lookup"><span data-stu-id="084e7-124">Local folder paths can be absolute, or relative to the current folder.</span></span> <span data-ttu-id="084e7-125">Если не указано, `Install-Package` выполняет поиск в текущем выбранном источнике пакетов.</span><span class="sxs-lookup"><span data-stu-id="084e7-125">If omitted, `Install-Package` searches the currently selected package source.</span></span> |
| <span data-ttu-id="084e7-126">Версия</span><span class="sxs-lookup"><span data-stu-id="084e7-126">Version</span></span> | <span data-ttu-id="084e7-127">Версия пакета, чтобы установить, по умолчанию используется последняя версия.</span><span class="sxs-lookup"><span data-stu-id="084e7-127">The version of the package to install, defaulting to the latest version.</span></span> |
| <span data-ttu-id="084e7-128">IncludePrerelease</span><span class="sxs-lookup"><span data-stu-id="084e7-128">IncludePrerelease</span></span> | <span data-ttu-id="084e7-129">Считает, что предварительные версии пакетов для установки.</span><span class="sxs-lookup"><span data-stu-id="084e7-129">Considers prerelease packages for the install.</span></span> <span data-ttu-id="084e7-130">Если не указано, рассматриваются только стабильные пакеты.</span><span class="sxs-lookup"><span data-stu-id="084e7-130">If omitted, only stable packages are considered.</span></span> |
| <span data-ttu-id="084e7-131">FileConflictAction</span><span class="sxs-lookup"><span data-stu-id="084e7-131">FileConflictAction</span></span> | <span data-ttu-id="084e7-132">Действие, выполняемое при появлении запроса, чтобы игнорировать существующие файлы, связанные с проектом или перезаписать.</span><span class="sxs-lookup"><span data-stu-id="084e7-132">The action to take when asked to overwrite or ignore existing files referenced by the project.</span></span> <span data-ttu-id="084e7-133">Возможными значениями являются *перезаписи, пропустить, None, OverwriteAll*, и *(3.0 +)* *IgnoreAll*.</span><span class="sxs-lookup"><span data-stu-id="084e7-133">Possible values are *Overwrite, Ignore, None, OverwriteAll*, and *(3.0+)* *IgnoreAll*.</span></span> |
| <span data-ttu-id="084e7-134">DependencyVersion</span><span class="sxs-lookup"><span data-stu-id="084e7-134">DependencyVersion</span></span> | <span data-ttu-id="084e7-135">Версия пакеты зависимостей для использования, которые может принимать одно из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="084e7-135">The version of the dependency packages to use, which can be one of the following:</span></span><br/><ul><li><span data-ttu-id="084e7-136">*Наименьший* (по умолчанию): самая ранняя версия</span><span class="sxs-lookup"><span data-stu-id="084e7-136">*Lowest* (default): the lowest version</span></span></li><li><span data-ttu-id="084e7-137">*HighestPatch*: версия с исправлением минимально основных минимально дополнительный: наибольшая</span><span class="sxs-lookup"><span data-stu-id="084e7-137">*HighestPatch*: the version with the lowest major, lowest minor, highest patch</span></span></li><li><span data-ttu-id="084e7-138">*HighestMinor*: версия с наименьшим основной, наивысший дополнительный номер: наибольшая исправления</span><span class="sxs-lookup"><span data-stu-id="084e7-138">*HighestMinor*: the version with the lowest major, highest minor, highest patch</span></span></li><li><span data-ttu-id="084e7-139">*Наибольший* (по умолчанию для пакета обновления без параметров): самую новую версию</span><span class="sxs-lookup"><span data-stu-id="084e7-139">*Highest* (default for Update-Package with no parameters): the highest version</span></span></li></ul><span data-ttu-id="084e7-140">Можно задать значение по умолчанию с помощью [ `dependencyVersion` ](../Schema/nuget-config-file.md#config-section) в `Nuget.Config` файла.</span><span class="sxs-lookup"><span data-stu-id="084e7-140">You can set the default value using the [`dependencyVersion`](../Schema/nuget-config-file.md#config-section) setting in the `Nuget.Config` file.</span></span> |
| <span data-ttu-id="084e7-141">WhatIf</span><span class="sxs-lookup"><span data-stu-id="084e7-141">WhatIf</span></span> | <span data-ttu-id="084e7-142">Показывает, что произойдет при запуске команды без фактического выполнения установки.</span><span class="sxs-lookup"><span data-stu-id="084e7-142">Shows what would happen when running the command without actually performing the install.</span></span> |

<span data-ttu-id="084e7-143">Ни один из этих параметров принимает входные данные или подстановочный знак символов конвейера.</span><span class="sxs-lookup"><span data-stu-id="084e7-143">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="084e7-144">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="084e7-144">Common Parameters</span></span>

<span data-ttu-id="084e7-145">`Install-Package`поддерживает следующие [Общие параметры PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): отладка, действие при возникновении ошибки, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction и WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="084e7-145">`Install-Package` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="084e7-146">Примеры</span><span class="sxs-lookup"><span data-stu-id="084e7-146">Examples</span></span>

```ps
# Installs the latest version of Elmah from the current source into the default project
Install-Package Elmah

# Installs Glimpse 1.0.0 into the MvcApplication1 project
Install-Package Glimpse -Version 1.0.0 -Project MvcApplication1

# Installs Ninject.Mvc3 but not its dependencies from c:\temp\packages
Install-Package Ninject.Mvc3 -IgnoreDependencies -Source c:\temp\packages

# Installs the package listed on the online packages.config into the current project.
Install-package https://raw.githubusercontent.com/json-ld.net/master/src/JsonLD/packages.config

# Installs jquery 1.10.2 package, using the .nupkg file under local path of c:\temp\packages.
Install-package c:\temp\packages\jQuery.1.10.2.nupkg

# Installs the specific online package
Install-package https://az320820.vo.msecnd.net/packages/microsoft.aspnet.mvc.5.2.3.nupkg
```