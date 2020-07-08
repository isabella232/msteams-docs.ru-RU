---
title: Создание приложений с помощью набора инструментов Microsoft Teams и кода Visual Studio
description: Приступая к созданию привлекательных пользовательских приложений непосредственно в Visual Studio Code с помощью набора инструментов Microsoft Teams
keywords: набор средств Visual Studio Code Toolkit для Teams
ms.date: 06/30/2020
ms.openlocfilehash: 17f21d1656b32074318030b9df9e643200f58f80
ms.sourcegitcommit: ecf7ca8e77e77fe3f4cad1b13e3d31a825155555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2020
ms.locfileid: "45054254"
---
# <a name="build-apps-with-the-microsoft-teams-toolkit-and-visual-studio-code"></a>Создание приложений с помощью набора инструментов Microsoft Teams и кода Visual Studio

Набор средств Microsoft Teams позволяет создавать пользовательские приложения Teams непосредственно в среде Visual Studio Code. Набор средств поможет вам выполнить все действия, необходимые для создания, отладки и запуска приложения Teams.

## <a name="installing-the-teams-toolkit"></a>Установка набора инструментов Teams

Набор средств Microsoft Teams для Visual Studio Code доступен для загрузки с [Visual Studio Marketplace](https://aka.ms/teams-toolkit) или напрямую в виде расширения в Visual Studio Code.

> [!TIP]
> После установки вы должны увидеть набор инструментов Teams на панели действий Visual Studio Code. Если это не так, щелкните правой кнопкой мыши на панели действий и выберите **Microsoft Teams** , чтобы закрепить набор инструментов для упрощения доступа.

## <a name="using-the-toolkit"></a>Использование набора средств

- [Настройка нового проекта](#set-up-a-new-teams-project)
- [Импорт существующего проекта](#import-an-existing-teams-app-project)
- [Настройка приложения](#configure-your-app)
- [Упаковка приложения](#package-your-app)
- [Запуск приложения в Teams](#run-your-app-in-teams)
- [Проверка приложения](#validate-your-app)
- [Публикация приложения](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Настройка нового проекта Teams

1. Создайте рабочую область или папку для проекта в локальной среде.
1. В Visual Studio Code выберите значок команды ![Значок Teams](../assets/icons/favicon-16x16.png) на панели действий в левой части окна.
1. Выберите **Открыть набор инструментов Microsoft Teams** в меню команд.
1. Выберите **создать приложение Teams** из меню команд.
1. При появлении соответствующего запроса введите имя рабочей области. Он будет использоваться в качестве имени папки, в которой будет размещаться проект, и именем приложения по умолчанию.
1. Нажмите клавишу **Ввод** , и вы будете доставлены на экране **добавить возможности** настройте свойства нового приложения.
1. Нажмите кнопку **Готово** , чтобы завершить процесс настройки.

## <a name="import-an-existing-teams-app-project"></a>Импорт существующего проекта приложения Teams

1. В Visual Studio Code выберите значок команды ![Значок Teams](../assets/icons/favicon-16x16.png) на панели действий в левой части окна.
1. Выберите пункт **Импорт пакета приложения** в меню команда.
1. Выберите существующий ZIP-файл [пакета приложения Teams](../concepts/build-and-test/apps-package.md) .
1. Нажмите кнопку **выбрать пакет публикации** . Теперь на вкладке Конфигурация набора средств необходимо заполнить сведения о приложении.
1. В Visual Studio Code выберите **файл**  ->  **Добавить папку в рабочую область** , чтобы добавить каталог с исходным кодом в рабочую область Visual Studio Code.

## <a name="configure-your-app"></a>Настройка приложения

В основном приложение Teams поработает с тремя компонентами:

  1. Клиент Microsoft Teams (веб-сайт, Настольный компьютер или мобильное устройство), на котором пользователи взаимодействуют с вашим приложением.
  1. Сервер, который отвечает на запросы для контента, который будет отображаться в Teams, например, контент вкладки HTML или адаптивной карточки Bot.
  1. [Пакет приложения](/concepts/build-and-test/apps-package.md) Teams состоит из трех файлов:

  > [!div class="checklist"]
  >
  > - manifest.jsна 
  > - [Значок цвета](../resources/schema/manifest-schema.md#icons) приложения для отображения в каталоге приложений "общедоступный" или "Организация"
 > - [Значок структуры](../resources/schema/manifest-schema.md#icons) для отображения на панели активности Teams.

При установке приложения клиент Teams анализирует файл манифеста, чтобы определить необходимые сведения, такие как имя вашего приложения и URL-адрес, по которому расположены службы.

1. Чтобы настроить приложение, перейдите на вкладку **набор инструментов Microsoft Teams** в Visual Studio Code.
1. Выберите команду **изменить пакет приложения** , чтобы просмотреть страницу **сведений о приложении** .
1. Изменение полей на странице "сведения о приложении" обновляет содержимое manifest.jsв файле, который в конечном итоге будет поставляться в составе пакета приложения. [Подробнее](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a>Упаковка приложения

Изменение страницы **сведений о приложении** или обновление **манифеста**, или **env** -файлов в папке **публикации** приложения автоматически создаст файл **Development.zip** . Необходимо включить [два значка](../concepts/build-and-test/apps-package.md#icons) в одну и ту же папку.

## <a name="install-and-run-your-app-locally"></a>Установка и запуск приложения на локальном компьютере

Для получения подробных инструкций по упаковке и тестированию приложения обратитесь к главной странице "**Построение и запуск* контента в проекте". В общем случае необходимо установить сервер приложения, заставить его работать, а затем настроить туннельное решение, чтобы Teams могла получить доступ к содержимому, запущенному с localhost.

## <a name="add-a-trusted-certificate-for-localhost"></a>Добавление доверенного сертификата для localhost

Если вы хотите отладить приложение на основе вкладки на localhost с использованием HTTPS, вам потребуется добавить сертификат для localhost в `Trusted Root Certification Authorities` каталог. Этот шаг необходимо выполнить только один раз для каждого компьютера.</br></br>

**Создайте и установите доверенный сертификат:**
<details>
  <summary>Разверните здесь</summary>

* Построение и запуск приложения
  * Следуйте инстуктионс в разделе **Build and run** файла Readme проекта, чтобы он был обслужен https://localhost:3000/tab . Как правило, в этом случае `npm install` будет выполняться`npm start`
  * Переход https://localhost:3000/tab из Google Chrome

* Получение SSL-сертификата:
  * Откройте окно инструменты разработчика Chrome ( `ctrl + shift + i`  /  `cmd + option + i` ).
  * Щелкните `Security` вкладку
  * Нажмите кнопку включить `View certificate` , чтобы скачать сертификат, перетащив его на Рабочий стол в OS X или щелкнув `Details` вкладку в Windows, а затем щелкнув`Copy to File…`
  * Назовите файл <*что-либо*>. cer и сохраните его в папку, не требующую согласия администратора для выполнения действия Write.
  
* Установка сертификата в **Windows**
  * Выберите `DER encoded binary X.509 (.CER)` параметр (первый) и сохраните его.
  * Дважды щелкните сертификат и установите его.
  * Задать`Local Machine`
  * Перейдите`Place all certificates in the following store`
  * Задать`Trusted Root Certification Authorities`
  * Подтверждение установки
  
* Установка **Mac OS X OS X**
  * В OS X Откройте служебную программу доступа к цепочке ключей и выберите `System` из меню слева. Щелкните значок замка, чтобы включить изменения.
  * Нажмите кнопку со знаком "плюс" рядом с пунктом Добавление нового сертификата и выберите `localhost.cer` файл, который вы перетащили на Рабочий стол. Щелкните `Always Trust` в появившемся диалоговом окне.
  * После добавления сертификата в цепочку ключей системы дважды щелкните сертификат и разверните `Trust` раздел сведений о сертификате. Выберите `Always Trust` для каждого параметра.

> [!IMPORTANT]
> Если вы получаете предупреждение сертификата безопасности, перейдите по адресу https://localhost:3000/tab . Если сайт по-прежнему не является доверенным, перезагрузите компьютер, и localhost должен быть принят как доверенный.
</details>

## <a name="run-your-app-in-teams"></a>Запуск приложения в Teams
- Предварительные требования:
  - [Включение режима предварительного просмотра для разработчиков Teams](https://aka.ms/teams-toolkit-enable-devpreview)

1. Перейдите на панель действий в левой части окна кода Visual Studio.
1. Выберите значок **Run (выполнить** ) для отображения представления " **Запуск" и "Отладка** ".
1. Вы также можете использовать сочетание клавиш `Ctrl+Shift+D` .

## <a name="validate-your-app"></a>Проверка приложения

Страница **проверки** позволяет проверить пакет приложения перед отправкой приложения в AppSource. Просто отправьте пакет манифеста, и средство проверки проверит ваше приложение на соответствие всем тестовым случаям, связанным с манифестом. Для каждого неудачных тестов в описании представлена ссылка на документацию, которая поможет исправить ошибку. Для тестов, которые трудно автоматизировать, **Предварительный контрольный список** включает 7 наиболее распространенных тестовых случаев, а также ссылки на полный контрольный список отправки.

## <a name="publish-your-app-to-teams"></a>Публикация приложения в Teams

На домашней странице проекта вы можете отправить свое приложение в группу, отправить свое приложение в пользовательскую магазин приложений для пользователей в вашей организации или отправить свое приложение в источник приложений для всех пользователей Teams. ИТ ИТ ИТ, просматривая эти отправки. Вы можете вернуться на страницу *публикации* , чтобы проверить состояние отправки, а также узнать, было ли ваше приложение утверждено или отклонено вашим ИТ-администратором. Кроме того, здесь вы будете передавать обновления в свое приложение или отменять все активные в данный момент отправки.

> [!div class="nextstepaction"]
> [Следующий шаг: обслуживание и поддержка опубликованного приложения](../concepts/deploy-and-publish/appsource/post-publish/overview.md)