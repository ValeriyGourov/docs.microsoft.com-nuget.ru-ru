---
title: "Файл project.json NuGet и проекты UWP | Документы Майкрософт"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 7/17/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 37caf4d7-dabd-4a78-aad2-7d445f818457
description: "Сведения об использовании файла project.json для отслеживания зависимостей NuGet в проектах универсальной платформы Windows (UWP)."
keywords: "зависимости NuGet, NuGet и UWP, UWP и project.json, файл project.json NuGet"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: ae49c017365e1a63622fde318d5c94b64ed1ea2e
ms.sourcegitcommit: a40c1c1cc05a46410f317a72f695ad1d80f39fa2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="projectjson-and-uwp"></a><span data-ttu-id="175ad-104">project.json и UWP</span><span class="sxs-lookup"><span data-stu-id="175ad-104">project.json and UWP</span></span>

<span data-ttu-id="175ad-105">Этот документ описывает структуру пакета, в которой используются функции NuGet 3+ (Visual Studio 2015 и более поздних версий).</span><span class="sxs-lookup"><span data-stu-id="175ad-105">This document describes the package structure that employs features in NuGet 3+ (Visual Studio 2015 and later).</span></span> <span data-ttu-id="175ad-106">Задав для свойства `minClientVersion` вашего `.nuspec` значение 3.1, вы можете указать потребность в описанных здесь функциях.</span><span class="sxs-lookup"><span data-stu-id="175ad-106">The `minClientVersion` property of your `.nuspec` can be used to state that you require the features described here by setting it to 3.1.</span></span>

## <a name="adding-uwp-support-to-an-existing-package"></a><span data-ttu-id="175ad-107">Добавление поддержки UWP для существующего пакета</span><span class="sxs-lookup"><span data-stu-id="175ad-107">Adding UWP support to an existing package</span></span>

<span data-ttu-id="175ad-108">Если у вас есть пакет и вы хотите добавить поддержку приложений UWP, то вам не нужно внедрять описанный здесь формат упаковки.</span><span class="sxs-lookup"><span data-stu-id="175ad-108">If you have an existing package and you want to add support for UWP applications, then you don’t need to adopt the  packaging format described here.</span></span> <span data-ttu-id="175ad-109">Это требуется только в том случае, если вы нуждаетесь в описанных в этом формате функциях и хотите работать только с клиентами, которые были обновлены до версии 3+ клиента NuGet.</span><span class="sxs-lookup"><span data-stu-id="175ad-109">You only need to adopt this format if you require the features it describes and are willing to  work only with clients that have updated to version 3+ of the NuGet client.</span></span>

## <a name="i-already-target-netcore45"></a><span data-ttu-id="175ad-110">Я уже ориентируюсь на netcore45</span><span class="sxs-lookup"><span data-stu-id="175ad-110">I already target netcore45</span></span>

<span data-ttu-id="175ad-111">Если вы уже ориентируетесь на `netcore45` и не хотите воспользоваться преимуществами описанных здесь функций, никаких действий не требуется.</span><span class="sxs-lookup"><span data-stu-id="175ad-111">If you target `netcore45` already, and you don’t need to take advantage of the features here, no action is needed.</span></span> <span data-ttu-id="175ad-112">Пакеты `netcore45` могут использоваться в приложениях UWP.</span><span class="sxs-lookup"><span data-stu-id="175ad-112">`netcore45` packages can be consumed by UWP applications.</span></span>

## <a name="i-want-to-take-advantage-of-windows-10-specific-apis"></a><span data-ttu-id="175ad-113">Я хочу использовать преимущества конкретных API для Windows 10</span><span class="sxs-lookup"><span data-stu-id="175ad-113">I want to take advantage of Windows 10 specific APIs</span></span>

<span data-ttu-id="175ad-114">В этом случае вам нужно добавить в пакет моникер целевой платформы `uap10.0` (TFM или TxM).</span><span class="sxs-lookup"><span data-stu-id="175ad-114">In this case you need to add the `uap10.0` target framework moniker (TFM or TxM) to your package.</span></span> <span data-ttu-id="175ad-115">Создайте в пакете папку и добавьте в нее сборку, скомпилированную для работы с Windows 10.</span><span class="sxs-lookup"><span data-stu-id="175ad-115">Create a new folder in your package and add the assembly that has been compiled to work with Windows 10 to that folder.</span></span>

