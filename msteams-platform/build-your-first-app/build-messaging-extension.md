---
title: Создание расширения для обмена сообщениями в Teams
author: heath-hamilton
description: Узнайте, как создать расширение для обмена сообщениями для первого приложения Microsoft Teams.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
ms.openlocfilehash: 0475fcea7d865849fa60c5b3b23788bf90ee5e25
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210317"
---
# <a name="build-a-teams-messaging-extension"></a>Создание расширения для обмена сообщениями в Teams

Существует два типа *расширений для обмена сообщениями*в teams: [команды поиска](../messaging-extensions/how-to/search-commands/define-search-command.md) и [команды действий](../messaging-extensions/how-to/action-commands/define-action-command.md).

На этом занятии вы создадите *команду поиска* (также называемую *расширением обмена сообщениями на основе поиска*), которая является ярлыком для поиска внешнего контента и предоставления общего доступа к ним в Teams. Пользователи могут получить доступ к командам поиска из [поля "Создание команд" или "команда"](../messaging-extensions/what-are-messaging-extensions.md).

## <a name="your-assignment"></a>Ваше назначение

Служба технической поддержки организации взаимодействуют с пользователями в Teams, но эти билеты размещаются в отдельной системе. Это означает, что сотрудники службы поддержки должны постоянно переходить между приложениями и перемещаться между ними. Вы узнаете, как можно уменьшить это большое количество контекстных переключений, создав простой модуль обмена сообщениями на основе поиска для Teams.

## <a name="what-youll-learn"></a>Что вы узнаете

> [!div class="checklist"]
>
> * Создание проекта приложения и расширения обмена сообщениями Bot с помощью набора инструментов Microsoft Teams для Visual Studio Code
> * Определите свойства манифеста приложения и некоторые шаблоны формирования шаблонов, относящиеся к расширениям обмена сообщениями.
> * Локальное размещение приложения
> * Настройка почтового робота для расширения обмена сообщениями
> * Загрузка неопубликованных и тестирование расширения обмена сообщениями в Teams

## <a name="before-you-begin"></a>Прежде чем начать

