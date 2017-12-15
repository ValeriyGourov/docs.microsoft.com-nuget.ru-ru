---
title: "Заметки о выпуске NuGet 2.8.6 | Документы Microsoft"
author: karann-msft
ms.author: karann-msft
manager: ghogen
ms.date: 11/11/2016
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 920c551c-18a7-40f4-a32b-ce84de6ea766
description: "Заметки о выпуске для NuGet 2.8.6, включая известные проблемы, исправленные ошибки, добавленные функции и DCR."
keywords: "NuGet 2.8.6 заметки о выпуске, исправления, известными проблемами, добавлены функции, DCR"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: f33c1edd3ef703a8cd97b7bdd97c37e12426aafa
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-286-release-notes"></a><span data-ttu-id="c826d-104">Заметки о выпуске NuGet 2.8.6</span><span class="sxs-lookup"><span data-stu-id="c826d-104">NuGet 2.8.6 Release Notes</span></span>

<span data-ttu-id="c826d-105">[Заметки о выпуске NuGet 2.8.5](../release-notes/nuget-2.8.5.md) | [NuGet 2.8.7 заметки о выпуске](../release-notes/nuget-2.8.7.md)</span><span class="sxs-lookup"><span data-stu-id="c826d-105">[NuGet 2.8.5 Release Notes](../release-notes/nuget-2.8.5.md) | [NuGet 2.8.7 Release Notes](../release-notes/nuget-2.8.7.md)</span></span>

<span data-ttu-id="c826d-106">NuGet 2.8.6 был выпущен 20 июля 2015 г. как незначительное обновление для наших 2.8.5 VSIX с некоторыми целевой исправления и улучшения для поддержки пакетов, которые могут доставляться с поддержкой модели разработки Windows 10 UWP.</span><span class="sxs-lookup"><span data-stu-id="c826d-106">NuGet 2.8.6 was released July 20, 2015 as a minor update to our 2.8.5 VSIX with some targeted fixes and improvements to support packages that may be delivered with support for the Windows 10 UWP development model.</span></span>

<span data-ttu-id="c826d-107">Эта версия расширения диспетчера пакетов NuGet обеспечивает поддержку только для Visual Studio 2013.</span><span class="sxs-lookup"><span data-stu-id="c826d-107">This version of the NuGet package manager extension provides support for Visual Studio 2013 only.</span></span>

<span data-ttu-id="c826d-108">В этом выпуске диспетчер пакетов NuGet диалогового окна имел добавлена поддержка для:</span><span class="sxs-lookup"><span data-stu-id="c826d-108">In this release, the NuGet Package Manager dialog had support added for:</span></span>

* <span data-ttu-id="c826d-109">Появился UAP моникер целевой платформы для разработки приложений Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c826d-109">Introduced the UAP Target Framework Moniker to support Windows 10 Application Development.</span></span>
* <span data-ttu-id="c826d-110">Протокол NuGet версии 3-конечные точки</span><span class="sxs-lookup"><span data-stu-id="c826d-110">NuGet protocol version 3 endpoints</span></span>
* <span data-ttu-id="c826d-111">Поддержка [Nuget.Config](../consume-packages/configuring-nuget-behavior.md) protocolVersion атрибут источникам репозиториев.</span><span class="sxs-lookup"><span data-stu-id="c826d-111">Support for [Nuget.Config](../consume-packages/configuring-nuget-behavior.md) protocolVersion attribute on repository sources.</span></span> <span data-ttu-id="c826d-112">Значение по умолчанию — «2»</span><span class="sxs-lookup"><span data-stu-id="c826d-112">Default value is "2"</span></span>
* <span data-ttu-id="c826d-113">Будет использоваться предыдущий удаленный репозиторий, если версия требуемый пакет недоступен в локальном кэше</span><span class="sxs-lookup"><span data-stu-id="c826d-113">Falling back to remote repository if a required package version is not available in the local cache</span></span>