## <a name="i-dont-need-windows-10-specific-apis-but-want-new-net-features-or-dont-have-netcore45-already"></a><span data-ttu-id="175ad-116">Мне не нужны конкретные API для Windows 10, но требуются новые возможности .NET, либо у меня еще нет netcore45</span><span class="sxs-lookup"><span data-stu-id="175ad-116">I don’t need Windows 10 specific APIs, but want new .NET features or don’t have netcore45 already</span></span>

<span data-ttu-id="175ad-117">В этом случае нужно добавить TxM `dotnet` в пакет.</span><span class="sxs-lookup"><span data-stu-id="175ad-117">In this case you would add the `dotnet` TxM to your package.</span></span> <span data-ttu-id="175ad-118">В отличие от других TxM, `dotnet` не подразумевает контактную зону или платформу.</span><span class="sxs-lookup"><span data-stu-id="175ad-118">Unlike other TxMs, `dotnet` doesn't imply a surface area or platform.</span></span> <span data-ttu-id="175ad-119">Он определяет, что ваш пакет работает на любой платформе, где работают ваши зависимости.</span><span class="sxs-lookup"><span data-stu-id="175ad-119">It is stating that your package works on any platform that your dependencies work on.</span></span> <span data-ttu-id="175ad-120">При сборке пакета с TxM `dotnet` вы, скорее всего, используете значительно больше зависимостей, связанных с TxM, в вашем `.nuspec`, так как нужно определить пакеты BCL, от которых вы зависите, например `System.Text`, `System.Xml` и т. д. Расположения, где работают эти зависимости, определяют рабочую область вашего пакета.</span><span class="sxs-lookup"><span data-stu-id="175ad-120">When building a package with the `dotnet` TxM, you are likely to have many more TxM-specific dependencies in your `.nuspec`, as you need to define the BCL packages you depend on, such `System.Text`, `System.Xml`, etc. The locations that those dependencies work on define where your package works.</span></span>

### <a name="how-do-i-find-out-my-dependencies"></a><span data-ttu-id="175ad-121">Как узнать свои зависимости</span><span class="sxs-lookup"><span data-stu-id="175ad-121">How do I find out my dependencies</span></span>

<span data-ttu-id="175ad-122">Понять, какие зависимости указывать, можно двумя способами:</span><span class="sxs-lookup"><span data-stu-id="175ad-122">There are two ways to figure out which dependencies to list:</span></span>

