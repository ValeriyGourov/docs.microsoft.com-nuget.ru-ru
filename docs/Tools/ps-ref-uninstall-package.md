---
title: "Справочник по PowerShell удалить пакет NuGet | Документы Microsoft"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 06/01/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Ссылка для команды PowerShell удалением пакета в консоли диспетчера пакетов NuGet в Visual Studio."
keywords: "Пакет NuGet консоли диспетчера, команд NuGet Powershell, справочник по NuGet Powershell, удалением пакета"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: db7cf9b2282bf40988eee2308c256381c4fd5124
ms.sourcegitcommit: 7969f6cd94eccfee5b62031bb404422139ccc383
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2018
---
# <a name="uninstall-package-package-manager-console-in-visual-studio"></a>Uninstall-Package (консоль диспетчера пакетов в Visual Studio)

*В этом разделе описываются команды в [консоль диспетчера пакетов NuGet](package-manager-console.md) в Visual Studio в Windows. Общая команда PowerShell Uninstall-Package. в разделе [PowerShell PackageManagement ссылка](/powershell/module/packagemanagement/?view=powershell-6).*

Удаляет пакет из проекта, при необходимости удаления его зависимости. Если для данного пакета зависят другие пакеты, команда будет выполнена, если указан параметр-Force.

## <a name="syntax"></a>Синтаксис

```ps
Uninstall-Package [-Id] <string> [-RemoveDependencies] [-ProjectName <string>] [-Force]
    [-Version <string>] [-WhatIf] [<CommonParameters>]
```

Если для данного пакета зависят другие пакеты, команда будет выполнена, если указан параметр-Force.

## <a name="parameters"></a>Параметры

| Параметр | Описание: |
| --- | --- |
| Идентификатор | (Обязательно) Идентификатор пакета для удаления. — Идентификатор коммутатора сам является необязательным. |
| Версия | Версия пакета для удаления, установка значений по умолчанию для текущей установленной версии. |
| RemoveDependencies | Удалите пакет и его неиспользуемые зависимости. То есть если какой-либо зависимостью связан другой пакет зависит от него, он пропускается. |
| ИмяПроекта | Проект, из которого необходимо удалить пакет, установка значений по умолчанию для проекта по умолчанию. |
| Force | Принудительное пакета будет удалена, даже если он зависят другие пакеты. |
| WhatIf | Показывает, что произойдет при запуске команды без фактического выполнения удаления. |

Ни один из этих параметров принимает входные данные или подстановочный знак символов конвейера.

## <a name="common-parameters"></a>Общие параметры

`Uninstall-Package` поддерживает следующие [Общие параметры PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): отладка, действие при возникновении ошибки, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction и WarningVariable.

## <a name="examples"></a>Примеры

```ps
# Uninstalls the Elmah package from the default project
Uninstall-Package Elmah

# Uninstalls the Elmah package and all its unused dependencies
Uninstall-Package Elmah -RemoveDependencies 

# Uninstalls the Elmah package even if another package depends on it
Uninstall-Package Elmah -Force
```