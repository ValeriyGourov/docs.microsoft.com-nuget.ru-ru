---
title: Заметки о выпуске NuGet 2.2.1
description: Заметки о выпуске NuGet 2.2.1, включая известные проблемы, исправления ошибок, добавленные функции и DCR.
author: JonDouglas
ms.author: jodou
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: b6058fd596e32d38042aa75027640a5e5baca472
ms.sourcegitcommit: ee6c3f203648a5561c809db54ebeb1d0f0598b68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2021
ms.locfileid: "98776802"
---
# <a name="nuget-221-release-notes"></a>Заметки о выпуске NuGet 2.2.1

[Заметки о](../release-notes/nuget-2.2.md)  |  выпуске NuGet 2,2 [Заметки о выпуске NuGet 2,5](../release-notes/nuget-2.5.md)

Версия NuGet 2.2.1 была выпущена 15 февраля 2013 г.  Номер версии расширения VS — 2.2.40116.9051.

## <a name="localization-refresh"></a>Обновление локализации
Когда NuGet поставляется в составе Visual Studio 2012, он был полностью локализован на английский + 13 других языков.  С этого момента, NuGet 2,1 и 2,2 поставляются, но локализация не обновлялась.  Выпуск NuGet 2.2.1 обновляет нашу локализацию.

Пользовательский интерфейс и консоль PowerShell для NuGet локализованы на следующие языки:

1. Китайский (упрощенное письмо)
1. Китайский (традиционное письмо)
1. Чешский
1. Английский
1. Французский
1. Немецкий
1. Итальянский
1. Японский
1. Корейский
1. Польский
1. Португальский (Бразилия)
1. Русский
1. Испанский
1. Турецкий

## <a name="visual-studio-templates-support-multiple-preinstalled-package-repositories"></a>Шаблоны Visual Studio поддерживают несколько предварительно установленных репозиториев пакетов
Если вы создаете шаблоны Visual Studio, вы можете использовать NuGet для [предварительной установки пакетов](../visual-studio-extensibility/visual-studio-templates.md) в составе шаблона.  До настоящего момента эта функция имела ограничение на то, что все пакеты, необходимые для появления из одного и того же источника.  При использовании NuGet 2.2.1 можно установить пакеты из нескольких репозиториев (в шаблоне, в VSIX или в папке на диске, определенном в реестре).

Основным сценарием для этой функции являются пользовательские шаблоны проектов ASP.NET.  Встроенные шаблоны ASP.NET используют Предустановленные пакеты, получая пакеты с локального диска.  Теперь можно создать пользовательский шаблон проекта ASP.NET, использующий существующие пакеты, установленные ASP.NET, но добавить дополнительные пакеты NuGet в шаблон.

## <a name="bug-fixes"></a>Исправления ошибок
NuGet 2.2.1 включает в себя несколько исправлений, предназначенных для устранения неполадок. Список рабочих элементов, исправленных в NuGet 2.2.1, см. в [этом выпуске](http://nuget.codeplex.com/workitem/list/advanced?keyword=&status=Closed&type=All&priority=All&release=NuGet%202.2.1&assignedTo=All&component=All&sortField=LastUpdatedDate&sortDirection=Descending&page=0).


## <a name="known-issues"></a>Известные проблемы

При расширении шаблонов проектов ASP.NET все предварительно установленные репозитории пакетов должны использовать одно и то же значение для `isPreunzipped` атрибута.
