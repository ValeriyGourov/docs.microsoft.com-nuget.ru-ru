---
title: Заметки о выпуске NuGet 3,4
description: Заметки о выпуске NuGet 3,4, включая известные проблемы, исправления ошибок, добавленные функции и DCR.
author: JonDouglas
ms.author: jodou
ms.date: 11/11/2016
ms.topic: conceptual
ms.openlocfilehash: 794b25e2d81d7a2c297a185bdb34a7cf68535723
ms.sourcegitcommit: ee6c3f203648a5561c809db54ebeb1d0f0598b68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2021
ms.locfileid: "98776423"
---
# <a name="nuget-34-release-notes"></a>Заметки о выпуске NuGet 3,4

[NuGet 3,4 — заметки о](../release-notes/nuget-3.4-RC.md)  |  ВЫпуске RC [Заметки о выпуске 3.4.1 NuGet](../release-notes/nuget-3.4.1.md)

Версия NuGet 3,4 была выпущена 30 марта 2016 в составе Visual Studio 2015 с обновлением 2 и Visual Studio 15 Preview и была разработана с использованием нескольких принципов в умы:

* Кросс-платформенная поддержка
* Улучшения производительности
* Незначительные улучшения пользовательского интерфейса

Следующие функции ранее были добавлены в версию-кандидат и были обновлены или завершены для выпуска 3,4:

## <a name="new-features"></a>Новые возможности

* Клиенты NuGet теперь поддерживают кодирование содержимого gzip из репозиториев
* Поддержка PDB из пакетов в проектах xproj
* Поддержка действий сборки iOS и Android в элементе contentFiles
* Поддержка моникеров платформы netstandard и нетстандардапп

## <a name="new-user-interface-features"></a>Новые функции пользовательского интерфейса

* Значительные улучшения производительности, особенно на вкладках «установленные», «обновления» и «консолидация»
* Доступен общий источник "все источники пакетов" с соответствующим слиянием результатов поиска
* Вкладки установленные и обновленные теперь сортируются в алфавитном порядке
* Добавлена кнопка Обновить, позволяющая обновлять Поиск.
* Последние параметры сборки в верхней части списка версий

## <a name="updates-and-improvements"></a>Обновления и улучшения

* Пакеты, на `project.json` которые ссылается в, имеют плавающую версию, не будут обновляться при каждой сборке. Вместо этого они будут обновляться только при принудительном восстановлении, очистке, перестроении или изменении `project.json` .
* источники репозитория nuget.org больше не переносятся в конфигурацию проекта при использовании пользовательского интерфейса настройки NuGet.
* NuGet больше не восстанавливает пакеты в общих проектах и не записывает файл блокировки.
* Мы улучшили сетевые сбои и повторную обработку недостижимых или медленных серверов.
* В пользовательском интерфейсе диспетчера пакетов Visual Studio улучшены режимы работы клавиатуры и мыши.
* Теперь мы поддерживаем последнюю `project.json` схему в DNX.

## <a name="breaking-changes"></a>Критические изменения

* Номера версий пакета теперь нормализованы до формата " *основной*". *дополнительный номер*. *исправление* - *Предварительный выпуск*   Каждое из основных, дополнительных и исправлений обрабатывается как целые числа и удаляет начальные нули.  Сведения о предварительном выпуске обрабатываются как строка, и к ней не применяются никакие изменения. Эти числа используются в запросах клиентов NuGet и в поиске, предоставляемом службой nuget.org.  Дополнительные сведения можно найти в документах NuGet в разделе [предварительные версии](../create-packages/prerelease-packages.md).

## <a name="known-issues"></a>Известные проблемы

* **Вопрос.** Пользователи Windows 10 клиенте v1511 установлен могут столкнуться с проблемами или даже с аварийным завершением Visual Studio с помощью PowerShell в Visual Studio в следующих сценариях:
    * Установка и удаление пакетов, в которых есть скрипты install.ps1 и uninstall.ps1
    * Загрузка проектов, имеющих скрипт init.ps1 (например, EntityFramework)
    * Публикация веб-содержимого

* **Обходной путь:** Убедитесь, что на установку Windows 10 установлены последние исправления, експеЦиалли 2016 января (KB 3124263) или более поздней версии.  Дополнительные сведения см. в [#1638 проблемы GitHub](http://github.com/nuget/home/issues/1638) .

* **Проблема.** Перенаправление протокола NuGet 2 не работает.
Пользовательские репозитории NuGet, которые перенаправляют запросы на другой узел, не учитывают запрос перенаправления.
* **Обходной путь:**  Чтобы обойти эту ошибку, настройте URI репозитория пакетов в параметрах, чтобы указать расположение перенаправленного сервера.
Дополнительные сведения см. в разделе [#387 запроса на вытягивание GitHub](https://github.com/NuGet/NuGet.Client/pull/387).

Мы продолжаем отслеживанием проблем в нашем списке проблем GitHub, который можно найти по адресу: [http://github.com/nuget/home/issues](http://github.com/nuget/home/issues)