Если вы еще не сделали это, убедитесь, что вы [знаете и установите необходимые компоненты для разработки Teams](build-first-app-overview.md#get-prerequisites).

## <a name="create-your-app-project"></a>Создание проекта приложения

Набор средств Microsoft Teams позволяет настроить следующие компоненты для расширения системы обмена сообщениями:

* **Манифест приложения и формирование шаблонов,** относящиеся к расширениям обмена сообщениями
* **Bot** для расширения обмена сообщениями, автоматически регистрируемого в службе Microsoft Azure Bot

> [!TIP]
> Если вы еще не создали проект приложения Teams, возможно, вам будет полезно выполнить приведенные [выше инструкции по](../build-your-first-app/build-and-run.md) более подробному объяснению проектов.

1. В Visual Studio Code выберите **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: на левой панели активности и выберите **создать приложение Teams**.
1. Введите имя приложения Teams. (Это имя приложения по умолчанию, а также имя каталога проекта приложения на локальном компьютере.)
1. На экране **добавить возможности** выберите **расширение системы обмена сообщениями** , а затем нажмите **Далее**.
1. На экране **Настройка расширения обмена сообщениями** выполните следующие действия:
    1. Выберите вариант только **на основе поиска** для типа расширения обмена сообщениями.
    1. Выберите **создать новый робот** **и войдите в систему,** используя учетную запись Microsoft 365 для разработки.
    1. Сохраните идентификатор и пароль почтового робота (это необходимо сделать чуть позже).
    1. Необязательно Введите настраиваемое имя для Bot и нажмите кнопку **создать**. (Это не имя уже указанного приложения Teams.)
    1. Пока нажмите кнопку **нет** для параметра link унфурлинг.</br>
:::image type="content" source="../assets/images/build-your-first-app/choose-me-search.png" alt-text="Иллюстрация, на которой показано, как в наборе инструментов Teams войти в свою учетную запись Microsoft 365, чтобы создать новый почтовый робот для расширения обмена сообщениями.":::
1. В нижней части экрана нажмите кнопку **Готово** , чтобы настроить проект.

## <a name="identify-relevant-app-project-components"></a>Определение соответствующих компонентов проекта приложения

Большинство манифестов и шаблонов приложений настраиваются автоматически при создании проекта с помощью набора инструментов Teams.

### <a name="app-manifest"></a>Манифест приложения

В следующем фрагменте кода из манифеста приложения ( `manifest.json` файл в каталоге проекта `.publish` ) показаны свойства и значения по умолчанию, относящиеся к расширениям обмена сообщениями.

```JSON
"composeExtensions": [
    {
        "botId": "{botId0}",
        "canUpdateConfiguration": true,
        "commands": [
            {
                "id": "searchQuery",
                "context": [
                    "compose",
                    "commandBox"
                ],
                "description": "Test command to run query",
                "title": "Search",
                "type": "query",
                "parameters": [
                    {
                        "name": "searchQuery",
                        "title": "Search Query",
                        "description": "Your search query",
                        "inputType": "text"
                    }
                ]
            }
        ]
    }
],
```

Давайте взглянем на некоторые из свойств, которые создает набор средств. (Обратитесь к полному списку поддерживаемых [`composeExtensions`](../resources/schema/manifest-schema.md#composeextensions) свойств.)

* `botId`: Идентификатор созданного робота, созданного вами с помощью настройки проекта. (Хранимая в `{botId0}` , вы можете найти фактический идентификатор в `Development.env` .)
* `commands`: Доступные команды для расширения обмена сообщениями. Набор средств, который обеспечивает формирование шаблонов для команды поиска.
* `context`: Где пользователи могут вызывать расширение системы обмена сообщениями. В этом случае вы можете запустить расширение системы обмена сообщениями из поля команда "создать" или "команда".
* `description`: Текст справки по пользовательскому интерфейсу, указывающий, что делает команда или как ее использовать.
* `parameters`: Включает все параметры, принимаемые командой (по крайней мере одна из них может иметь до пяти).
* `parameters.description`: Текст справки по пользовательскому интерфейсу, описывающий назначение параметра или пример ввода.

### <a name="app-scaffolding"></a>Формирование шаблонов приложений

Формирование шаблонов приложений включает в себя `.env` файл, расположенный в корневом каталоге проекта, в котором ХРАНИТСЯ идентификатор и пароль для ленты расширения обмена сообщениями.

Кроме того, в корневом каталоге существует `botActivityHandler.js` файл для обработки расширения системы обмена сообщениями (или техническим образом [messaging extension's bot](#configuring-the-bot-for-your-messaging-extension)) ответа на поисковые запросы в Teams.

## <a name="set-up-a-secure-tunnel-to-your-app"></a>Настройка безопасного туннеля для приложения

В целях тестирования давайте разместите расширение обмена сообщениями на локальном веб-сервере (порт 3978).

1. В терминале запустите `ngrok http -host-header=rewrite 3978` .
1. Скопируйте URL-адрес HTTPS в выходных данных, так как teams требует HTTPS-подключения.
1. В `.publish` каталоге откройте `Development.env` .
1. Замените `baseUrl0` значение скопированным URL-адресом. (Например, замените `baseUrl0=http://localhost:3000` на `baseUrl0=https://85528b2b3ca5.ngrok.io` .)

Манифест приложения указывает на место размещения ленты, используемой расширением обмена сообщениями.

## <a name="configuring-the-bot-for-your-messaging-extension"></a>Настройка почтового робота для расширения обмена сообщениями

Расширения обмена сообщениями основываются на боты для отправки и обработки запросов пользователей из Teams в размещенную службу.

Робот должен быть зарегистрирован в службе Azure Bot, которая была выполнена при настройке приложения с помощью набора инструментов Teams.

### <a name="specify-your-bot-id-and-password"></a>Указание идентификатора и пароля почтового робота

Когда ваш Bot зарегистрирован в службе Azure Bot, ему назначается идентификатор и пароль, о которых должно знать ваше приложение Teams.

1. Нахождение идентификатора и пароля ленты, сохраненных во время установки набора средств.
1. Откройте файл в корневом каталоге `.env` .
1. Задайте для идентификатора и пароля почтового робота `BotId` Свойства и пароль `BotPassword` соответственно.

### <a name="add-the-bot-endpoint-address"></a>Добавление адреса конечной точки Bot

Необходимо указать URL-адрес конечной точки Bot для получения и обработки поисковых запросов в вашем расширении обмена сообщениями. Как правило, URL-адрес выглядит так `https://HOST_URL/api/messages` : Это можно сделать быстро в наборе инструментов Teams.

1. В Visual Studio Code выберите **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: на левой панели действий, а затем выберите пункт **Открыть набор средств Microsoft Teams**.
1. Перейдите к элементу **управления Bot > существующих регистраций ленты** и выберите элемент управления Bot, созданный во время установки.
1. В поле **адрес конечной точки Bot** введите локальный веб-сервер, на котором размещается Bot ( `baseUrl10` значение), и добавьте `/api/messages` к нему.

Ваш робот сможет обрабатывать запросы в вашем расширении системы обмена сообщениями.

## <a name="run-your-app"></a>Запуск приложения

Вы настроили URL-адрес для размещения своего расширения обмена сообщениями и настройки его для обработки запросов поиска. Самое время заставить ваше приложение работать и работать.

1. В терминале перейдите к корневому каталогу проекта приложения и запустите его `npm install` .
1. Выполните команду `npm start` .

В случае успеха вы увидите нечто вроде следующего сообщения, указывающего на то, что служба расширения обмена сообщениями прослушивает активность `localhost` :

`Bot/ME service listening at http://localhost:3978`

## <a name="sideload-your-messaging-extension-in-teams"></a>Загрузка неопубликованных вашего расширения системы обмена сообщениями в Teams

Если ваш модуль обмена сообщениями работает, вы можете установить его в Teams.

> [!TIP]
> Если вы еще не неопубликованные приложение Teams до и не выпустили проблемы, выполните указанные ниже [действия](../build-your-first-app/build-and-run.md#sideload-your-app-in-teams).

1. Выполните вход в клиент Teams с учетной записью, позволяющей выполнять загрузку неопубликованных приложений.
1. Выберите **приложения**, а затем нажмите кнопку **Отправить пользовательское приложение**.
1. Перейдите в папку проекта приложения `.publish` и выберите `Development.zip` .
1. В модальном окне установки нажмите кнопку **Добавить** , чтобы установить приложение.

## <a name="test-your-messaging-extension"></a>Проверка расширения системы обмена сообщениями

Узнайте, как работают расширения обмена сообщениями в чате Teams.

1. Начните новый сеанс разговора. В поле создать **, а затем выберите** :::image type="icon" source="../assets/icons/teams-client-more.png"::: приложение расширения обмена сообщениями, которое вы только что неопубликованныее.<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-access.png" alt-text="Иллюстрация, на которой показано, как получить доступ к расширению системы обмена сообщениями на основе поиска в поле "Создание Teams".":::
1. Попробуйте выполнить поиск чего-либо (например, "билеты"). Если ваше приложение работает, вы увидите пример результатов поиска (вы можете добавить его позже).<br/>
   :::image type="content" source="../assets/images/build-your-first-app/me-teams-test.png" alt-text="Снимок экрана, демонстрирующий использование расширения обмена сообщениями на основе поиска в поле "Создание Teams".":::

## <a name="well-done"></a>Прекрасно

Поздравляем! У вас есть основные расширения системы обмена сообщениями Teams, которые задают поиск внешнего контента в поле "создать" или "команда".

## <a name="next-steps"></a>Дальнейшие действия

Чтобы продолжить и создать полнофункциональное расширение системы обмена сообщениями, ознакомьтесь со следующими страницами:

1. [Определите команды поиска](../messaging-extensions/how-to/search-commands/define-search-command.md) , связанные со службой.
1. Настройте службу для [реагирования на поиск пользователей](../messaging-extensions/how-to/search-commands/respond-to-search.md).

## <a name="troubleshooting"></a>Устранение неполадок

Приведенные ниже сведения помогут вам устранить проблемы, связанные с выполнением этого руководства.

### <a name="toolkit-setup-fails"></a>Не удается установить набор средств

Когда вы настраиваете проект приложения с помощью набора инструментов Teams, вы получаете сообщение об ошибке после выбора параметра **создать новый элемент Bot** и входа в систему с помощью учетной записи разработчика Microsoft 365.

Это может быть проблема проверки подлинности. Выполните следующие действия, чтобы завершить настройку проекта.

1. В Visual Studio Code выберите **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: на левой панели действий и нажмите **выйти**.
1. Снова пройдите процесс настройки, выполнив вход в систему с той же учетной записью и создав новый элемент Bot.

### <a name="bot-isnt-connected-to-teams"></a>Bot не подключены к Teams

Если вы установили приложение, но оно не работает, убедитесь, что линия канала для расширения обмена сообщениями [подключена к *каналу*команд службы Azure Bot](https://docs.microsoft.com/azure/bot-service/channel-connect-teams?view=azure-bot-service-4.0&preserve-view=true).

Важно понимать, что это не то же самое, что и канал в Teams. В этом случае каналом является способ подключения службы Azure Bot к Teams или другому [поддерживаемому Microsoft или стороннему приложению для общения](https://docs.microsoft.com/azure/bot-service/bot-service-channels-reference?view=azure-bot-service-4.0&preserve-view=true).

## <a name="learn-more"></a>Подробнее

* [Включение функции Link унфурлинг](../messaging-extensions/how-to/link-unfurling.md)
* [Добавить аутентификацию](../messaging-extensions/how-to/add-authentication.md)
* [Создание расширения обмена сообщениями на основе действий](../messaging-extensions/how-to/action-commands/define-action-command.md)
* [Microsoft Bot Framework](https://dev.botframework.com/)