1. <span data-ttu-id="175ad-123">Используйте средство [NuSpec Dependency Generator](https://github.com/onovotny/ReferenceGenerator) **стороннего разработчика**.</span><span class="sxs-lookup"><span data-stu-id="175ad-123">Use the [NuSpec Dependency Generator](https://github.com/onovotny/ReferenceGenerator) **3rd party** tool.</span></span> <span data-ttu-id="175ad-124">Оно автоматизирует процесс и обновляет ваш файл `.nuspec` с использованием зависимых пакетов при сборке.</span><span class="sxs-lookup"><span data-stu-id="175ad-124">The tool automates the process and updates your `.nuspec` file with the dependant packages on build.</span></span> <span data-ttu-id="175ad-125">Это средство доступно в виде пакета NuGet [NuSpec.ReferenceGenerator](https://www.nuget.org/packages/NuSpec.ReferenceGenerator/).</span><span class="sxs-lookup"><span data-stu-id="175ad-125">It is available via a NuGet package, [NuSpec.ReferenceGenerator](https://www.nuget.org/packages/NuSpec.ReferenceGenerator/).</span></span>
2. <span data-ttu-id="175ad-126">Используйте `ILDasm` для просмотра вашей `.dll`, чтобы узнать, какие сборки действительно нужны во время выполнения (для тех, кто не ищет легких путей).</span><span class="sxs-lookup"><span data-stu-id="175ad-126">(The hard way) Use `ILDasm` to look at your `.dll` to see what assemblies are actually needed at runtime.</span></span> <span data-ttu-id="175ad-127">После этого определите, к какому пакету NuGet относится каждая из них.</span><span class="sxs-lookup"><span data-stu-id="175ad-127">Then determine which NuGet package they each come from.</span></span>

<span data-ttu-id="175ad-128">Дополнительные сведения о функциях, которые помогают создавать пакеты, поддерживающие TxM `dotnet`, см .в разделе [`project.json`](../Schema/project-json.md).</span><span class="sxs-lookup"><span data-stu-id="175ad-128">See the [`project.json`](../Schema/project-json.md) topic for details on features that help in the creation of a package that supports the `dotnet` TxM.</span></span>

> [!Important]
> <span data-ttu-id="175ad-129">Если ваш пакет предназначен для работы с проектами PCL, настоятельно рекомендуется создать папку `dotnet`, чтобы избежать предупреждений и потенциальных проблем совместимости.</span><span class="sxs-lookup"><span data-stu-id="175ad-129">If your package is intended to work with PCL projects, we highly recommend to create a `dotnet` folder, to avoid warnings and potential compatibility issues.</span></span>


## <a name="directory-structure"></a><span data-ttu-id="175ad-130">Структура каталогов</span><span class="sxs-lookup"><span data-stu-id="175ad-130">Directory structure</span></span>

<span data-ttu-id="175ad-131">Пакеты NuGet, использующие этот формат, имеют следующие стандартные папки и поведения:</span><span class="sxs-lookup"><span data-stu-id="175ad-131">NuGet packages using this format have the following well-known folder and behaviors:</span></span>

| <span data-ttu-id="175ad-132">Папка</span><span class="sxs-lookup"><span data-stu-id="175ad-132">Folder</span></span> | <span data-ttu-id="175ad-133">поведения</span><span class="sxs-lookup"><span data-stu-id="175ad-133">Behaviors</span></span> |
| --- | --- |
| <span data-ttu-id="175ad-134">Построить</span><span class="sxs-lookup"><span data-stu-id="175ad-134">Build</span></span> | <span data-ttu-id="175ad-135">Файлы свойств и целевых объектов MSBuild в этой папке интегрируются в проект по-разному, в противном случае изменения отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="175ad-135">Contains MSBuild targets and props files in this folder are integrated differently into the project, but otherwise there is no change.</span></span> |
| <span data-ttu-id="175ad-136">Инструменты</span><span class="sxs-lookup"><span data-stu-id="175ad-136">Tools</span></span> | <span data-ttu-id="175ad-137">`install.ps1` и `uninstall.ps1` не выполняются.</span><span class="sxs-lookup"><span data-stu-id="175ad-137">`install.ps1` and `uninstall.ps1` are not run.</span></span> <span data-ttu-id="175ad-138">`init.ps1` работает обычным образом.</span><span class="sxs-lookup"><span data-stu-id="175ad-138">`init.ps1` works as it always has.</span></span> |
| <span data-ttu-id="175ad-139">Content</span><span class="sxs-lookup"><span data-stu-id="175ad-139">Content</span></span> | <span data-ttu-id="175ad-140">Содержимое не копируется в проект пользователя автоматически.</span><span class="sxs-lookup"><span data-stu-id="175ad-140">Content is not copied automatically into a user's project.</span></span> <span data-ttu-id="175ad-141">Поддержка для включения содержимого в проект запланирована в будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="175ad-141">Support for content inclusion in the project is planned for a later release.</span></span> |
| <span data-ttu-id="175ad-142">LIB</span><span class="sxs-lookup"><span data-stu-id="175ad-142">Lib</span></span> | <span data-ttu-id="175ad-143">Для множества пакетов `lib` работает так же, как и в NuGet 2.x, но для нее были расширены варианты имен, которые можно использовать внутри этой папки, а также доработана логика для выбора подходящей вложенной папки при использовании пакетов.</span><span class="sxs-lookup"><span data-stu-id="175ad-143">For many packages the `lib` works the same way it does in NuGet 2.x, but with expanded options for what names can be used inside it and better logic for picking the correct sub-folder when consuming packages.</span></span> <span data-ttu-id="175ad-144">Однако при использовании в сочетании с `ref` папка `lib` содержит сборки, реализующие контактную зону, которая определяется сборками в папке `ref`.</span><span class="sxs-lookup"><span data-stu-id="175ad-144">However, when used in conjunction with `ref`, the `lib` folder contains assemblies that implement the surface area defined by the assemblies in the `ref` folder.</span></span> |
| <span data-ttu-id="175ad-145">Ссылочный</span><span class="sxs-lookup"><span data-stu-id="175ad-145">Ref</span></span> | <span data-ttu-id="175ad-146">`ref` — это необязательная папка, которая содержит сборки .NET, определяющие общедоступную область (общие типы и методы), используемую при компиляции приложения.</span><span class="sxs-lookup"><span data-stu-id="175ad-146">`ref` is an optional folder that contains .NET assemblies defining the public surface (public types and methods) for an application to compile against.</span></span> <span data-ttu-id="175ad-147">Сборки в этой папке могут не иметь реализации, они используются исключительно в целях определения контактной зоны для компилятора.</span><span class="sxs-lookup"><span data-stu-id="175ad-147">The assemblies in this folder may have no implementation, they are purely used to define surface area for the compiler.</span></span> <span data-ttu-id="175ad-148">Если пакет не содержит папку `ref`, то `lib` является как базовой сборкой, так и сборкой реализации.</span><span class="sxs-lookup"><span data-stu-id="175ad-148">If the package has no `ref` folder, then the `lib` is both the reference assembly and the implementation assembly.</span></span> |
| <span data-ttu-id="175ad-149">Runtimes</span><span class="sxs-lookup"><span data-stu-id="175ad-149">Runtimes</span></span> | <span data-ttu-id="175ad-150">`runtimes` — это необязательная папка, которая содержит код для операционной системы, например для архитектуры ЦП и зависящих от операционной системы или платформы двоичных файлов.</span><span class="sxs-lookup"><span data-stu-id="175ad-150">`runtimes` is an optional folder that contains OS specific code, such as CPU architecture and OS specific or otherwise platform-dependent binaries.</span></span> |


## <a name="msbuild-targets-and-props-files-in-packages"></a><span data-ttu-id="175ad-151">Файлы целевых объектов и свойств MSBuild в пакетах</span><span class="sxs-lookup"><span data-stu-id="175ad-151">MSBuild targets and props files in packages</span></span>

<span data-ttu-id="175ad-152">Пакеты NuGet могут содержать файлы `.targets` и `.props` файлов, которые импортируются в любой проект MSBuild, где устанавливается пакет.</span><span class="sxs-lookup"><span data-stu-id="175ad-152">NuGet packages can contain `.targets` and `.props` files which are imported into any MSBuild project that the package is installed into.</span></span> <span data-ttu-id="175ad-153">В NuGet 2.x это осуществлялось путем внедрения операторов `<Import>` в файл `.csproj`, в NuGet 3.0 конкретное действие по установке в проект отсутствует.</span><span class="sxs-lookup"><span data-stu-id="175ad-153">In NuGet 2.x, this was done by injecting `<Import>` statements into the `.csproj` file, in NuGet 3.0 there is no specific "installation to project" action.</span></span> <span data-ttu-id="175ad-154">Вместо этого процесс восстановления пакета записывает два файла — `[projectname].nuget.props` и `[projectname].NuGet.targets`.</span><span class="sxs-lookup"><span data-stu-id="175ad-154">Instead the package restore process writes two files `[projectname].nuget.props` and `[projectname].NuGet.targets`.</span></span>

<span data-ttu-id="175ad-155">MSBuild ищет эти файлы и автоматически импортирует их в начале и в конце процесса сборки проекта.</span><span class="sxs-lookup"><span data-stu-id="175ad-155">MSBuild knows to look for these two files and automatically imports them near the beginning and near the end of the project build process.</span></span> <span data-ttu-id="175ad-156">Это поведение во многом аналогично NuGet 2.x, но одно из основных отличий заключается в том, что *в этом случае отсутствует гарантированный порядок файлов целевых объектов и свойств*.</span><span class="sxs-lookup"><span data-stu-id="175ad-156">This provides very similar behavior to NuGet 2.x, but with one major difference: *there is no guaranteed order of targets/props files in this case*.</span></span> <span data-ttu-id="175ad-157">Однако MSBuild позволяет упорядочить целевые объекты с помощью атрибутов `BeforeTargets` и `AfterTargets` определения `<Target>` (см. раздел [Элемент Target (MSBuild)](/visualstudio/msbuild/target-element-msbuild).</span><span class="sxs-lookup"><span data-stu-id="175ad-157">However, MSBuild does provide ways to order targets through the `BeforeTargets` and `AfterTargets` attributes of the `<Target>` definition (see [Target Element (MSBuild)](/visualstudio/msbuild/target-element-msbuild).</span></span>


## <a name="lib-and-ref"></a><span data-ttu-id="175ad-158">Lib и Ref</span><span class="sxs-lookup"><span data-stu-id="175ad-158">Lib and Ref</span></span>

<span data-ttu-id="175ad-159">В NuGet 3 поведение папки `lib` изменилось мало.</span><span class="sxs-lookup"><span data-stu-id="175ad-159">The behavior of the `lib` folder hasn't changed significantly in NuGet v3.</span></span> <span data-ttu-id="175ad-160">Однако все сборки должны находиться во вложенных папках, названных согласно TxM, и больше не могут находиться прямо в папке `lib`.</span><span class="sxs-lookup"><span data-stu-id="175ad-160">However, all assemblies must be within sub-folders named after a TxM, and can no longer be placed directly under the `lib` folder.</span></span> <span data-ttu-id="175ad-161">TxM — это название платформы, с которой должен работать заданный ресурс в пакете.</span><span class="sxs-lookup"><span data-stu-id="175ad-161">A TxM is the name of a platform that a given asset in a package is supposed to work for.</span></span> <span data-ttu-id="175ad-162">Логически это расширение моникеров целевой платформы (TFM), например `net45`, `net46`, `netcore50` и `dnxcore50` являются примерами TxM (см. раздел [Целевые платформы](../Schema/Target-Frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="175ad-162">Logically these are an extension of the Target Framework Monikers (TFM) e.g. `net45`, `net46`, `netcore50`, and `dnxcore50` are all examples of TxMs (see [Target Frameworks](../Schema/Target-Frameworks.md).</span></span> <span data-ttu-id="175ad-163">TxM может ссылаться на платформу (TFM), а также на другие контактные зоны конкретных платформ.</span><span class="sxs-lookup"><span data-stu-id="175ad-163">TxM can refer to a framework (TFM) as well as other platform-specific surface areas.</span></span> <span data-ttu-id="175ad-164">Например, TxM UWP (`uap10.0`) представляет контактную зону .NET, а также контактную зону Windows для приложений UWP.</span><span class="sxs-lookup"><span data-stu-id="175ad-164">For example the UWP TxM (`uap10.0`) represents the .NET surface area as well as the Windows surface area for UWP applications.</span></span>

<span data-ttu-id="175ad-165">Пример структуры lib:</span><span class="sxs-lookup"><span data-stu-id="175ad-165">An example lib structure:</span></span>

    lib
    ├───net40
    │       MyLibrary.dll
    └───wp81
            MyLibrary.dll

<span data-ttu-id="175ad-166">Папка `lib` содержит сборки, используемые во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="175ad-166">The `lib` folder contains assemblies that are used at runtime.</span></span> <span data-ttu-id="175ad-167">Для большинства пакетов для каждого из целевых TxM требуется только папка в `lib`.</span><span class="sxs-lookup"><span data-stu-id="175ad-167">For most packages a folder under `lib` for each of the target TxMs is all that is required.</span></span>

## <a name="ref"></a><span data-ttu-id="175ad-168">Ссылочный</span><span class="sxs-lookup"><span data-stu-id="175ad-168">Ref</span></span>

<span data-ttu-id="175ad-169">Иногда во время компиляции требуется использовать другую сборку (сейчас за это отвечают базовые сборки .NET).</span><span class="sxs-lookup"><span data-stu-id="175ad-169">There are sometimes cases where a different assembly should be used during compilation (.NET Reference Assemblies do this today).</span></span> <span data-ttu-id="175ad-170">В этих случаях используйте папку верхнего уровня с именем `ref` (сокращенное обозначение базовых сборок).</span><span class="sxs-lookup"><span data-stu-id="175ad-170">For those cases, use a top-level folder called `ref` (short for "Reference Assemblies").</span></span>

<span data-ttu-id="175ad-171">Большинству создателей пакетов папка `ref` не требуется.</span><span class="sxs-lookup"><span data-stu-id="175ad-171">Most package authors don't require the `ref` folder.</span></span> <span data-ttu-id="175ad-172">Она удобна для пакетов, которые должны обеспечивать согласованную контактную зону для компиляции и IntelliSense, однако имеют разные реализации разных TxM.</span><span class="sxs-lookup"><span data-stu-id="175ad-172">It is useful for packages that need to provide a consistent surface area for compilation and IntelliSense but then have different implementation for different TxMs.</span></span> <span data-ttu-id="175ad-173">Основным ее вариантом использования являются пакеты `System.*`, создаваемые в процессе доставки .NET Core в NuGet.</span><span class="sxs-lookup"><span data-stu-id="175ad-173">The biggest use case of this are the `System.*` packages that are being produced as part of shipping .NET Core on NuGet.</span></span> <span data-ttu-id="175ad-174">Они имеют различные реализации, которые унифицируются с помощью согласованного набора базовых сборок.</span><span class="sxs-lookup"><span data-stu-id="175ad-174">These packages have various implementations that are being unified by a consistent set of ref assemblies.</span></span>

<span data-ttu-id="175ad-175">Технически включенные в папку `ref` сборки — это базовые сборки, передаваемые компилятору.</span><span class="sxs-lookup"><span data-stu-id="175ad-175">Mechanically, the assemblies included in the `ref` folder are the reference assemblies being passed to the compiler.</span></span> <span data-ttu-id="175ad-176">Для тех, кто использовал csc.exe, это сборки, которые мы передаем в параметр [/reference C#](/dotnet/articles/csharp/language-reference/compiler-options/reference-compiler-option).</span><span class="sxs-lookup"><span data-stu-id="175ad-176">For those of you who have used csc.exe these are the assemblies we are passing to the [C# /reference option](/dotnet/articles/csharp/language-reference/compiler-options/reference-compiler-option) switch.</span></span>

<span data-ttu-id="175ad-177">Структура папки `ref` аналогична `lib`, например:</span><span class="sxs-lookup"><span data-stu-id="175ad-177">The structure of the `ref` folder is the same as `lib`, for example:</span></span>

    └───MyImageProcessingLib
         ├───lib
         │   ├───net40
         │   │       MyImageProcessingLibrary.dll
         │   │
         │   ├───net451
         │   │       MyImageProcessingLibrary.dll
         │   │
         │   └───win81
         │           MyImageProcessingLibrary.dll
         │
         └───ref
             ├───net40
             │       MyImageProcessingLibrary.dll
             │
             └───portable-net451-win81
                     MyImageProcessingLibrary.dll


<span data-ttu-id="175ad-178">Здесь все сборки в каталогах `ref` были бы одинаковыми.</span><span class="sxs-lookup"><span data-stu-id="175ad-178">In this example the assemblies in the `ref` directories would all be identical.</span></span>


## <a name="runtimes"></a><span data-ttu-id="175ad-179">Runtimes</span><span class="sxs-lookup"><span data-stu-id="175ad-179">Runtimes</span></span>

<span data-ttu-id="175ad-180">Папка "runtimes" содержит сборки и собственные библиотеки, необходимые для запуска в конкретных средах выполнения, которые обычно определяются операционной системой и архитектурой ЦП.</span><span class="sxs-lookup"><span data-stu-id="175ad-180">The runtimes folder contains assemblies and native libraries required to run on specific "runtimes", which are generally defined by Operating System and CPU architecture.</span></span> <span data-ttu-id="175ad-181">Эти среды выполнения описываются [идентификаторами среды выполнения (RID)](/dotnet/core/rid-catalog), такими как `win`, `win-x86`, `win7-x86`, `win8-64` и т. д.</span><span class="sxs-lookup"><span data-stu-id="175ad-181">These runtimes are identified using [Runtime Identifiers (RIDs)](/dotnet/core/rid-catalog) such as `win`, `win-x86`, `win7-x86`, `win8-64`, etc.</span></span>

## <a name="native-light-up"></a><span data-ttu-id="175ad-182">Сведения о машинном коде</span><span class="sxs-lookup"><span data-stu-id="175ad-182">Native light-up</span></span>

<span data-ttu-id="175ad-183">В следующем примере показан пакет, имеющий реализацию только из управляемого кода для нескольких платформ, но использующий собственные вспомогательные приложения в Windows 8, где он может вызывать собственные API для Windows 8.</span><span class="sxs-lookup"><span data-stu-id="175ad-183">The following example shows a package that has a purely managed implementation for several platforms, but uses native helpers on Windows 8 where it can call into Windows 8-specific native APIs.</span></span>

    └───MyLibrary
         ├───lib
         │   └───net40
         │           MyLibrary.dll
         │
         └───runtimes
             ├───win8-x64
             │   ├───lib
             │   │   └───net40
             │   │           MyLibrary.dll
             │   │
             │   └───native
             │           MyNativeLibrary.dll
             │
             └───win8-x86
                 ├───lib
                 │   └───net40
                 │           MyLibrary.dll
                 │
                 └───native
                         MyNativeLibrary.dll

<span data-ttu-id="175ad-184">Для указанного выше пакета выполняется следующее:</span><span class="sxs-lookup"><span data-stu-id="175ad-184">Given the above package the following things happen:</span></span>

- <span data-ttu-id="175ad-185">Если работа ведется не в Windows 8, используется сборка `lib/net40/MyLibrary.dll`.</span><span class="sxs-lookup"><span data-stu-id="175ad-185">When not on Windows 8 the `lib/net40/MyLibrary.dll` assembly is used.</span></span>

- <span data-ttu-id="175ad-186">Если работа ведется в Windows 8, используется `runtimes/win8-<architecture>/lib/MyLibrary.dll`, а `native/MyNativeHelper.dll` копируется в выходные данные сборки.</span><span class="sxs-lookup"><span data-stu-id="175ad-186">When on Windows 8 the `runtimes/win8-<architecture>/lib/MyLibrary.dll` is used and the `native/MyNativeHelper.dll` is copied to the output of your build.</span></span>

<span data-ttu-id="175ad-187">В приведенном выше примере сборка `lib/net40` состоит исключительно из управляемого кода, а сборки в папке "runtimes" будут вызывать неуправляемый код для сборки собственного вспомогательного приложения, чтобы вызвать API, относящиеся к Windows 8.</span><span class="sxs-lookup"><span data-stu-id="175ad-187">In the example above the `lib/net40` assembly is purely managed code, whilst the assemblies in the runtimes folder will p/invoke into the native helper assembly to call APIs specific to Windows 8.</span></span>

<span data-ttu-id="175ad-188">Вы можете выбрать только одну папку `lib`, поэтому при наличии конкретной папки для среды выполнения выбирается именно она вместо папки `lib`, не относящейся ни к какой среде.</span><span class="sxs-lookup"><span data-stu-id="175ad-188">Only a single `lib` folder is ever be picked, so if there is a runtime specific folder it's chosen over non-runtime specific `lib`.</span></span> <span data-ttu-id="175ad-189">Собственная папка является аддитивной, при ее наличии она копируется в выходные данные сборки.</span><span class="sxs-lookup"><span data-stu-id="175ad-189">The native folder is additive, if it exists it's copied to the output of the build.</span></span>

## <a name="managed-wrapper"></a><span data-ttu-id="175ad-190">Управляемая оболочка</span><span class="sxs-lookup"><span data-stu-id="175ad-190">Managed wrapper</span></span>

<span data-ttu-id="175ad-191">Другой способ использования среды выполнения заключается в поставке пакета, который представляет собой оболочку, состоящую исключительно из управляемого кода, вместо сборки в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="175ad-191">Another way to use runtimes is to ship a package that is purely a managed wrapper over a native assembly.</span></span> <span data-ttu-id="175ad-192">В этом сценарии вы создаете следующий пакет:</span><span class="sxs-lookup"><span data-stu-id="175ad-192">In this scenario you create a package like the following:</span></span>

    └───MyLibrary
         └───runtimes
             ├───win8-x64
             │   ├───lib
             │   │   └───net451
             │   │           MyLibrary.dll
             │   │
             │   └───native
             │           MyImplementation.dll
             │
             └───win8-x86
                 ├───lib
                 │   └───net451
                 │           MyLibrary.dll
                 │
                 └───native
                         MyImplementation.dll

<span data-ttu-id="175ad-193">Здесь папка верхнего уровня `lib` отсутствует, так как нет реализации этого пакета, которая не зависит от соответствующей машинной сборки.</span><span class="sxs-lookup"><span data-stu-id="175ad-193">In this case there is no top-level `lib` folder as that folder as there is no implementation of this package that doesn't rely on the corresponding native assembly.</span></span> <span data-ttu-id="175ad-194">Если бы управляемая сборка `MyLibrary.dll` была одинаковой в обоих случаях, можно было бы поместить ее в папку `lib` верхнего уровня, но из-за отсутствия машинной сборки не возникает ошибка при установке пакета на платформе, отличной от win-x86 и win-x64, а также использовалась бы папка "lib" верхнего уровня, однако машинная сборка не копировалась бы.</span><span class="sxs-lookup"><span data-stu-id="175ad-194">If the managed assembly, `MyLibrary.dll`, was exactly the same in both of these cases then we could put it in a top level `lib` folder, but because the lack of a native assembly doesn't cause the package to fail installing if it was installed on a platform that wasn't win-x86 or win-x64 then the top level lib would be used but no native assembly would be copied.</span></span>


## <a name="authoring-packages-for-nuget-2-and-nuget-3"></a><span data-ttu-id="175ad-195">Создание пакетов для NuGet 2 и NuGet 3</span><span class="sxs-lookup"><span data-stu-id="175ad-195">Authoring packages for NuGet 2 and NuGet 3</span></span>

<span data-ttu-id="175ad-196">Если вы хотите создать пакет, который могут использовать проекты, использующие `packages.config`, а также пакеты, использующие `project.json`, применяются следующие условия:</span><span class="sxs-lookup"><span data-stu-id="175ad-196">If you want to create a package that can be consumed by projects using `packages.config` as well as packages using `project.json` then the following apply:</span></span>

- <span data-ttu-id="175ad-197">Папки "ref" и "runtimes" работают только в NuGet 3.</span><span class="sxs-lookup"><span data-stu-id="175ad-197">Ref and runtimes only work on NuGet 3.</span></span> <span data-ttu-id="175ad-198">В NuGet 2 обе они игнорируются.</span><span class="sxs-lookup"><span data-stu-id="175ad-198">They are both ignored by NuGet 2.</span></span>

- <span data-ttu-id="175ad-199">Невозможно полагаться на работу `install.ps1` или `uninstall.ps1`.</span><span class="sxs-lookup"><span data-stu-id="175ad-199">You cannot rely on `install.ps1` or `uninstall.ps1` to function.</span></span> <span data-ttu-id="175ad-200">Эти файлы выполняются при использовании `packages.config`, однако игнорируются при `project.json`.</span><span class="sxs-lookup"><span data-stu-id="175ad-200">These files execute when using `packages.config`, but are ignored with `project.json`.</span></span> <span data-ttu-id="175ad-201">Поэтому пакет должен работать без них.</span><span class="sxs-lookup"><span data-stu-id="175ad-201">So your package needs to be usable without them running.</span></span> <span data-ttu-id="175ad-202">`init.ps1` по-прежнему выполняется на NuGet 3.</span><span class="sxs-lookup"><span data-stu-id="175ad-202">`init.ps1` still runs on NuGet 3.</span></span>

- <span data-ttu-id="175ad-203">Установка целевых объектов и свойств отличается, поэтому убедитесь, что ваш пакет работает правильно для обоих клиентов.</span><span class="sxs-lookup"><span data-stu-id="175ad-203">Targets and Props installation is different, so make sure that your package works as expected on both clients.</span></span>

- <span data-ttu-id="175ad-204">Подкаталоги папки "lib" должны быть TxM в NuGet 3.</span><span class="sxs-lookup"><span data-stu-id="175ad-204">Subdirectories of lib must be a TxM in NuGet 3.</span></span> <span data-ttu-id="175ad-205">Невозможно поместить библиотеки в корень папки `lib`.</span><span class="sxs-lookup"><span data-stu-id="175ad-205">You cannot place libraries at the root of the `lib` folder.</span></span>

- <span data-ttu-id="175ad-206">При использовании NuGet 3 содержимое не копируется автоматически.</span><span class="sxs-lookup"><span data-stu-id="175ad-206">Content is not copied automatically with NuGet 3.</span></span> <span data-ttu-id="175ad-207">Потребители вашего пакета могут скопировать файлы самостоятельно или воспользоваться таким средством, как запускатель задач, чтобы автоматизировать этот процесс.</span><span class="sxs-lookup"><span data-stu-id="175ad-207">Consumers of your package could copy the files themselves or use a tool like a task runner to automate copying the files.</span></span>

- <span data-ttu-id="175ad-208">NuGet 3 не преобразует файлы конфигурации и исходного кода.</span><span class="sxs-lookup"><span data-stu-id="175ad-208">Source and config file transforms are not run by NuGet 3.</span></span>

<span data-ttu-id="175ad-209">Если вы поддерживаете NuGet 2 и 3, то `minClientVersion` должен соответствовать самой ранней версии клиента NuGet 2, с которой работает ваш пакет.</span><span class="sxs-lookup"><span data-stu-id="175ad-209">If you are supporting NuGet 2 and 3 then your `minClientVersion` should be the lowest version of NuGet 2 client that your package works on.</span></span> <span data-ttu-id="175ad-210">При использовании существующего пакета изменять его не требуется.</span><span class="sxs-lookup"><span data-stu-id="175ad-210">In the case of an existing package it shouldn't need to change.</span></span>