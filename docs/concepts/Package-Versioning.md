---
title: Справочник по версиям пакета NuGet
description: Точные сведения об указании номеров и диапазонов версий для других пакетов, от которых зависит пакет NuGet, а также об установке зависимостей.
author: karann-msft
ms.author: karann
ms.date: 03/23/2018
ms.topic: reference
ms.reviewer: anangaur
ms.openlocfilehash: 7c6992d6bf3142eb6aca70f1fa3c46f72efd25a0
ms.sourcegitcommit: 7441f12f06ca380feb87c6192ec69f6108f43ee3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69520354"
---
# <a name="package-versioning"></a><span data-ttu-id="9c42e-103">Управление версиями пакета</span><span class="sxs-lookup"><span data-stu-id="9c42e-103">Package versioning</span></span>

<span data-ttu-id="9c42e-104">При указании определенного пакета всегда используется его идентификатор и точный номер версии.</span><span class="sxs-lookup"><span data-stu-id="9c42e-104">A specific package is always referred to using its package identifier and an exact version number.</span></span> <span data-ttu-id="9c42e-105">Например, для [Entity Framework](https://www.nuget.org/packages/EntityFramework/) на сайте nuget.org доступно несколько десятков специальных пакетов, начиная с версии *4.1.10311* и заканчивая версией *6.1.3* (последний стабильный выпуск), а также множество предварительных версий, таких как *6.2.0-beta1*.</span><span class="sxs-lookup"><span data-stu-id="9c42e-105">For example, [Entity Framework](https://www.nuget.org/packages/EntityFramework/) on nuget.org has several dozen specific packages available, ranging from version *4.1.10311* to version *6.1.3* (the latest stable release) and a variety of pre-release versions like *6.2.0-beta1*.</span></span>

<span data-ttu-id="9c42e-106">При создании пакета вы назначаете определенный номер версии с необязательным текстовым суффиксом предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="9c42e-106">When creating a package, you assign a specific version number with an optional pre-release text suffix.</span></span> <span data-ttu-id="9c42e-107">С другой стороны, при использовании пакетов вы можете указать либо точный номер версии, либо диапазон допустимых версий.</span><span class="sxs-lookup"><span data-stu-id="9c42e-107">When consuming packages, on the other hand, you can specify either an exact version number or a range of acceptable versions.</span></span>

<span data-ttu-id="9c42e-108">В этом разделе.</span><span class="sxs-lookup"><span data-stu-id="9c42e-108">In this topic:</span></span>

- <span data-ttu-id="9c42e-109">[Основные сведения о версиях](#version-basics), включая информацию о суффиксах предварительных версий.</span><span class="sxs-lookup"><span data-stu-id="9c42e-109">[Version basics](#version-basics) including pre-release suffixes.</span></span>
- <span data-ttu-id="9c42e-110">[Диапазоны версий и подстановочные знаки](#version-ranges-and-wildcards).</span><span class="sxs-lookup"><span data-stu-id="9c42e-110">[Version ranges and wildcards](#version-ranges-and-wildcards)</span></span>
- <span data-ttu-id="9c42e-111">[Нормализованные номера версий](#normalized-version-numbers).</span><span class="sxs-lookup"><span data-stu-id="9c42e-111">[Normalized version numbers](#normalized-version-numbers)</span></span>

## <a name="version-basics"></a><span data-ttu-id="9c42e-112">Основные сведения о версиях</span><span class="sxs-lookup"><span data-stu-id="9c42e-112">Version basics</span></span>

<span data-ttu-id="9c42e-113">Номер определенной версии выглядит следующим образом: *Основной номер.Дополнительный номер.Исправление[-Суффикс]* . Компоненты номера имеют следующие значения:</span><span class="sxs-lookup"><span data-stu-id="9c42e-113">A specific version number is in the form *Major.Minor.Patch[-Suffix]*, where the components have the following meanings:</span></span>

- <span data-ttu-id="9c42e-114">*Основной номер*: Критические изменения</span><span class="sxs-lookup"><span data-stu-id="9c42e-114">*Major*: Breaking changes</span></span>
- <span data-ttu-id="9c42e-115">*Дополнительный номер*: новые функции; сохраняется обратная совместимость;</span><span class="sxs-lookup"><span data-stu-id="9c42e-115">*Minor*: New features, but backwards compatible</span></span>
- <span data-ttu-id="9c42e-116">*Исправление*: исправления ошибок; сохраняется обратная совместимость.</span><span class="sxs-lookup"><span data-stu-id="9c42e-116">*Patch*: Backwards compatible bug fixes only</span></span>
- <span data-ttu-id="9c42e-117">*-Суффикс* (необязательно): дефис, за которым следует строка, обозначающая предварительную версию (в соответствии с [Семантическим версионированием (или соглашением SemVer 1.0)](http://semver.org/spec/v1.0.0.html)).</span><span class="sxs-lookup"><span data-stu-id="9c42e-117">*-Suffix* (optional): a hyphen followed by a string denoting a pre-release version (following the [Semantic Versioning or SemVer 1.0 convention](http://semver.org/spec/v1.0.0.html)).</span></span>

<span data-ttu-id="9c42e-118">**Примеры**</span><span class="sxs-lookup"><span data-stu-id="9c42e-118">**Examples:**</span></span>

    1.0.1
    6.11.1231
    4.3.1-rc
    2.2.44-beta1

> [!Important]
> <span data-ttu-id="9c42e-119">nuget.org отклоняет любую загрузку пакета, в которой отсутствует точный номер версии.</span><span class="sxs-lookup"><span data-stu-id="9c42e-119">nuget.org rejects any package upload that lacks an exact version number.</span></span> <span data-ttu-id="9c42e-120">Версия должна быть указана в `.nuspec` или файле проекта, с помощью которого был создан пакет.</span><span class="sxs-lookup"><span data-stu-id="9c42e-120">The version must be specified in the `.nuspec` or project file used to create the package.</span></span>

### <a name="pre-release-versions"></a><span data-ttu-id="9c42e-121">Предварительные версии</span><span class="sxs-lookup"><span data-stu-id="9c42e-121">Pre-release versions</span></span>

<span data-ttu-id="9c42e-122">С технической точки зрения, создатели пакетов могут использовать любую строку в качестве суффикса для обозначения предварительной версии, так как NuGet рассматривает любую такую версию как предварительную версию, не делая других интерпретаций.</span><span class="sxs-lookup"><span data-stu-id="9c42e-122">Technically speaking, package creators can use any string as a suffix to denote a pre-release version, as NuGet treats any such version as pre-release and makes no other interpretation.</span></span> <span data-ttu-id="9c42e-123">Это значит, что NuGet отображает полную строку версии в любом пользовательском интерфейсе, предоставляя потребителю возможность по-своему интерпретировать значение суффикса.</span><span class="sxs-lookup"><span data-stu-id="9c42e-123">That is, NuGet displays the full version string in whatever UI is involved, leaving any interpretation of the suffix's meaning to the consumer.</span></span>

<span data-ttu-id="9c42e-124">Тем не менее, разработчики пакетов обычно следуют общепризнанным соглашениям об именовании:</span><span class="sxs-lookup"><span data-stu-id="9c42e-124">That said, package developers generally follow recognized naming conventions:</span></span>

- <span data-ttu-id="9c42e-125">`-alpha`: альфа-версия, обычно используемая для текущей работы и экспериментирования;</span><span class="sxs-lookup"><span data-stu-id="9c42e-125">`-alpha`: Alpha release, typically used for work-in-progress and experimentation.</span></span>
- <span data-ttu-id="9c42e-126">`-beta`: бета-версия, которая обычно содержит полный набор функций для следующего запланированного выпуска, но может иметь известные ошибки;</span><span class="sxs-lookup"><span data-stu-id="9c42e-126">`-beta`: Beta release, typically one that is feature complete for the next planned release, but may contain known bugs.</span></span>
- <span data-ttu-id="9c42e-127">`-rc`: версия-кандидат, которая обычно может служить итоговой (стабильной), если не будут выявлены серьезные ошибки.</span><span class="sxs-lookup"><span data-stu-id="9c42e-127">`-rc`: Release candidate, typically a release that's potentially final (stable) unless significant bugs emerge.</span></span>

> [!Note]
> <span data-ttu-id="9c42e-128">NuGet 4.3.0+ поддерживает соглашение [SemVer 2.0.0](http://semver.org/spec/v2.0.0.html), которое позволяет использовать номера предварительных версий с точечной нотацией, как в случае с *1.0.1-build.23*.</span><span class="sxs-lookup"><span data-stu-id="9c42e-128">NuGet 4.3.0+ supports [SemVer 2.0.0](http://semver.org/spec/v2.0.0.html), which supports pre-release numbers with dot notation, as in *1.0.1-build.23*.</span></span> <span data-ttu-id="9c42e-129">В версиях NuGet, предшествующих 4.3.0, точечная нотация не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="9c42e-129">Dot notation is not supported with NuGet versions before 4.3.0.</span></span> <span data-ttu-id="9c42e-130">Вы можете использовать такую форму, как *1.0.1-build23*.</span><span class="sxs-lookup"><span data-stu-id="9c42e-130">You can use a form like *1.0.1-build23*.</span></span>

<span data-ttu-id="9c42e-131">При разрешении ссылок на пакеты и наличии нескольких версий пакета, отличающихся лишь суффиксом, NuGet сначала выбирает версию без суффикса, а затем применяет приоритет к предварительным версиям в обратном алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="9c42e-131">When resolving package references and multiple package versions differ only by suffix, NuGet chooses a version without a suffix first, then applies precedence to pre-release versions in reverse alphabetical order.</span></span> <span data-ttu-id="9c42e-132">Например, приведенные ниже версии будут выбраны в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="9c42e-132">For example, the following versions would be chosen in the exact order shown:</span></span>

    1.0.1
    1.0.1-zzz
    1.0.1-rc
    1.0.1-open
    1.0.1-beta
    1.0.1-alpha2
    1.0.1-alpha
    1.0.1-aaa

## <a name="semantic-versioning-200"></a><span data-ttu-id="9c42e-133">Семантическое версионирование 2.0.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-133">Semantic Versioning 2.0.0</span></span>

<span data-ttu-id="9c42e-134">В NuGet 4.3.0+ и Visual Studio 2017 версии 15.3+ NuGet поддерживает систему [Семантическое версионирование 2.0.0](http://semver.org/spec/v2.0.0.html).</span><span class="sxs-lookup"><span data-stu-id="9c42e-134">With NuGet 4.3.0+ and Visual Studio 2017 version 15.3+, NuGet supports [Semantic Versioning 2.0.0](http://semver.org/spec/v2.0.0.html).</span></span>

<span data-ttu-id="9c42e-135">Определенная семантика SemVer версии 2.0.0 не поддерживается в более старых клиентах.</span><span class="sxs-lookup"><span data-stu-id="9c42e-135">Certain semantics of SemVer v2.0.0 are not supported in older clients.</span></span> <span data-ttu-id="9c42e-136">NuGet определяет версию пакета как соответствующую SemVer версии 2.0.0, если выполнено любое из следующих условий:</span><span class="sxs-lookup"><span data-stu-id="9c42e-136">NuGet considers a package version to be SemVer v2.0.0 specific if either of the following statements is true:</span></span>

- <span data-ttu-id="9c42e-137">Метка предварительной версии разделена точкой, например *1.0.0-alpha.1*.</span><span class="sxs-lookup"><span data-stu-id="9c42e-137">The pre-release label is dot-separated, for example, *1.0.0-alpha.1*</span></span>
- <span data-ttu-id="9c42e-138">Версия содержит метаданные сборки, например *1.0.0+githash*.</span><span class="sxs-lookup"><span data-stu-id="9c42e-138">The version has build-metadata, for example, *1.0.0+githash*</span></span>

<span data-ttu-id="9c42e-139">Сайт nuget.org определяет пакет как SemVer версии 2.0.0, если выполнено любое из следующих условий:</span><span class="sxs-lookup"><span data-stu-id="9c42e-139">For nuget.org, a package is defined as a SemVer v2.0.0 package if either of the following statements is true:</span></span>

- <span data-ttu-id="9c42e-140">Собственная версия пакета совместима с SemVer версии 2.0.0, но не совместима с SemVer версии 1.0.0, как определено выше.</span><span class="sxs-lookup"><span data-stu-id="9c42e-140">The package's own version is SemVer v2.0.0 compliant but not SemVer v1.0.0 compliant, as defined above.</span></span>
- <span data-ttu-id="9c42e-141">Любой из диапазонов версий зависимостей пакета включает минимальную или максимальную версию, совместимую с SemVer версии 2.0.0, но не совместимую с системой SemVer версии 1.0.0, определенной выше, например, *[1.0.0-alpha.1,)* .</span><span class="sxs-lookup"><span data-stu-id="9c42e-141">Any of the package's dependency version ranges has a minimum or maximum version that is SemVer v2.0.0 compliant but not SemVer v1.0.0 compliant, defined above; for example, *[1.0.0-alpha.1, )*.</span></span>

<span data-ttu-id="9c42e-142">Если вы загрузите пакет, соответствующий SemVer версии 2.0.0, на сайт nuget.org, он будет невидим для более старых клиентов и доступен только для приведенных ниже клиентов NuGet:</span><span class="sxs-lookup"><span data-stu-id="9c42e-142">If you upload a SemVer v2.0.0-specific package to nuget.org, the package is invisible to older clients and available to only the following NuGet clients:</span></span>

- <span data-ttu-id="9c42e-143">NuGet 4.3.0+;</span><span class="sxs-lookup"><span data-stu-id="9c42e-143">NuGet 4.3.0+</span></span>
- <span data-ttu-id="9c42e-144">Visual Studio 2017 версии 15.3+;</span><span class="sxs-lookup"><span data-stu-id="9c42e-144">Visual Studio 2017 version 15.3+</span></span>
- <span data-ttu-id="9c42e-145">Visual Studio 2015 с [NuGet VSIX версии 3.6.0](https://dist.nuget.org/visualstudio-2015-vsix/latest/NuGet.Tools.vsix);</span><span class="sxs-lookup"><span data-stu-id="9c42e-145">Visual Studio 2015 with [NuGet VSIX v3.6.0](https://dist.nuget.org/visualstudio-2015-vsix/latest/NuGet.Tools.vsix)</span></span>
- <span data-ttu-id="9c42e-146">dotnet</span><span class="sxs-lookup"><span data-stu-id="9c42e-146">dotnet</span></span>
  - <span data-ttu-id="9c42e-147">dotnetcore.exe (пакета SDK для .NET 2.0.0+).</span><span class="sxs-lookup"><span data-stu-id="9c42e-147">dotnetcore.exe (.NET SDK 2.0.0+)</span></span>

<span data-ttu-id="9c42e-148">Сторонние клиенты:</span><span class="sxs-lookup"><span data-stu-id="9c42e-148">Third-party clients:</span></span>

- <span data-ttu-id="9c42e-149">JetBrains Rider;</span><span class="sxs-lookup"><span data-stu-id="9c42e-149">JetBrains Rider</span></span>
- <span data-ttu-id="9c42e-150">Paket версии 5.0+.</span><span class="sxs-lookup"><span data-stu-id="9c42e-150">Paket version 5.0+</span></span>

<!-- For compatibility with previous dependency-versions page -->
<a name="version-ranges"></a>

## <a name="version-ranges-and-wildcards"></a><span data-ttu-id="9c42e-151">Диапазоны версий и подстановочные знаки</span><span class="sxs-lookup"><span data-stu-id="9c42e-151">Version ranges and wildcards</span></span>

<span data-ttu-id="9c42e-152">Что касается зависимостей пакетов, NuGet поддерживает использование интервальной нотации для указания диапазонов версий, которые представлены следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9c42e-152">When referring to package dependencies, NuGet supports using interval notation for specifying version ranges, summarized as follows:</span></span>

| <span data-ttu-id="9c42e-153">Notation</span><span class="sxs-lookup"><span data-stu-id="9c42e-153">Notation</span></span> | <span data-ttu-id="9c42e-154">Примененное правило</span><span class="sxs-lookup"><span data-stu-id="9c42e-154">Applied rule</span></span> | <span data-ttu-id="9c42e-155">ОПИСАНИЕ</span><span class="sxs-lookup"><span data-stu-id="9c42e-155">Description</span></span> |
|----------|--------------|-------------|
| <span data-ttu-id="9c42e-156">1.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-156">1.0</span></span> | <span data-ttu-id="9c42e-157">x ≥ 1.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-157">x ≥ 1.0</span></span> | <span data-ttu-id="9c42e-158">Минимальная версия, включающая</span><span class="sxs-lookup"><span data-stu-id="9c42e-158">Minimum version, inclusive</span></span> |
| <span data-ttu-id="9c42e-159">(1.0,)</span><span class="sxs-lookup"><span data-stu-id="9c42e-159">(1.0,)</span></span> | <span data-ttu-id="9c42e-160">x > 1.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-160">x > 1.0</span></span> | <span data-ttu-id="9c42e-161">Минимальная версия, исключающая</span><span class="sxs-lookup"><span data-stu-id="9c42e-161">Minimum version, exclusive</span></span> |
| <span data-ttu-id="9c42e-162">[1.0]</span><span class="sxs-lookup"><span data-stu-id="9c42e-162">[1.0]</span></span> | <span data-ttu-id="9c42e-163">x == 1.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-163">x == 1.0</span></span> | <span data-ttu-id="9c42e-164">Точное соответствие версии</span><span class="sxs-lookup"><span data-stu-id="9c42e-164">Exact version match</span></span> |
| <span data-ttu-id="9c42e-165">(,1.0]</span><span class="sxs-lookup"><span data-stu-id="9c42e-165">(,1.0]</span></span> | <span data-ttu-id="9c42e-166">x ≤ 1.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-166">x ≤ 1.0</span></span> | <span data-ttu-id="9c42e-167">Максимальная версия, включающая</span><span class="sxs-lookup"><span data-stu-id="9c42e-167">Maximum version, inclusive</span></span> |
| <span data-ttu-id="9c42e-168">(,1.0)</span><span class="sxs-lookup"><span data-stu-id="9c42e-168">(,1.0)</span></span> | <span data-ttu-id="9c42e-169">x < 1.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-169">x < 1.0</span></span> | <span data-ttu-id="9c42e-170">Максимальная версия, исключающая</span><span class="sxs-lookup"><span data-stu-id="9c42e-170">Maximum version, exclusive</span></span> |
| <span data-ttu-id="9c42e-171">[1.0,2.0]</span><span class="sxs-lookup"><span data-stu-id="9c42e-171">[1.0,2.0]</span></span> | <span data-ttu-id="9c42e-172">1.0 ≤ x ≤ 2.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-172">1.0 ≤ x ≤ 2.0</span></span> | <span data-ttu-id="9c42e-173">Точный диапазон, включающий</span><span class="sxs-lookup"><span data-stu-id="9c42e-173">Exact range, inclusive</span></span> |
| <span data-ttu-id="9c42e-174">(1.0,2.0)</span><span class="sxs-lookup"><span data-stu-id="9c42e-174">(1.0,2.0)</span></span> | <span data-ttu-id="9c42e-175">1.0 < x < 2.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-175">1.0 < x < 2.0</span></span> | <span data-ttu-id="9c42e-176">Точный диапазон, исключающий</span><span class="sxs-lookup"><span data-stu-id="9c42e-176">Exact range, exclusive</span></span> |
| <span data-ttu-id="9c42e-177">[1.0,2.0)</span><span class="sxs-lookup"><span data-stu-id="9c42e-177">[1.0,2.0)</span></span> | <span data-ttu-id="9c42e-178">1.0 ≤ x < 2.0</span><span class="sxs-lookup"><span data-stu-id="9c42e-178">1.0 ≤ x < 2.0</span></span> | <span data-ttu-id="9c42e-179">Смешанная включающая минимальная и исключающая максимальная версии</span><span class="sxs-lookup"><span data-stu-id="9c42e-179">Mixed inclusive minimum and exclusive maximum version</span></span> |
| <span data-ttu-id="9c42e-180">(1.0)</span><span class="sxs-lookup"><span data-stu-id="9c42e-180">(1.0)</span></span>    | <span data-ttu-id="9c42e-181">недействительные</span><span class="sxs-lookup"><span data-stu-id="9c42e-181">invalid</span></span> | <span data-ttu-id="9c42e-182">недействительные</span><span class="sxs-lookup"><span data-stu-id="9c42e-182">invalid</span></span> |

<span data-ttu-id="9c42e-183">При использовании формата PackageReference NuGet также поддерживает применение нотации с использованием подстановочных знаков \* для основного и дополнительного номеров, а также для исправления и суффикса предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="9c42e-183">When using the PackageReference format, NuGet also supports using a wildcard notation, \*, for Major, Minor, Patch, and pre-release suffix parts of the number.</span></span> <span data-ttu-id="9c42e-184">В формате `packages.config` подстановочные знаки не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="9c42e-184">Wildcards are not supported with the `packages.config` format.</span></span>

> [!Note]
> <span data-ttu-id="9c42e-185">Диапазоны версий в PackageReference включают предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="9c42e-185">Version ranges in PackageReference include pre-release versions.</span></span> <span data-ttu-id="9c42e-186">По умолчанию плавающие версии не разрешают предварительные версии, если не указано обратное.</span><span class="sxs-lookup"><span data-stu-id="9c42e-186">By design, floating versions do not resolve prerelease versions unless opted into.</span></span> <span data-ttu-id="9c42e-187">Сведения о состоянии запроса соответствующей функции см. [на сайте GitHub](https://github.com/NuGet/Home/issues/6434#issuecomment-358782297) (запрос 6434).</span><span class="sxs-lookup"><span data-stu-id="9c42e-187">For the status of the related feature request, see [issue 6434](https://github.com/NuGet/Home/issues/6434#issuecomment-358782297).</span></span>

### <a name="examples"></a><span data-ttu-id="9c42e-188">Примеры</span><span class="sxs-lookup"><span data-stu-id="9c42e-188">Examples</span></span>

<span data-ttu-id="9c42e-189">Всегда указывайте версию или диапазон версий для зависимостей пакетов в файлах проекта (`packages.config` и `.nuspec`).</span><span class="sxs-lookup"><span data-stu-id="9c42e-189">Always specify a version or version range for package dependencies in project files, `packages.config` files, and `.nuspec` files.</span></span> <span data-ttu-id="9c42e-190">Без версии или диапазона версий NuGet 2.8.x и более ранние версии выбирают последнюю доступную версию пакета при разрешении зависимости, тогда как NuGet 3.x и более поздние версии выбирают самую раннюю версию пакета.</span><span class="sxs-lookup"><span data-stu-id="9c42e-190">Without a version or version range, NuGet 2.8.x and earlier chooses the latest available package version when resolving a dependency, whereas NuGet 3.x and later chooses the lowest package version.</span></span> <span data-ttu-id="9c42e-191">Указав версию или диапазон версий, вы сможете избежать этой неопределенности.</span><span class="sxs-lookup"><span data-stu-id="9c42e-191">Specifying a version or version range avoids this uncertainty.</span></span>

#### <a name="references-in-project-files-packagereference"></a><span data-ttu-id="9c42e-192">Ссылки в файлах проекта (PackageReference)</span><span class="sxs-lookup"><span data-stu-id="9c42e-192">References in project files (PackageReference)</span></span>

```xml
<!-- Accepts any version 6.1 and above. -->
<PackageReference Include="ExamplePackage" Version="6.1" />

<!-- Accepts any 6.x.y version. -->
<PackageReference Include="ExamplePackage" Version="6.*" />
<PackageReference Include="ExamplePackage" Version="[6,7)" />

<!-- Accepts any version above, but not including 4.1.3. Could be
     used to guarantee a dependency with a specific bug fix. -->
<PackageReference Include="ExamplePackage" Version="(4.1.3,)" />

<!-- Accepts any version up below 5.x, which might be used to prevent pulling in a later
     version of a dependency that changed its interface. However, this form is not
     recommended because it can be difficult to determine the lowest version. -->
<PackageReference Include="ExamplePackage" Version="(,5.0)" />

<!-- Accepts any 1.x or 2.x version, but not 0.x or 3.x and higher. -->
<PackageReference Include="ExamplePackage" Version="[1,3)" />

<!-- Accepts 1.3.2 up to 1.4.x, but not 1.5 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.3.2,1.5)" />
```

<span data-ttu-id="9c42e-193">**Ссылки в `packages.config`**</span><span class="sxs-lookup"><span data-stu-id="9c42e-193">**References in `packages.config`:**</span></span>

<span data-ttu-id="9c42e-194">В `packages.config` каждая зависимость указана с точным атрибутом `version`, который используется при восстановлении пакетов.</span><span class="sxs-lookup"><span data-stu-id="9c42e-194">In `packages.config`, every dependency is listed with an exact `version` attribute that's used when restoring packages.</span></span> <span data-ttu-id="9c42e-195">Атрибут `allowedVersions` используется только во время выполнения операций обновления, чтобы ограничить версии, до которых может быть обновлен пакет.</span><span class="sxs-lookup"><span data-stu-id="9c42e-195">The `allowedVersions` attribute is used only during update operations to constrain the versions to which the package might be updated.</span></span>

```xml
<!-- Install/restore version 6.1.0, accept any version 6.1.0 and above on update. -->
<package id="ExamplePackage" version="6.1.0" allowedVersions="6.1.0" />

<!-- Install/restore version 6.1.0, and do not change during update. -->
<package id="ExamplePackage" version="6.1.0" allowedVersions="[6.1.0]" />

<!-- Install/restore version 6.1.0, accept any 6.x version during update. -->
<package id="ExamplePackage" version="6.1.0" allowedVersions="[6,7)" />

<!-- Install/restore version 4.1.4, accept any version above, but not including, 4.1.3.
     Could be used to guarantee a dependency with a specific bug fix. -->
<package id="ExamplePackage" version="4.1.4" allowedVersions="(4.1.3,)" />

<!-- Install/restore version 3.1.2, accept any version up below 5.x on update, which might be
     used to prevent pulling in a later version of a dependency that changed its interface.
     However, this form is not recommended because it can be difficult to determine the lowest version. -->
<package id="ExamplePackage" version="3.1.2" allowedVersions="(,5.0)" />

<!-- Install/restore version 1.1.4, accept any 1.x or 2.x version on update, but not
     0.x or 3.x and higher. -->
<package id="ExamplePackage" version="1.1.4" allowedVersions="[1,3)" />

<!-- Install/restore version 1.3.5, accepts 1.3.2 up to 1.4.x on update, but not 1.5 and higher. -->
<package id="ExamplePackage" version="1.3.5" allowedVersions="[1.3.2,1.5)" />
```

<span data-ttu-id="9c42e-196">**Ссылки в файлах `.nuspec`**</span><span class="sxs-lookup"><span data-stu-id="9c42e-196">**References in `.nuspec` files**</span></span>

<span data-ttu-id="9c42e-197">Атрибут `version` в элементе `<dependency>` описывает версии диапазона, допустимые для зависимости.</span><span class="sxs-lookup"><span data-stu-id="9c42e-197">The `version` attribute in a `<dependency>` element describes the range versions that are acceptable for a dependency.</span></span>

```xml
<!-- Accepts any version 6.1 and above. -->
<dependency id="ExamplePackage" version="6.1" />

<!-- Accepts any version above, but not including 4.1.3. Could be
     used to guarantee a dependency with a specific bug fix. -->
<dependency id="ExamplePackage" version="(4.1.3,)" />

<!-- Accepts any version up below 5.x, which might be used to prevent pulling in a later
     version of a dependency that changed its interface. However, this form is not
     recommended because it can be difficult to determine the lowest version. -->
<dependency id="ExamplePackage" version="(,5.0)" />

<!-- Accepts any 1.x or 2.x version, but not 0.x or 3.x and higher. -->
<dependency id="ExamplePackage" version="[1,3)" />

<!-- Accepts 1.3.2 up to 1.4.x, but not 1.5 and higher. -->
<dependency id="ExamplePackage" version="[1.3.2,1.5)" />
```

## <a name="normalized-version-numbers"></a><span data-ttu-id="9c42e-198">Нормализованные номера версий</span><span class="sxs-lookup"><span data-stu-id="9c42e-198">Normalized version numbers</span></span>

> [!Note]
> <span data-ttu-id="9c42e-199">Это критическое изменение для NuGet 3.4 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="9c42e-199">This is a breaking change for NuGet 3.4 and later.</span></span>

<span data-ttu-id="9c42e-200">При получении пакетов из репозитория во время выполнения операций установки, переустановки или восстановления NuGet 3.4+ обрабатывает номера версий следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9c42e-200">When obtaining packages from a repository during install, reinstall, or restore operations, NuGet 3.4+ treats version numbers as follows:</span></span>

- <span data-ttu-id="9c42e-201">Начальные нули удаляются из номеров версий:</span><span class="sxs-lookup"><span data-stu-id="9c42e-201">Leading zeroes are removed from version numbers:</span></span>

        1.00 is treated as 1.0
        1.01.1 is treated as 1.1.1
        1.00.0.1 is treated as 1.0.0.1

- <span data-ttu-id="9c42e-202">Ноль в четвертой части номера версии будет опущен.</span><span class="sxs-lookup"><span data-stu-id="9c42e-202">A zero in the fourth part of the version number will be omitted</span></span>

        1.0.0.0 is treated as 1.0.0
        1.0.01.0 is treated as 1.0.1

<span data-ttu-id="9c42e-203">При возможности операции `pack` и `restore` нормализуют версии.</span><span class="sxs-lookup"><span data-stu-id="9c42e-203">`pack` and `restore` operations normalize versions whenever possible.</span></span> <span data-ttu-id="9c42e-204">Что касается уже собранных пакетов, эта нормализация не влияет на номера версий в самих пакетах. Она повлияет только на способ сопоставления версий NuGet при разрешении зависимостей.</span><span class="sxs-lookup"><span data-stu-id="9c42e-204">For packages already built, this normalization does not affect the version numbers in the packages themselves; it affects only how NuGet matches versions when resolving dependencies.</span></span>

<span data-ttu-id="9c42e-205">Однако репозитории пакетов NuGet должны обрабатывать эти значения так же, как NuGet, чтобы предотвратить дублирование версий пакетов.</span><span class="sxs-lookup"><span data-stu-id="9c42e-205">However, NuGet package repositories must treat these values in the same way as NuGet to prevent package version duplication.</span></span> <span data-ttu-id="9c42e-206">Таким образом, репозиторий, содержащий пакет версии *1.0*, не должен содержать версию *1.0.0* в качестве отдельного пакета.</span><span class="sxs-lookup"><span data-stu-id="9c42e-206">Thus a repository that contains version *1.0* of a package should not also host version *1.0.0* as a separate and different package.</span></span>