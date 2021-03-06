---
title: Начало работы с C#/.нет
description: Приступая к созданию качественных приложений в Microsoft Teams с помощью C#/.нет
keywords: Начало работы с .NET c# CSharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 3aca72a43765036c0014a9e16fa585575fe97b2e
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452846"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-cnet-and-app-studio"></a>Начало работы на платформе Microsoft Teams с C#/.нет и App Studio

Платформа для разработчиков [Microsoft Teams](/microsoftteams/) позволяет легко расширять Teams и самостоятельно интегрировать свои приложения и службы в рабочую область Teams. Затем эти приложения можно распространять на предприятие или в Teams по всему миру.

Для расширения Microsoft Teams вам потребуется создать приложение Microsoft Teams. Приложение Microsoft Teams — это веб-приложение, которое вы размещаете. Затем это приложение можно интегрировать в рабочую область пользователя в Teams.

Это руководство поможет вам приступить к созданию приложения Microsoft Teams с помощью C# в .NET. Вы можете протестировать приложение, загрузив его в группу, для которой у вас есть разрешения, или в тестовый клиент, созданный с помощью программы разработчика Office.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Получение необходимых компонентов

Для выполнения этого руководства необходимо получить следующие инструменты:

- [Установка Git](https://git-scm.com/downloads)
- [Установите Visual Studio](https://www.visualstudio.com/downloads/). Вы можете установить бесплатную версию сообщества.

Если вы видите параметр, который будет добавлен `git` к пути во время установки, нажмите эту кнопку. Это будет удобно.

Проверьте `git` установку, выполнив следующую команду в окне терминала:
> [!NOTE]
> Используйте окно терминала, наиболее удобное для вашей платформы. В этих примерах используется bash, но они будут выполняться на большинстве платформ.

```bash
$ git --version
git version 2.17.1.windows.2

```

Обязательно запустите последнюю версию Visual Studio и установите все обновления, если они отображаются.

Вы можете продолжить использование этого окна терминала для выполнения команд, приведенных в этом руководстве.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Скачать пример

Мы предоставили простой [Hello, World!](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) Пример в C#, чтобы приступить к работе. В окне терминала выполните приведенную ниже команду, чтобы клонировать репозиторий примера на локальный компьютер.

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> Вы можете [разветвление](https://help.github.com/articles/fork-a-repo/) этого [репозитория](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) , если вы хотите изменить и вернуть изменения в GitHub для дальнейшего использования.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Сборка и запуск примера

После клонирования репозитория с помощью Visual Studio откройте файл решения `Microsoft.Teams.Samples.HelloWorld.sln` из корневого каталога примера и щелкните `Build Solution` в `Build` меню. Вы можете запустить пример, нажав `F5` или выбрав `Start Debugging` его в `Debug` меню.

Когда приложение запустится, откроется окно браузера с корневым каталогом запущенного приложения. Вы можете перейти по следующим URL-адресам, чтобы убедиться, что загружаются все URL-адреса приложений:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> Если возникнет ошибка `Could not find a part of the path … bin\roslyn\csc.exe` , попробуйте обновить пакет с помощью команды `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Для получения дополнительных сведений обратитесь [к этому вопросу в сайте StackOverflow](https://stackoverflow.com/questions/32780315) .

## <a name="host-the-sample-app"></a>Размещение примера приложения

Помните, что приложения в Microsoft Teams представляют собой веб-приложения, которые предоставляют одну или несколько возможностей. Чтобы платформа Teams загружала приложение, ваше приложение должно быть достижимо из Интернета. Чтобы приложение было достижимо из Интернета, необходимо разместить приложение. Вы можете разместить его в Microsoft Azure бесплатно или создать туннель для локального процесса на вашем компьютере для разработки с помощью `ngrok` . После завершения хостинга приложения запишите его корневой URL-адрес. Он будет выглядеть примерно так: `https://yourteamsapp.ngrok.io` или `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Туннелирование с помощью ngrok

Для быстрого тестирования можно запустить приложение на локальном компьютере и создать для него туннель через конечную точку веб-сайта. [ngrok](https://ngrok.com) — это бесплатный инструмент, который позволяет вам выполнить именно эту задачу. С помощью ngrok вы можете получить веб-адрес, например `https://d0ac14a5.ngrok.io` (этот URL-адрес — это только пример). Вы можете [скачать и установить](https://ngrok.com/download) ngrok для своей среды. Убедитесь, что вы добавляете его в папку `PATH` .

После установки можно открыть новое окно терминала и выполнить следующую команду для создания туннеля. В примере используется порт 3333, поэтому обязательно указывайте его здесь.

```bash
ngrok http 3333 -host-header=localhost:3333
```

Ngrok прослушивает запросы из Интернета и направляет их в ваше приложение, работающее на порте 3333. Вы можете проверить его, открыв браузер и перейдя на `https://d0ac14a5.ngrok.io/hello` страницу приветствия приложения. Обязательно используйте адрес пересылки, отображаемый в ngrok в сеансе консоли, а не этот URL-адрес.

> [!NOTE]
> Если вы использовали другой порт в описанном выше шаге [Build and run](#build-and-run-the-sample) , убедитесь, что для установки туннеля используется тот же номер порта `ngrok` .
> [!TIP]
> Рекомендуется запустить `ngrok` в другом окне терминала, чтобы оно было запущено без конфликта с приложением, которое позднее потребуется остановить, перестроить и повторно запустить. `ngrok`Сеанс возвратит полезную информацию об отладке в этом окне.

Приложение будет доступно только в текущем сеансе на компьютере разработчика. Если компьютер выключен или перейдет в спящий режим, служба станет недоступна. Помните об этом при совместном использовании приложения для тестирования другими пользователями. Если вам нужно перезапустить службу, она возвратит новый адрес, и вам потребуется обновить все место, где используется этот адрес. Платная версия Ngrok не имеет этого ограничения.

### <a name="host-in-azure"></a>Узел в Azure

Microsoft Azure позволяет размещать приложение .NET на свободном уровне с использованием общей инфраструктуры. Это достаточно для запуска этого `Hello World` примера. Для получения дополнительных сведений ознакомьтесь со статьей [Создание новой бесплатной учетной записи](https://azure.microsoft.com/free/) .

В Visual Studio есть встроенная поддержка развертывания приложений для разных поставщиков, в том числе Azure.

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Обновление учетных данных для размещаемого приложения

Для примера приложения требуются следующие переменные среды, чтобы задать значения, которые вы захотите заметку ранее.

Откройте appsettings.jsфайла. Обновите значение *микрософтаппид* с помощью идентификатора ленты, сохраненного ранее. Обновите *микрософтапппассворд* с помощью сохраненного ранее пароля Bot.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

После внесения этих изменений Перестройте приложение. Если вы используете ngrok, запустите приложение локально и, если вы размещаете в Azure, повторно разверните приложение.

## <a name="configure-the-app-tab"></a>Настройка вкладки "приложение"

После установки приложения в команду его необходимо настроить для отображения контента. Перейдите к каналу в группе, где вы установили пример приложения, и нажмите кнопку **"+"** , чтобы добавить новую вкладку. Затем можно выбрать в `Hello World` списке **Добавить вкладку** . После этого появится диалоговое окно настройки. Это диалоговое окно позволит выбрать вкладку для отображения в этом канале. После выбора вкладки и нажатия на эту вкладку `Save` вы увидите вкладку, `Hello World` загруженную с выбранной вкладкой.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Тестирование ленты в Teams

Теперь вы можете взаимодействовать с роботом в Teams. Выберите канал в группе, в которой вы зарегистрировали свое приложение, и введите `@your-bot-name` . Это называется ** \@ упоминанием**. Любое сообщение, отправляемое в Bot, будет отправлено вам в качестве ответа.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Проверка расширения системы обмена сообщениями

Чтобы проверить расширение системы обмена сообщениями, щелкните три точки под полем ввода в представлении беседы. В меню появится приложение **"Hello World"** . При нажатии на нее отображается множество случайных текстов на экране. Вы можете выбрать один из них и вставить его в беседу.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Выберите один из случайных текстов, и вы увидите карту, отформатированную и готовую к отправке сообщения в нижней части.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
