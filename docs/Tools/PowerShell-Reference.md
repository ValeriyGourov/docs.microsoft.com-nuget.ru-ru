---
title: "Справочник по PowerShell NuGet | Документы Microsoft"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/2/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: cd08b869-44c6-480e-90f7-494a6d08e6d0
description: "Полный справочник команд PowerShell доступны в консоли диспетчера пакетов NuGet в Visual Studio."
keywords: "Консоли пакета NuGet диспетчера, команд NuGet Powershell, справочник по NuGet Powershell"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: c0da5c88447784fdd49d824bbd03b11f73c22ebc
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2017
---
# <a name="powershell-reference"></a><span data-ttu-id="45390-104">Справочник по PowerShell</span><span class="sxs-lookup"><span data-stu-id="45390-104">PowerShell reference</span></span>

<span data-ttu-id="45390-105">Консоль диспетчера пакетов предоставляет интерфейс PowerShell в среде Visual Studio в Windows для взаимодействия с помощью NuGet через определенные команды перечисленные ниже.</span><span class="sxs-lookup"><span data-stu-id="45390-105">The Package Manager Console provides a PowerShell interface within Visual Studio on Windows to interact with NuGet through the specific commands listed below.</span></span> <span data-ttu-id="45390-106">(Консоль недоступна в настоящее время в Visual Studio для Mac.) Руководство по использованию консоли см. в разделе [консоль диспетчера пакетов](../tools/package-manager-console.md) раздела.</span><span class="sxs-lookup"><span data-stu-id="45390-106">(The console is not presently available in Visual Studio for Mac.) For a guide to using the console, see the [Package Manager Console](../tools/package-manager-console.md) topic.</span></span>

> [!Tip]
> <span data-ttu-id="45390-107">Все команды PowerShell относятся только к потребления пакета.</span><span class="sxs-lookup"><span data-stu-id="45390-107">All PowerShell commands relate only to package consumption.</span></span> <span data-ttu-id="45390-108">Команды PowerShell не связаны с создания и публикации пакеты, за исключением того, при условии, что пакет может быть также потребителя другие пакеты.</span><span class="sxs-lookup"><span data-stu-id="45390-108">No PowerShell commands relate to creating and publishing packages except to the extent that a package can also be a consumer of other packages.</span></span>

