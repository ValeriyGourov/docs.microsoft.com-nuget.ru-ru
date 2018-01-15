---
title: "Удаление пакетов NuGet с сайта nuget.org | Документы Майкрософт"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 1/9/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: a348ca2e-0a5d-40ad-ba33-9bb37e1d980b
description: "Политики для исключения пакетов с сайта nuget.org; окончательное удаление не поддерживается, если только пакеты не нарушают другие политики."
keywords: "удаление пакетов NuGet, исключение пакетов NuGet, запрещенные варианты использования пакетов"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 9e388171f83fae7deb4f20033184dfa91bfab3da
ms.sourcegitcommit: a40c1c1cc05a46410f317a72f695ad1d80f39fa2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
---
# <a name="deleting-packages"></a><span data-ttu-id="33306-104">Удаление пакетов</span><span class="sxs-lookup"><span data-stu-id="33306-104">Deleting packages</span></span>

<span data-ttu-id="33306-105">Сайт nuget.org не поддерживает окончательное удаление пакетов.</span><span class="sxs-lookup"><span data-stu-id="33306-105">nuget.org does not support permanent deletion of packages.</span></span> <span data-ttu-id="33306-106">Это бы нарушило работоспособность всех проектов, зависящих от доступности пакета, особенно для рабочих процессов, связанных с восстановлением пакетов.</span><span class="sxs-lookup"><span data-stu-id="33306-106">Doing so would break every project depending on the availability of the package, especially with build workflows that involve package restore.</span></span>

<span data-ttu-id="33306-107">Сайт nuget.org поддерживает *исключение* пакета, которое можно выполнить на странице управления пакетом на веб-сайте.</span><span class="sxs-lookup"><span data-stu-id="33306-107">nuget.org does supports *unlisting* a package, which can be done in the package management page on the web site.</span></span> <span data-ttu-id="33306-108">Исключенные пакеты не отображаются на сайте nuget.org или в пользовательском интерфейсе Visual Studio, а также в результатах поиска.</span><span class="sxs-lookup"><span data-stu-id="33306-108">Unlisted packages don't appear on nuget.org or in the Visual Studio UI, and do not appear in search results.</span></span> <span data-ttu-id="33306-109">Однако их по-прежнему можно скачать и установить по точному номеру версии, что обеспечивает возможность восстановления пакетов.</span><span class="sxs-lookup"><span data-stu-id="33306-109">Unlisted packages, however, can still be downloaded and installed by using an exact version number, which supports package restore.</span></span> <span data-ttu-id="33306-110">Кроме того, исключенные пакеты по-прежнему можно обнаружить в следующих сценариях:</span><span class="sxs-lookup"><span data-stu-id="33306-110">In addition, unlisted packages may still be discovered in the following specific scenarios:</span></span>

- <span data-ttu-id="33306-111">Восстановление пакетов с использованием групповых версий (например, `1.0.0-*`), если последний пакет, удовлетворяющий ограничениям по версии или зависимости, является исключенным.</span><span class="sxs-lookup"><span data-stu-id="33306-111">Package restore using floating versions (for example, `1.0.0-*`), if the latest available package matching the version or dependency constraints is an unlisted package.</span></span>
- <span data-ttu-id="33306-112">Репликация пакетов через каталог (так как он также содержит исключенные пакеты).</span><span class="sxs-lookup"><span data-stu-id="33306-112">Replication of packages through the catalog (as the catalog also contains unlisted packages).</span></span>

## <a name="exceptions"></a><span data-ttu-id="33306-113">Исключения</span><span class="sxs-lookup"><span data-stu-id="33306-113">Exceptions</span></span>

<span data-ttu-id="33306-114">В исключительных ситуациях, например при нарушении авторских прав и потенциально опасном содержимом, команда NuGet может удалить пакеты вручную.</span><span class="sxs-lookup"><span data-stu-id="33306-114">In exceptional situations such as copyright infringement and potentially harmful content, packages can be deleted manually by the NuGet team.</span></span> <span data-ttu-id="33306-115">Чтобы запустить эту процедуру, вы можете отправить запрос в службу поддержки через [коллекцию NuGet](http://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="33306-115">Submit a support request through [NuGet Gallery](http://www.nuget.org) to start the process.</span></span>

## <a name="prohibited-use"></a><span data-ttu-id="33306-116">Запрещенные варианты использования</span><span class="sxs-lookup"><span data-stu-id="33306-116">Prohibited use</span></span>

<span data-ttu-id="33306-117">Пакеты, соответствующие любому из следующих критериев, запрещено размещать в общедоступной коллекции NuGet. Они будут немедленно удалены без каких-либо обсуждений.</span><span class="sxs-lookup"><span data-stu-id="33306-117">Packages that meet any of the following criteria are not allowed on the public NuGet gallery and will be immediately removed without discussion.</span></span> <span data-ttu-id="33306-118">При этом владельцы пакетов получат уведомление об удалении.</span><span class="sxs-lookup"><span data-stu-id="33306-118">Package owners will, however, be notified of the removal.</span></span>

- <span data-ttu-id="33306-119">Наличие вредоносных программ, программ для показа рекламы и любых видов программ-шпионов.</span><span class="sxs-lookup"><span data-stu-id="33306-119">Contains malware, adware, or any kind of spyware.</span></span>
- <span data-ttu-id="33306-120">Способность причинить вред рабочей станции разработчика или его организации.</span><span class="sxs-lookup"><span data-stu-id="33306-120">Are designed to harm a developer's workstation or their organization.</span></span>
- <span data-ttu-id="33306-121">Нарушение авторских прав или условий лицензии.</span><span class="sxs-lookup"><span data-stu-id="33306-121">Infringes copyrights or violates licenses.</span></span>
- <span data-ttu-id="33306-122">Наличие недопустимого содержимого.</span><span class="sxs-lookup"><span data-stu-id="33306-122">Contains illegal content.</span></span>
- <span data-ttu-id="33306-123">Использование для захвата идентификаторов пакетов, включая пакеты без полезного содержимого.</span><span class="sxs-lookup"><span data-stu-id="33306-123">Are being used to squat on package identifiers, including packages that have zero productive content.</span></span> <span data-ttu-id="33306-124">Пакеты должны содержать код, либо владельцы должны уступить идентификатор тому, у кого есть предоставляемый продукт.</span><span class="sxs-lookup"><span data-stu-id="33306-124">Packages must contain code or the owners must concede the identifier to someone who actually has a product to ship.</span></span>
- <span data-ttu-id="33306-125">Попытки заставить коллекцию выполнять какие-то действия, для которых она явным образом не создана.</span><span class="sxs-lookup"><span data-stu-id="33306-125">Attempt to make the gallery do something that it's not explicitly designed to do.</span></span>

<span data-ttu-id="33306-126">Если вы нашли пакет, который соответствует любому из этих пунктов, выберите ссылку **Сообщить о нарушении** на странице со сведениями об этом пакете и отправьте отчет.</span><span class="sxs-lookup"><span data-stu-id="33306-126">If you find a package that is in violation of any of these items, click the **Report Abuse** link on the package details page and submit a report.</span></span>

<span data-ttu-id="33306-127">Обратите внимание, что команда NuGet и .NET Foundation оставляет за собой право изменить эти условия в любое время.</span><span class="sxs-lookup"><span data-stu-id="33306-127">Note that the NuGet team and the .NET Foundation reserves the right to change these criteria at any time.</span></span>