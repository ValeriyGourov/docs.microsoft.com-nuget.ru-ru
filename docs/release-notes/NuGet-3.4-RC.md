---
title: Заметки о выпуске 3.4 RC NuGet
description: Заметки о выпуске для RC NuGet 3.4, включая известные проблемы, исправленные ошибки, добавленные функции и DCR.
author: karann-msft
ms.author: karann
manager: unnir
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: e40d685a5256fdfee818f0cc1f1bc352c698f3c2
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31820824"
---
# <a name="nuget-34-rc-release-notes"></a>Заметки о выпуске 3.4 RC NuGet

[Заметки о выпуске NuGet 3.3](../release-notes/nuget-3.3.md) | [NuGet 3.4 заметки о выпуске](../release-notes/nuget-3.4.md)

NuGet 3.4-RC была выпущена 3 марта 2016 г. параллельно с Visual Studio 2015 г. обновление 2 RC и был построен с несколько принципов в умы:

* Кроссплатформенная поддержка
* Улучшения производительности
* Незначительные изменения пользовательского интерфейса

Следующие функции доступны в этой версии-Кандидата с более спланированных для 3,4 окончательной версии.

## <a name="new-features"></a>Новые функции

* Клиенты NuGet теперь поддерживают gzip content-encoding из репозиториев
* Поддержка PDB-файлы из пакетов в компилируемых проектах
* Поддержка iOS и Android построения действий в элементе contentFiles
* Поддержка моникеров netstandard и netstandardapp моникеров платформы

## <a name="new-user-interface-features"></a>Новые функции пользовательского интерфейса

* Значительное повышение производительности особенно на вкладках установки, обновления и Консолидация
* Установки и обновления вкладки теперь отсортированы в алфавитном порядке
* Добавить кнопку обновления, которая позволяет поиска для обновления

## <a name="updates-and-improvements"></a>Обновления и улучшения

* Пакеты, на которые ссылается `project.json` , имеющих плавающей версии не будут обновлены для каждой сборки. Вместо этого они будут обновлены только в том случае, когда принудительного восстановления, очистка, перестроение и изменение `project.json`.
* источники NuGet.org репозитории нет необходимости в конфигурацию проекта при использовании NuGet конфигурации пользовательского интерфейса.
* NuGet больше не восстанавливает пакетов в общих проектов, а также записывает файл блокировки.
* Мы улучшили сбой сети и повторите попытку обработки для серверов недоступен или медленно в ответ.
* Клавиатура и мышь поведения улучшение в пользовательском Интерфейсе диспетчера пакетов Visual Studio.
* Добавлена поддержка последней `project.json` схемы в DNX.

## <a name="known-issues"></a>Известные проблемы

Мы продолжаем отслеживания проблем на наш список проблем GitHub, которую можно найти в: [http://github.com/nuget/home/issues](http://github.com/nuget/home/issues)