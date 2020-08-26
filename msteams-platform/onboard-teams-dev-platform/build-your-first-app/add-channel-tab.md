---
title: Создание вкладки канала для Teams
author: heath-hamilton
description: Узнайте, как создать вкладку канала в первом приложении Microsoft Teams.
ms.topic: tutorial
ms.openlocfilehash: f0c59328219b5611efc02c9eb04db6fdc517ca08
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652169"
---
# <a name="create-a-channel-tab-for-teams"></a>Создание вкладки канала для Teams

В этом руководстве рассказывается, как создать базовую *вкладку канала*, страницу содержимого в полноэкранном режиме для канала команды или чата. В отличие от вкладки личных сведений, пользователи могут настроить некоторые аспекты вкладки канала (например, переименовать вкладку, чтобы она была осмысленной для канала).

## <a name="before-you-begin"></a>Прежде чем начать

Чтобы начать работу, вам потребуется базовое работающее приложение. Если у вас его нет, следуйте инструкциям в статье [Build и запустите первое приложение Teams](build-and-run-with-toolkit.md). При создании проекта приложения выберите параметр только **вкладка "Группа" или "канал Teams"** .

## <a name="your-assignment"></a>Ваше назначение

Не давно, ваша организация создала вкладку команды со сведениями о том, как обращаться к важным функциям (служба технической поддержки, HR и т. д.). Тем не менее, так как вкладка была создана только для личного использования, каждый пользователь должен установить эту вкладку, чтобы ее увидеть, а уровень внедрения меньше ожидаемого. Другими словами, слишком много сотрудников по-прежнему не знают, как связаться со службой поддержки.

Вы можете упростить поиск этих сведений путем создания вкладки канала, которая будет изменять нагрузку, требующую от всех пользователей устанавливать приложение. Вместо этого один пользователь может установить вкладку в канале или чат, чтобы воспользоваться преимуществами всей группы.

## <a name="what-youll-learn"></a>Что вы узнаете

> [!div class="checklist"]
>
> * Определение манифеста приложения и компонентов формирования шаблонов, относящихся к вкладкам каналов
> * Создание контента для вкладки
> * Создание контента для страницы конфигурации вкладки
> * Настройка и установка вкладки
> * Ввод предлагаемого имени вкладки

## <a name="identify-relevant-app-manifest-and-scaffolding-components"></a>Определение соответствующего манифеста приложения и компонентов формирования шаблонов

Во многих вкладках каналов формирование шаблонов и манифеста приложения автоматически настраивается при создании проекта с помощью набора инструментов Teams. Рассмотрим основные компоненты для создания вкладки канала.

### <a name="app-manifest"></a>Манифест приложения

