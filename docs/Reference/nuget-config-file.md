---
title: "Справочник по файлу NuGet.Config | Документы Майкрософт"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/25/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Справочник по файлу NuGet.Config, включая разделы config, bindingRedirects, packageRestore, solution и packageSource."
keywords: "файл NuGet.Config, справочник по настройке NuGet, параметры конфигурации NuGet"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 9a183b67ae18f4fa5c042f1806f8abcc9b799b77
ms.sourcegitcommit: 4651b16a3a08f6711669fc4577f5d63b600f8f58
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="nugetconfig-reference"></a>Справочник по NuGet.Config

Для управления работой NuGet используются параметры в различных файлах `NuGet.Config`, как описано в разделе [Настройка поведения NuGet](../consume-packages/configuring-nuget-behavior.md).

`NuGet.Config` — это XML-файл, содержащий узел `<configuration>` верхнего уровня, который, в свою очередь, содержит элементы разделов, описываемые в этой статье. Каждый раздел содержит ноль или более элементов `<add>` с атрибутами `key` и `value`. См. [пример файла конфигурации](#example-config-file). В именах регистр символов не учитывается, а в качестве значений могут использоваться [переменные среды](#using-environment-variables).

В этом разделе.

- [Раздел config](#config-section)
- [Раздел bindingRedirects](#bindingredirects-section)
- [Раздел packageRestore](#packagerestore-section)
- [Раздел solution](#solution-section)
- [Разделы источников пакета](#package-source-sections):
  - [packageSources](#packagesources)
  - [packageSourceCredentials](#packagesourcecredentials)
  - [apikeys](#apikeys)
  - [disabledPackageSources](#disabledpackagesources)
  - [activePackageSource](#activepackagesource)
- [Использование переменных среды](#using-environment-variables)
- [Пример файла конфигурации](#example-config-file)

<a name="dependencyVersion"></a>
<a name="globalPackagesFolder"></a>
<a name="repositoryPath"></a>
<a name="proxy-settings"></a>

## <a name="config-section"></a>Раздел config

Содержит различные параметры конфигурации, которые можно задавать с помощью [команды `nuget config`](../tools/cli-ref-config.md).

Примечание. Параметры `dependencyVersion` и `repositoryPath` применяются только к проектам, в которых используется файл `packages.config`. `globalPackagesFolder`применяется только к проектам, используя формат PackageReference.

| Ключ | Значение |
| --- | --- |
| dependencyVersion (только `packages.config`) | Значение `DependencyVersion` по умолчанию для установки, восстановления и обновления пакета, если параметр `-DependencyVersion` не указан напрямую. Это значение также используется в пользовательском интерфейсе диспетчера пакетов NuGet. Возможные значения: `Lowest`, `HighestPatch`, `HighestMinor`, `Highest`. |
| globalPackagesFolder (проекты, в которых не используется `packages.config`) | Расположение глобальной папки пакетов по умолчанию. Значение по умолчанию — `%USERPROFILE%\.nuget\packages` (Windows) или `~/.nuget/packages` (Mac и Linux). В файлах `Nuget.Config` для конкретных проектов можно использовать относительный путь. |
| repositoryPath (только `packages.config`) | Расположение, в котором следует установить пакеты NuGet вместо папки `$(Solutiondir)/packages` по умолчанию. В файлах `Nuget.Config` для конкретных проектов можно использовать относительный путь. |
| defaultPushSource | Определяет URL-адрес источника пакета или путь к нему, который следует использовать по умолчанию, если другие источники пакета для операции не обнаружены. |
| http_proxy http_proxy.user http_proxy.password no_proxy | Параметры прокси-сервера, которые следует использовать при подключении к источникам пакета; значение `http_proxy` должно иметь формат `http://<username>:<password>@<domain>`. Пароли зашифровываются, и их нельзя добавить вручную. Значение параметра `no_proxy` представляет собой разделенный запятыми список доменов, для которых производится обход прокси-сервера. В качестве этих значений можно также использовать переменные среды http_proxy и no_proxy. Дополнительные сведения см. в записи блога [Параметры прокси-сервера в NuGet](http://skolima.blogspot.com/2012/07/nuget-proxy-settings.html) (skolima.blogspot.com). |

**Пример**:

```xml
<config>
    <add key="dependencyVersion" value="Highest" />
    <add key="globalPackagesFolder" value="c:\packages" />
    <add key="repositoryPath" value="c:\repo" />
    <add key="http_proxy" value="http://company-squid:3128@contoso.com" />
</config>
```

## <a name="bindingredirects-section"></a>Раздел bindingRedirects

Определяет то, производится ли в NuGet автоматическая переадресация привязок при установке пакета.

| Ключ | Значение |
| --- | --- |
| skip | Логическое значение, указывающее, следует ли пропустить автоматическую переадресацию привязок. Значение по умолчанию – false. |

**Пример**:

```xml
<bindingRedirects>
    <add key="skip" value="True" />
</bindingRedirects>
```

## <a name="packagerestore-section"></a>Раздел packageRestore

*Игнорируется в версии 2.7 и более поздних*

Управляет восстановлением пакета во время сборки.

| Ключ | Значение |
| --- | --- |
| enabled | Логическое значение, указывающее, может ли NuGet выполнять автоматическое восстановление. Вы также можете задать переменную среды `EnableNuGetPackageRestore` со значением `True` вместо того, чтобы задавать этот параметр в файле конфигурации. |
| автоматическая | Логическое значение, указывающее, должен ли диспетчер NuGet проверять отсутствие пакетов во время сборки. |

**Пример**:

```xml
<packageRestore>
    <add key="enabled" value="true" />
    <add key="automatic" value="true" />
</packageRestore>
```

## <a name="solution-section"></a>Раздел solution

Определяет то, включается ли папка `packages` решения в систему управления версиями. Этот раздел работает только в файлах `Nuget.Config` в папке решения.

| Ключ | Значение |
| --- | --- |
| disableSourceControlIntegration | Логическое значение, указывающее, следует ли игнорировать папку пакетов при работе с системой управления версиями. Значением по умолчанию является false. |

**Пример**:

```xml
<solution>
    <add key="disableSourceControlIntegration" value="true" />
</solution>
```

## <a name="package-source-sections"></a>Разделы источников пакета

Параметры `packageSources`, `packageSourceCredentials`, `apikeys`, `activePackageSource` и `disabledPackageSources` в совокупности определяют то, как NuGet работает с репозиториями пакетов во время операций установки, восстановления и обновления.

Как правило, для управления этими параметрами используется [команда `nuget sources`](../tools/cli-ref-sources.md), за исключением параметра `apikeys`, который настраивается с помощью [команды `nuget setapikey`](../tools/cli-ref-setapikey.md).

Обратите внимание, что URL-адрес источника для nuget.org — `https://api.nuget.org/v3/index.json`.

### <a name="packagesources"></a>packageSources

Выводит список всех известных источников пакетов.

| Ключ | Значение |
| --- | --- |
| (имя, назначаемое источнику пакета) | Путь к источнику пакета или его URL-адрес. |

**Пример**:

```xml
<packageSources>
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
    <add key="Contoso" value="https://contoso.com/packages/" />
    <add key="Test Source" value="c:\packages" />
</packageSources>
```

### <a name="packagesourcecredentials"></a>packageSourceCredentials

Содержит имена пользователей и пароли источников, которые, как правило, задаются с помощью параметров `-username` и `-password` команды `nuget sources`. По умолчанию пароли зашифровываются, если также не указан параметр `-storepasswordincleartext`.

| Ключ | Значение |
| --- | --- |
| Имя пользователя | Имя пользователя источника в виде обычного текста. |
| пароль | Зашифрованный пароль источника. |
| cleartextpassword | Незашифрованный пароль источника. |

**Пример:**

В файле конфигурации элемент `<packageSourceCredentials>` содержит дочерние узлы для каждого применимого имени источника (пробелы в имени заменяются на `_x0020+`). То есть для источников с именами Contoso и Test Source файл конфигурации содержит следующие значения при использовании зашифрованных паролей:

```xml
<packageSourceCredentials>
    <Contoso>
        <add key="Username" value="user@contoso.com" />
        <add key="Password" value="..." />
    </Contoso>
    <Test_x0020_Source>
        <add key="Username" value="user" />
        <add key="Password" value="..." />
    </Test_x0020_Source>
</packageSourceCredentials>
```

При использовании незашифрованных паролей:

```xml
<packageSourceCredentials>
    <Contoso>
        <add key="Username" value="user@contoso.com" />
        <add key="ClearTextPassword" value="33f!!lloppa" />
    </Contoso>
    <Test_x0020_Source>
        <add key="Username" value="user" />
        <add key="ClearTextPassword" value="hal+9ooo_da!sY" />
    </Test_x0020_Source>
</packageSourceCredentials>
```

### <a name="apikeys"></a>apikeys

Содержит ключи для источников, которые используют проверку подлинности на основе ключей API. Эти ключи задаются с помощью [команды `nuget setapikey`](../tools/cli-ref-setapikey.md).

| Ключ | Значение |
| --- | --- |
| (URL-адрес источника) | Зашифрованный ключ API. |

**Пример**:

```xml
<apikeys>
    <add key="https://MyRepo/ES/api/v2/package" value="encrypted_api_key" />
</apikeys>
```

### <a name="disabledpackagesources"></a>disabledPackageSources

Определяет источники, отключенные в настоящее время. Значение может быть пустым.

| Ключ | Значение |
| --- | --- |
| (имя источника) | Логическое значение, указывающее, отключен ли источник. |

**Пример:**

```xml
<disabledPackageSources>
    <add key="Contoso" value="true" />
</disabledPackageSources>

<!-- Empty list -->
<disabledPackageSources />
```

### <a name="activepackagesource"></a>activePackageSource

*(Только в версиях 2.x; в версиях 3.x и более поздних является нерекомендуемым)*

Определяет текущий активный источник или указывает совокупность всех источников.

| Ключ | Значение |
| --- | --- |
| (имя источника) или `All` | Если ключ представляет имя источника, значением является путь к источнику или его URL-адрес. Если используется ключ `All`, требуется значение `(Aggregate source)`, объединяющее все источники пакетов, которые не отключены. |

**Пример**:

```xml
<activePackageSource>
    <!-- Only one active source-->
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />

    <!-- All non-disabled sources are active -->
    <add key="All" value="(Aggregate source)" />
</activePackageSource>
```

## <a name="using-environment-variables"></a>Использование переменных среды

В значениях `NuGet.Config` можно использовать переменные среды (в NuGet 3.4 и более поздних версиях) для применения параметров во время выполнения.

Например, если переменная среды `HOME` в Windows имеет значение `c:\users\username`, значение параметра `%HOME%\NuGetRepository` в файле конфигурации разрешается в `c:\users\username\NuGetRepository`.

Аналогичным образом, если переменная `HOME` в Mac или Linux имеет значение `/home/myStuff`, параметр `$HOME/NuGetRepository` в файле конфигурации разрешается в `/home/myStuff/NuGetRepository`.

Если переменная среды не найдена, NuGet использует буквальное значение из файла конфигурации.

## <a name="example-config-file"></a>Пример файла конфигурации

Ниже приведен пример файла `NuGet.Config`, в котором демонстрируется ряд параметров.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <config>
        <!--
            Used to specify the default location to expand packages.
            See: nuget.exe help install
            See: nuget.exe help update

            In this example, %PACKAGEHOME% is an environment variable. On Mac/Linux,
            use $PACKAGE_HOME/External as the value.
        -->
        <add key="repositoryPath" value="%PACKAGEHOME%\External" />

        <!--
            Used to specify default source for the push command.
            See: nuget.exe help push
        -->

        <add key="defaultPushSource" value="https://MyRepo/ES/api/v2/package" />

        <!-- Proxy settings -->
        <add key="http_proxy" value="host" />
        <add key="http_proxy.user" value="username" />
        <add key="http_proxy.password" value="encrypted_password" />
    </config>

    <packageRestore>
        <!-- Allow NuGet to download missing packages -->
        <add key="enabled" value="True" />

        <!-- Automatically check for missing packages during build in Visual Studio -->
        <add key="automatic" value="True" />
    </packageRestore>

    <!--
        Used to specify the default Sources for list, install and update.
        See: nuget.exe help list
        See: nuget.exe help install
        See: nuget.exe help update
    -->
    <packageSources>
        <add key="NuGet official package source" value="https://api.nuget.org/v3/index.json" />
        <add key="MyRepo - ES" value="https://MyRepo/ES/nuget" />
    </packageSources>

    <!-- Used to store credentials -->
    <packageSourceCredentials />

    <!-- Used to disable package sources  -->
    <disabledPackageSources />

    <!--
        Used to specify default API key associated with sources.
        See: nuget.exe help setApiKey
        See: nuget.exe help push
        See: nuget.exe help mirror
    -->
    <apikeys>
        <add key="https://MyRepo/ES/api/v2/package" value="encrypted_api_key" />
    </apikeys>
</configuration>
```