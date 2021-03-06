---
title: Приложения в собраниях Teams
author: laujan
description: Обзор приложений в собраниях Teams на основе роли участника и пользователя
ms.topic: overview
ms.author: lajanuar
keywords: API роли участника для собраний приложений Teams
ms.openlocfilehash: 13fc44e9831cf58f0ab847eab06cc5b99ed8cc70
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796227"
---
# <a name="apps-in-teams-meetings-developer-preview"></a>Приложения в собраниях Teams (разработчик предварительной версии)

>[!IMPORTANT]
> Функции, включенные в Microsoft Teams Preview, предоставляются только для раннего доступа, тестирования и создания отзывов. Они могут быть подвергнуты изменениям, прежде чем стать доступными в общедоступном выпуске и не должны использоваться в рабочих приложениях.

Собрания являются ключевыми для продуктивности в Teams. Они обеспечивают совместную работу, партнерство, информирование о связи и совместную работу на активном форуме. Разработчик может создавать [настраиваемые приложения вкладок](../tabs/what-are-tabs.md#how-do-tabs-work), [Bot](../bots/what-are-bots.md)и [расширений сообщений](../messaging-extensions/what-are-messaging-extensions.md) , чтобы улучшить и расширить возможности для собраний в Teams. Пользователи собраний могут получать доступ к приложениям с помощью коллекции вкладок, позволяя выполнять соответствующие сценарии, такие как предварительная настройка доски Канбан, запуск диалогового окна для проведения собрания или создание опроса после собрания. Ваше приложение для собраний может обеспечить взаимодействие с пользователем для каждого этапа жизненного цикла собрания на основе состояния участника.

Центр расширяемости приложений собраний Teams в трех концепциях:

✔ **Жизненный цикл собраний** — до, во время и после кадра времени собрания.  
**Роль участника** ✔ — организатор собрания, докладчика или участник.  
✔ **Тип пользователя** — пользователь в группах "гость", "гость", "федеративный" или "Аноним".

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a>Сценарии жизненного цикла собраний

## <a name="tabs"></a>Вкладки

> [!IMPORTANT]
> Как и во всех приложениях с вкладками, ваше приложение должно выполнять [процесс проверки подлинности единого входа](../tabs/how-to/authentication/auth-aad-sso.md) Teams для вкладок.

> [!NOTE]
> Мобильные клиенты поддерживают вкладки только на поверхностях предварительных и посылаемых собраний. Скоро будет доступен интерфейс для собраний (диалоговое окно и панель на собрании) на мобильном устройстве.

### <a name="pre-meeting-app-experience"></a>Взаимодействие с приложением перед собранием

**Подготовка к собранию:**

![работа перед собранием](../assets/images/apps-in-meetings/PreMeeting.png)

**Вкладка перед собранием:**

![представление вкладки перед собранием](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ С разрешениями пользователи могут добавлять приложения к собранию через коллекцию вкладок двумя способами:

&emsp;&emsp;&#9679; с помощью вкладки " **сведения** " формы планирования Teams.

&emsp;&emsp;&#9679; с помощью вкладки " **чат** для собраний" в существующем собрании.</br> </br>

Вкладки ✔ доступны на страницах **сведений о** собраниях и **беседах** с помощью кнопки со значком плюс (➕). |

### <a name="in-meeting-app-experience"></a>Взаимодействие с приложением для собраний

✔ Приложения собраний будут размещаться в верхней верхней панели окна Chat и на вкладке "в собрании". Когда пользователи добавляют вкладку на собрание с помощью коллекции вкладок, будут отображаться приложения, находящиеся **во время проведения собрания** .

✔ С разрешениями пользователи могут добавлять приложения во время собрания.

✔ При загрузке в контексте собрания приложения смогут использовать клиентский пакет SDK Teams для доступа к серверам, а также `meetingId` `userMri` `frameContext` для надлежащего отображения интерфейса.

✔ Для приложения могут быть видны в собрании Teams в двух областях:

&emsp;&emsp;&#9679; **боковой панели** . </br>

> [!NOTE]
> Если _манифест приложения_ указывает, что вкладка [оптимизирована для боковой панели](create-apps-for-teams-meetings.md#in-meeting), здесь будет отображаться эта вкладка. Она также может быть частью интерфейса подающего лоток, в соответствии с указанными рекомендациями по проектированию.

&emsp;&emsp;&#9679; **диалоговое окно собраний** . Используйте диалоговое окно "в собрании" для демонстрации действий, выполняемых участниками собрания. *Ознакомьтесь* с разделом [Создание приложений для собраний Teams](create-apps-for-teams-meetings.md).

**Возможности для собраний:**

![взаимодействие с собраниями](../assets/images/apps-in-meetings/in-meeting-experience.png)

![Представление на собрании — диалоговое окно](../assets/images/apps-in-meetings/in-meeting-dialog.png)

**Диалоговое окно с действиями в собрании для пользователей:**

![Представление диалоговых окон](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>Взаимодействие с приложениями после собраний

**Взаимодействие после собрания:**

![представление "опубликовать собрание"](../assets/images/apps-in-meetings/PostMeeting.png)

Сценарий приложения после собрания аналогичен текущему действию, связанному с собранием, с дополнительным преимуществом использования вкладок в области. Пользователи с разрешениями могут добавлять приложения из коллекции вкладок на собрание с помощью вкладки " **сведения** " в форме "Планирование команд" и на вкладке **чат** Meeting в существующем собрании.

### <a name="bots"></a>Боты

В этой статье представлены сведения о реализации [боты в документации по собраниям Teams](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) .

### <a name="messaging-extensions"></a>Расширения для сообщений

Для реализации расширения для обмена сообщениями ознакомьтесь [с нашими расширениями обмена сообщениями в документации по собраниям Teams](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) .

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Роли участников и типы пользователей на собрании

![Участники собрания](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Роли участников

Вы можете разработать приложение с проверкой подлинности, зависящей от участников. Например, возможно, только организатор или докладчик могут создать опрос в собраниях. Несмотря на то, что параметры участников по умолчанию определяются ИТ ИТ администратором, организатору собрания может потребоваться изменить параметры для определенного собрания. Организаторов могут вносить эти изменения на веб-странице параметров собрания.

1. **Организатор** . Организатор планирует собрание, задает параметры собрания, назначает роли собраний и запускает собрание. Только пользователи с учетной записью M365 (обладающими лицензией Teams) могут быть организаторов и управлять разрешениями участников.
1. **Выступающий** . У докладчиков почти те же возможности, что и у организатора; Однако докладчик не может удалить организатора из сеанса или изменить параметры собрания для этого сеанса. По умолчанию участники, присоединяющиеся к собранию, имеют роль докладчика.
1. **Участник** . Участник — это пользователь, приглашенный на собрание, но не уполномоченный выступающий в качестве докладчика. Участники могут взаимодействовать с другими участниками собрания, но не могут управлять параметрами собрания или общими контентом.

_Просмотр_ [ **ролей в собрании Teams**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

Вы можете получить доступ к странице  **параметры собрания** следующим образом:

&#11200; в Teams откройте раздел **Календарь календаря** ![ ](../assets/images/apps-in-meetings/calendar-logo.png) , выберите собрание, а затем — **параметры собрания** .

&#11200; в приглашении на собрание выберите **параметры собрания** .

&#11200; во время собрания Установите флажок **Показывать участников** ![ Отображать значок участников ](../assets/images/apps-in-meetings/show-participants.png) в элементах управления собрания. Затем над списком участников выберите **Управление разрешениями** .

### <a name="user-types"></a>Типы пользователей.

> [!NOTE]
> Пользовательские типы могут присоединяться к собраниям и принимать одну из ролей участника, описанных выше. Тип пользователя не предоставляется в составе API **жетпартиЦипантроле** .

1. **В клиенте** . Эти пользователи принадлежат организации и имеют учетные данные в Azure Active Directory для клиента. Обычно они являются полноценными, сотрудниками или удаленными сотрудниками.
1. **Гость** . Гость — это участник другой организации, который был приглашен на доступ к Teams и другим ресурсам в клиенте Организации. Гости добавляются в Active Directory вашей организации, и им могут быть предоставлены почти все возможности Teams в качестве собственного члена группы с полным доступом к разговорам групп, собраниям и файлам. _Просмотр_ [гостевого доступа в Microsoft Teams](/microsoftteams/guest-access)
1. **Федеративные и внешние** . Федеративный пользователь — это пользователь внешней группы в другой организации, приглашенный на присоединение к собранию. Так как эти пользователи имеют действительные учетные данные с федеративными партнерами, они считаются подлинными в Teams, но не имеют доступа к рабочим группам или другим общим ресурсам Организации. Если вы хотите, чтобы внешние пользователи могли получать доступ к Teams и каналам, гостевой доступ может быть лучший вариант. _Просмотр_ [управления внешним доступом в Microsoft Teams](/microsoftteams/manage-external-access)
1. **Анонимный** доступ. Анонимные пользователи не имеют удостоверения Active Directory и не объединены с клиентом. Анонимный участник похож на внешнего пользователя, но его удостоверение не проецируется на собрание. Анонимные пользователи не смогут получать доступ к приложениям в окне собрания.

## <a name="next-steps"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Создание приложений для собраний групп](create-apps-for-teams-meetings.md)