> [!Important]
> <span data-ttu-id="45390-109">Команды, перечисленные ниже относятся к консоли диспетчера пакетов в Visual Studio и отличаться от [команды модуля пакета управления](https://msdn.microsoft.com/powershell/reference/6/packagemanagement/packagemanagement) , которые доступны в среде PowerShell Общие.</span><span class="sxs-lookup"><span data-stu-id="45390-109">The commands listed here are specific to the Package Manager Console in Visual Studio, and differ from the [Package Management module commands](https://msdn.microsoft.com/powershell/reference/6/packagemanagement/packagemanagement) that are available in a general PowerShell environment.</span></span> <span data-ttu-id="45390-110">В частности каждая среда имеет команд, которые недоступны в другом, а команды с тем же именем в их конкретных аргументах также могут различаться.</span><span class="sxs-lookup"><span data-stu-id="45390-110">Specifically, each environment has commands that are not available in the other, and commands with the same name may also differ in their specific arguments.</span></span> <span data-ttu-id="45390-111">При использовании консоли управления пакета в Visual Studio, команды и аргументы, описанные в этом разделе присутствует применяются.</span><span class="sxs-lookup"><span data-stu-id="45390-111">When using the Package Management Console in Visual Studio, the commands and arguments documented in this present topic apply.</span></span>

| <span data-ttu-id="45390-112">Стандартные команды</span><span class="sxs-lookup"><span data-stu-id="45390-112">Common Commands</span></span> | <span data-ttu-id="45390-113">Описание</span><span class="sxs-lookup"><span data-stu-id="45390-113">Description</span></span> | <span data-ttu-id="45390-114">Версия NuGet</span><span class="sxs-lookup"><span data-stu-id="45390-114">NuGet Version</span></span> |
| --- | --- | --- |
| [<span data-ttu-id="45390-115">Пакет установки</span><span class="sxs-lookup"><span data-stu-id="45390-115">Install-Package</span></span>](ps-ref-install-package.md) | <span data-ttu-id="45390-116">Устанавливает пакет и его зависимости в проект.</span><span class="sxs-lookup"><span data-stu-id="45390-116">Installs a package and its dependencies into the project.</span></span> | <span data-ttu-id="45390-117">Все</span><span class="sxs-lookup"><span data-stu-id="45390-117">All</span></span> |
| [<span data-ttu-id="45390-118">Пакет обновления</span><span class="sxs-lookup"><span data-stu-id="45390-118">Update-Package</span></span>](ps-ref-update-package.md) | <span data-ttu-id="45390-119">Обновляет пакет и его зависимости, а также все пакеты в проекте.</span><span class="sxs-lookup"><span data-stu-id="45390-119">Updates a package and its dependencies, or all packages in a project.</span></span> | <span data-ttu-id="45390-120">Все</span><span class="sxs-lookup"><span data-stu-id="45390-120">All</span></span> |
| [<span data-ttu-id="45390-121">Find-Package</span><span class="sxs-lookup"><span data-stu-id="45390-121">Find-Package</span></span>](ps-ref-find-package.md) | <span data-ttu-id="45390-122">Поиск источника пакета, используя идентификатор пакета или ключевые слова.</span><span class="sxs-lookup"><span data-stu-id="45390-122">Searches a package source using a package ID or keywords.</span></span> | <span data-ttu-id="45390-123">3.0+</span><span class="sxs-lookup"><span data-stu-id="45390-123">3.0+</span></span> |
| [<span data-ttu-id="45390-124">Get-Package</span><span class="sxs-lookup"><span data-stu-id="45390-124">Get-Package</span></span>](ps-ref-get-package.md) | <span data-ttu-id="45390-125">Возвращает список пакетов, установленных в локальном хранилище или список пакетов из исходного пакета.</span><span class="sxs-lookup"><span data-stu-id="45390-125">Retrieves the list of packages installed in the local repository, or lists packages available from a package source.</span></span> | <span data-ttu-id="45390-126">Все</span><span class="sxs-lookup"><span data-stu-id="45390-126">All</span></span> |

| <span data-ttu-id="45390-127">Дополнительные команды</span><span class="sxs-lookup"><span data-stu-id="45390-127">Secondary Commands</span></span> | <span data-ttu-id="45390-128">Описание</span><span class="sxs-lookup"><span data-stu-id="45390-128">Description</span></span> | <span data-ttu-id="45390-129">Версия NuGet</span><span class="sxs-lookup"><span data-stu-id="45390-129">NuGet Version</span></span> |
| --- | --- | --- |
| [<span data-ttu-id="45390-130">Добавить BindingRedirect</span><span class="sxs-lookup"><span data-stu-id="45390-130">Add-BindingRedirect</span></span>](ps-ref-add-bindingredirect.md) | <span data-ttu-id="45390-131">Проверяет все сборки по пути вывода для проекта и добавляет перенаправления привязки `app.config` или `web.config` при необходимости.</span><span class="sxs-lookup"><span data-stu-id="45390-131">Examines all assemblies within the output path for a project and adds binding redirects to the `app.config` or `web.config` where necessary.</span></span> | <span data-ttu-id="45390-132">Все</span><span class="sxs-lookup"><span data-stu-id="45390-132">All</span></span> |
| [<span data-ttu-id="45390-133">Get проект</span><span class="sxs-lookup"><span data-stu-id="45390-133">Get-Project</span></span>](ps-ref-get-project.md) | <span data-ttu-id="45390-134">Отображает сведения о значения по умолчанию или указанный проект.</span><span class="sxs-lookup"><span data-stu-id="45390-134">Displays information about the default or specified project.</span></span> | <span data-ttu-id="45390-135">3.0+</span><span class="sxs-lookup"><span data-stu-id="45390-135">3.0+</span></span> |
| [<span data-ttu-id="45390-136">Откройте PackagePage</span><span class="sxs-lookup"><span data-stu-id="45390-136">Open-PackagePage</span></span>](ps-ref-open-packagepage.md) | <span data-ttu-id="45390-137">Запускает браузер по умолчанию проекта, лицензии или URL-адрес отчетов о нарушении для указанного пакета.</span><span class="sxs-lookup"><span data-stu-id="45390-137">Launches the default browser with the project, license, or report abuse URL for the specified package.</span></span> | <span data-ttu-id="45390-138">Рекомендуется использовать в 3.0 +</span><span class="sxs-lookup"><span data-stu-id="45390-138">Deprecated in 3.0+</span></span> |
| [<span data-ttu-id="45390-139">TabExpansion регистра</span><span class="sxs-lookup"><span data-stu-id="45390-139">Register-TabExpansion</span></span>](ps-ref-register-tabexpansion.md) | <span data-ttu-id="45390-140">Регистрирует расширение по клавише tab для параметров команды, что позволяет создавать пользовательские расширения для значения часто используемых параметров.</span><span class="sxs-lookup"><span data-stu-id="45390-140">Registers a tab expansion for the parameters of a command, allowing you to create customized expansions for commonly-used parameter values.</span></span> | <span data-ttu-id="45390-141">Все</span><span class="sxs-lookup"><span data-stu-id="45390-141">All</span></span> |
| [<span data-ttu-id="45390-142">Синхронизация пакета</span><span class="sxs-lookup"><span data-stu-id="45390-142">Sync-Package</span></span>](ps-ref-sync-package.md) | <span data-ttu-id="45390-143">Get, установленная версия пакета из указанного проекта и синхронизируется с остальными проектами в решении.</span><span class="sxs-lookup"><span data-stu-id="45390-143">Get the version of installed package from specified project and syncs the version to the rest of projects in the solution.</span></span> | <span data-ttu-id="45390-144">3.0+</span><span class="sxs-lookup"><span data-stu-id="45390-144">3.0+</span></span> |
| [<span data-ttu-id="45390-145">Удаление пакета</span><span class="sxs-lookup"><span data-stu-id="45390-145">Uninstall-Package</span></span>](ps-ref-uninstall-package.md) | <span data-ttu-id="45390-146">Удаляет пакет из проекта, при необходимости удаления его зависимости.</span><span class="sxs-lookup"><span data-stu-id="45390-146">Removes a package from a project, optionally removing its dependencies.</span></span> | <span data-ttu-id="45390-147">Все</span><span class="sxs-lookup"><span data-stu-id="45390-147">All</span></span> |

<span data-ttu-id="45390-148">Полные и подробные справочные сведения о любой из этих команд в консоли выполните следующую команду с именем команды в вопросе.</span><span class="sxs-lookup"><span data-stu-id="45390-148">For complete, detailed help on any of these commands within the console, just run the following with the command name in question:</span></span>

```ps
Get-Help <command> -full
```

<span data-ttu-id="45390-149">Все консоли диспетчера пакетов команды поддерживает следующие [Общие параметры PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216):</span><span class="sxs-lookup"><span data-stu-id="45390-149">All Package Manager Console commands support the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216):</span></span>

- <span data-ttu-id="45390-150">Отладка</span><span class="sxs-lookup"><span data-stu-id="45390-150">Debug</span></span>
- <span data-ttu-id="45390-151">ErrorAction</span><span class="sxs-lookup"><span data-stu-id="45390-151">ErrorAction</span></span>
- <span data-ttu-id="45390-152">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="45390-152">ErrorVariable</span></span>
- <span data-ttu-id="45390-153">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="45390-153">OutBuffer</span></span>
- <span data-ttu-id="45390-154">OutVariable</span><span class="sxs-lookup"><span data-stu-id="45390-154">OutVariable</span></span>
- <span data-ttu-id="45390-155">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="45390-155">PipelineVariable</span></span>
- <span data-ttu-id="45390-156">Verbose</span><span class="sxs-lookup"><span data-stu-id="45390-156">Verbose</span></span>
- <span data-ttu-id="45390-157">WarningAction</span><span class="sxs-lookup"><span data-stu-id="45390-157">WarningAction</span></span>
- <span data-ttu-id="45390-158">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="45390-158">WarningVariable</span></span>

<span data-ttu-id="45390-159">Дополнительные сведения см. в [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216) в документации по PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45390-159">For details, refer to [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216) in the PowerShell documentation.</span></span>