В следующем фрагменте манифеста приложения показано [`configurableTabs`](../../resources/schema/manifest-schema.md#configurabletabs) , в том числе свойства и значения по умолчанию, относящиеся к вкладкам канала.

```JSON
    "configurableTabs": [
        {
            "configurationUrl": "{baseUrl0}/config",
            "canUpdateConfiguration": true,
            "scopes": [
                "team",
                "groupchat"
            ]
        }
    ],
```

* `configurationUrl`: URL-адрес узла для страницы настройки вкладки (должен быть HTTPS).
* `canUpdateConfiguration`: Если задано значение `true` , пользователи могут изменять параметры вкладок, переименовывать вкладку или удалять ее из канала или чата.
* `scopes`: Указывает, могут ли пользователи устанавливать приложение в каналах ( `team` ) и чата ( `groupchat` ). Необходимо указать по крайней мере одно значение.

### <a name="app-scaffolding"></a>Формирование шаблонов приложений

Формирование шаблонов приложений предоставляет `TabConfig.js` файл, расположенный в `src/components` каталоге проекта, для отображения страницы конфигурации вкладки (больше в скором времени).

## <a name="create-your-tab-content"></a>Создание содержимого вкладки

Откройте манифест приложения ( `manifest.json` ) и задайте следующие свойства в разделе [`staticTabs`](../../resources/schema/manifest-schema.md#statictabs) , определяющем страницу содержимого вкладки.

```JSON
    "staticTabs": [
        {
            "entityId": "index",
            "name": "My Contacts",
            "contentUrl": "{baseUrl0}/tab",
            "scopes": [ "personal" ]
        }
    ],
```

Скопируйте и обновите следующий фрагмент кода, используя сведения, которые относятся к вашей организации, или, в целях простоты, используйте код как есть.

```JSX
  <div>
    <h1>Important Contacts</h1>
      <ul>
        <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
        <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
        <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
      </ul>
  </div>
```

Перейдите в `src/components` каталог и откройте его `Tab.js` . Нахождение `render()` функции и вставка содержимого внутри `return()` (как показано на рисунке).

```JavaScript
  render() {

      let userName = Object.keys(this.state.context).length > 0 ? this.state.context['upn'] : "";

      return (
      <div>
        <h1>Important Contacts</h1>
          <ul>
            <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
            <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
            <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
          </ul>
      </div>
      );
  }
```

Добавьте следующее правило, чтобы `App.css` ссылки электронной почты легче читались независимо от того, какая тема используется.

```CSS
  a {
    color: inherit;
  }
```

## <a name="create-your-tab-configuration-page"></a>Страница "Создание конфигурации вкладки"

На каждой вкладке канала есть страница конфигурации, которая является модальной и по крайней мере с одним параметром установки, который отображается при установке приложения. По умолчанию на странице конфигурации запрашиваются пользователи, хотят ли они уведомлять канал или чат при установке вкладки.

Добавьте содержимое на страницу конфигурации. Перейдите в `src/components` каталог проекта, откройте `TabConfig.js` и вставьте содержимое внутри `return()` (как показано на рисунке).

```JavaScript
    return (
        <div>
          <h1>Add My Contoso Contacts</h1>
          <div>
            Select <b>Save</b> to add our organization's important contacts to this workspace.
          </div>
        </div>
    );
```
 
> [!TIP]
> Как минимум, укажите некоторые краткие сведения о приложении на этой странице, так как это может быть первый раз, когда пользователи узнают об этом. Кроме того, можно включить настраиваемые параметры конфигурации или [Рабочий процесс проверки подлинности](../../tabs/how-to/authentication/auth-aad-sso.md), который распространен на страницах настройки вкладок.

## <a name="allow-the-tab-to-be-configured-and-installed"></a>Настройка и установка вкладки

Для успешной настройки и установки вкладки канала необходимо добавить URL-адрес узла, который вы настроили при [создании и запуске первого приложения](build-and-run-with-toolkit.md) в компоненте страницы конфигурации.

Перейдите к разделу `TabConfig.js` и выберите `microsoftTeams.settings.setSettings` . Для `"contentUrl"` замените `localhost:3000` часть URL-адреса на домен, в котором размещается содержимое вкладки (как показано на рисунке).

```JavaScript
    microsoftTeams.settings.setSettings({
      "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
    });
```

Кроме того, убедитесь, что `microsoftTeams.settings.setValidityState(true);` . По умолчанию он имеет значение, но если для этого параметра задано значение `false` , то кнопка **сохранить** на странице Конфигурация отключена.

## <a name="provide-a-suggested-tab-name"></a>Ввод предлагаемого имени вкладки

При установке вкладки для личного использования отображаемым именем является `name` свойство в `staticTabs` части манифеста приложения (например, " **Мои контакты**"). При установке вкладки канал по умолчанию отображается имя приложения (например, **First-App**).

Это может быть разумно в зависимости от того, что вы назначите для вашего приложения, но вы можете указать имя, которое лучше в контексте совместной работы группы (например, " **Контакты группы**").

В `TabConfig.js` , вернитесь к `microsoftTeams.settings.setSettings` . Добавьте `suggestedDisplayName` свойство с именем вкладки, которое будет отображаться по умолчанию (как показано). Используйте предоставленное имя или создайте собственное. Помните, что в манифесте вы можете разрешить пользователям изменять имя, если это необходимо.

```JavaScript
    microsoftTeams.settings.setSettings({
      "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
      "suggestedDisplayName": "Team Contacts"
    });
```

## <a name="view-the-channel-tab"></a>Просмотр вкладки "канал"

Чтобы просмотреть страницы конфигурации и контента на вкладке канала, необходимо установить его в канале или чате.

1. В клиенте Teams выберите **приложения**.
1. Выберите **Отправить настраиваемое приложение** и выберите приложение `Development.zip` .
1. Выберите команду **Добавить в группу** или **Добавить в чат** , а затем выберите канал или чат, который вы можете использовать для тестирования.
1. Выберите **Настройка вкладки**. Отобразится страница Конфигурация.

:::image type="content" source="../doc-links/images/channel-tab-tutorial-content.png" alt-text="Пример снимка экрана со страницей конфигурации вкладки канала":::

После выбора параметра **сохранить** для настройки вкладки отображается содержимое.

![Пример снимка экрана с вкладкой канала со статическим содержимым](../doc-links/images/channel-tab-tutorial-content-installed.png)

## <a name="well-done"></a>Прекрасно

Поздравляем! У вас есть приложение Teams с вкладкой канал для отображения содержимого в каналах и беседах.

## <a name="learn-more"></a>Дополнительные сведения

* [Проверка подлинности пользователей вкладки с единым входом](../../tabs/how-to/authentication/auth-aad-sso.md): Если вы хотите, чтобы авторизованные пользователи просматривали вкладку, настройте единый вход (SSO) через Azure Active Directory (AD).
* [Внедрение контента из существующего веб-приложения или веб-страницы](../../tabs/how-to/add-tab.md#tab-requirements): мы показали, как создать новое содержимое для вкладки личных данных, но вы также можете загрузить контент с внешнего URL-адреса.
* [Создайте простой интерфейс для вкладки](../../tabs/design/tabs.md): Ознакомьтесь с рекомендациями по проектированию вкладок Teams.
* [Создание вкладок для мобильных устройств](../../tabs/design/tabs-mobile.md): Узнайте, как разрабатывать вкладки для смартфонов и планшетов.