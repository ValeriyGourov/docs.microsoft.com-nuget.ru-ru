---
title: Кроссплатформенный подключаемый модуль проверки подлинности NuGet
description: Подключаемые модули межплатформенной проверки подлинности NuGet для NuGet. exe, DotNet. exe, MSBuild. exe и Visual Studio
author: nkolev92
ms.author: nikolev
ms.date: 07/01/2018
ms.topic: conceptual
ms.openlocfilehash: a716737343ea826d28da6de46c32ca73aef590bd
ms.sourcegitcommit: efc18d484fdf0c7a8979b564dcb191c030601bb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/18/2019
ms.locfileid: "68317282"
---
# <a name="nuget-cross-platform-authentication-plugin"></a>Кроссплатформенный подключаемый модуль проверки подлинности NuGet

В версии 4.8 + все клиенты NuGet (NuGet. exe, Visual Studio, DotNet. exe и MSBuild. exe) могут использовать подключаемый модуль проверки подлинности, построенный на основе модели [подключаемых модулей NuGet кросс-платформы](NuGet-Cross-Platform-Plugins.md) .

## <a name="authentication-in-dotnetexe"></a>Проверка подлинности в DotNet. exe

Visual Studio и NuGet. exe по умолчанию являются интерактивными. NuGet. exe содержит переключатель, чтобы сделать его [неинтерактивным](../nuget-exe-CLI-Reference.md).
Кроме того, модули NuGet. exe и Visual Studio запрашивают у пользователя входные данные.
В DotNet. exe нет запросов и значение по умолчанию — не Interactive.

Механизм проверки подлинности в DotNet. exe — это поток устройства. Если операция восстановления или добавления пакета выполняется в интерактивном режиме, блоки и инструкции для пользователя по выполнению проверки подлинности будут предоставлены в командной строке.
Когда пользователь завершает проверку подлинности, операция будет продолжена.

Чтобы сделать операцию интерактивной, должна пройти `--interactive`одна.
В настоящее время интерактивный `dotnet add package` коммутатор поддерживает только явные `dotnet restore` команды и.
Интерактивный коммутатор отсутствует в `dotnet build` и. `dotnet publish`

## <a name="authentication-in-msbuild"></a>Проверка подлинности в MSBuild

Как и в DotNet. exe, MSBuild. exe по умолчанию является неинтерактивным механизмом проверки подлинности MSBuild. exe — это поток устройства.
Чтобы позволить восстановить приостановку и ожидание проверки подлинности, `msbuild -t:restore -p:NuGetInteractive="true"`Вызовите инструкцию RESTORE WITH.

## <a name="creating-a-cross-platform-authentication-plugin"></a>Создание подключаемого модуля межплатформенной проверки подлинности

Пример реализации можно найти в [подключаемом модуле поставщика учетных данных Майкрософт](https://github.com/Microsoft/artifacts-credprovider).

Очень важно, чтобы подключаемые модули применялись к требованиям безопасности, заданным в клиентских средствах NuGet.
Минимальная требуемая версия подключаемого модуля должна быть подключаемым модулем проверки подлинности — *2.0.0*.
NuGet выполняет подтверждение с помощью подключаемого модуля и запрашивает поддерживаемые утверждения операций.
Дополнительные сведения о конкретных сообщениях см. в [сообщениях о протоколе](NuGet-Cross-Platform-Plugins.md#protocol-messages-index) межплатформенного подключаемого модуля NuGet.

NuGet устанавливает уровень ведения журнала и предоставляет подключаемому модулю сведения о прокси-сервере, если это применимо.
Ведение журнала в консоли NuGet допустимо только после того, как NuGet установила уровень ведения журнала для подключаемого модуля.

- Поведение проверки подлинности подключаемого модуля .NET Framework

В .NET Framework подключаемые модули могут запрашивать у пользователя ввод в виде диалогового окна.

- Поведение проверки подлинности подключаемого модуля .NET Core

В .NET Core невозможно отобразить диалоговое окно. Подключаемые модули должны использовать поток устройства для проверки подлинности.
Подключаемый модуль может отправить сообщения журнала в NuGet с инструкциями для пользователя.
Обратите внимание, что ведение журнала доступно после того, как уровень ведения журнала установлен для подключаемого модуля.
NuGet не будет принимать Интерактивные входные данные из командной строки.

Когда клиент вызывает подключаемый модуль с учетными данными получения для проверки подлинности, подключаемые модули должны соответствовать переключателю взаимодействия и соблюдать параметр диалогового окна. 

В следующей таблице приведена сводка поведения подключаемого модуля для всех сочетаний.

| иснонинтерактиве | каншовдиалог | Поведение подключаемого модуля |
| ---------------- | ------------- | --------------- |
| true | true | Параметр Иснонинтерактиве имеет приоритет над параметром диалогового окна. Подключаемому модулю не разрешено открывать диалоговое окно. Это сочетание допустимо только для подключаемых модулей .NET Framework |
| true | false | Параметр Иснонинтерактиве имеет приоритет над параметром диалогового окна. Не допускается блокирование подключаемого модуля. Это сочетание допустимо только для подключаемых модулей .NET Core |
| false | true | Подключаемый модуль должен отображать диалоговое окно. Это сочетание допустимо только для подключаемых модулей .NET Framework |
| false | false | Подключаемый модуль должен отображать диалоговое окно или не может его отобразить. Подключаемый модуль должен использовать поток устройства для проверки подлинности, записывая сообщение инструкции через средство ведения журнала. Это сочетание допустимо только для подключаемых модулей .NET Core |

Перед созданием подключаемого модуля Ознакомьтесь со следующими спецификациями.

- [Подключаемый модуль скачивания пакетов NuGet](https://github.com/NuGet/Home/wiki/NuGet-Package-Download-Plugin)
- [Подключаемый модуль Plat проверки подлинности NuGet](https://github.com/NuGet/Home/wiki/NuGet-cross-plat-authentication-plugin)
