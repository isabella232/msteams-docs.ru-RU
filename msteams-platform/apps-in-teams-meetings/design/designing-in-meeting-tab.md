---
title: Создание вкладки собрания
author: heath-hamilton
description: Узнайте, как эффективно проектировать вкладку "в собрании" для Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 402d25e543494636af287bcc2e8a308765b4cea9
ms.sourcegitcommit: df9448681d2a81f1029aad5a5e1989cd438d1ae0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877031"
---
# <a name="design-an-in-meeting-tab"></a>Создание вкладки собрания

Вкладка "в собрании" это холст для расширения совместной работы во время собраний. В зависимости от возможности вкладки Teams участники могут просматривать содержимое приложения и взаимодействовать с ним в выделенном пространстве за пределами этапа собрания с помощью общих представлений или представлений на основе ролей.

## <a name="use-cases"></a>Варианты использования

С помощью вкладки в собрании пользователи могут выполнять следующие действия:

* Предоставление подробной обратной связи (например, Оценка кандидата на задание)
* Быстрое создание опроса, опроса или элемента задачи для участников собрания
* Отображение заметок, относящихся к собранию (например, сведений о менеджере по продажам)

## <a name="example"></a>Пример

В следующем примере показана вкладка на собрании, в которой отображается контент приложения опроса.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-organizer-view.png" alt-text="Пример: вкладка Собрание в собрании может выглядеть с точки зрения организатора собрания.":::

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Просмотр полного сценария (фигма)</a>

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Другие примеры вариантов использования (фигма)</a>

## <a name="anatomy"></a>Составляющие

На вкладке в собрании отображается контент приложения с использованием следующих измерений:

* **Ширина** : 280 пикселей для области вебвиев. В левой и правой сторонах вебвиев есть 20 точек заполнения.
* **Высота** : полный выпуск в нижней части вкладки. Существует 20 точек заполнения между областью вебвиев и заголовком табуляции.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-anatomy.png" alt-text="Иллюстрация, демонстрирующая пользовательский интерфейс Анатомия расширения собрания на вкладке &quot;собрание&quot;." border="false":::

1. **Значок приложения** : точка входа на вкладку "в собрании".
1. **Верхний колонтитул** : включает имя вкладки.
1. **Name** : имя экземпляра вкладки.
1. **Закрыть** : закрывает вкладку. Всегда используйте значок закрытия сверху справа, а не действие в нижнем колонтитуле.
1. **Вебвиев** : отображает весь контент стороннего приложения.

## <a name="behavior"></a>Поведение

### <a name="scale"></a>Масштаб

В настоящее время ширина вкладки "в собрании" исправлена.

### <a name="scrolling"></a>Прокрутки

Вот что нужно знать о прокрутке на вкладке на собрании:

* Эту возможность можно прокручивать только по вертикали.
* Отображается только содержимое, к которому вы выполнили прокрутку (ничего или не ниже).
* Полоса прокрутки является частью содержимого вебвиев.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll.png" alt-text="Иллюстрация, на которой показано, как работает прокрутка содержимого вебвиев на вкладке &quot;в собрании&quot;." border="false":::

### <a name="navigation"></a>Навигация

Для сценариев с слоями навигации или большим содержимым рекомендуется разрешить пользователям переходить на дополнительный слой. Пользователи должны иметь возможность вернуться к предыдущему слою.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav.png" alt-text="Иллюстрация, на которой показано, как работает переход на дополнительный слой на вкладке &quot;в собрании&quot;." border="false":::

## <a name="components"></a>Компоненты

Вкладки на собрании в первую очередь строятся с помощью следующих <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">компонентов пользовательского интерфейса (фигма)</a>, основанных на <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">системе дизайна Fluent</a>.

Компонент | Рекомендации | Пример
 - | - | -
Кнопка | Основные и дополнительные кнопки могут быть средними или малыми | Отправка ответа
Input | Поле для краткого ввода данных пользователем. Текст метки может включать значок  | Введите отзыв
Раскрывающийся список | Выберите один или несколько параметров из списка. Может включать функции поиска и выбора нескольких элементов | Выбор языка
Элементы управления выбором | Используйте флажки для нескольких вариантов или переключателей и переключитесь на один вариант. Для более подробного выбора используйте ползунок | Голосование за опрос
Оповещения | При отображении срочных сообщений, состояния ошибок или предупреждений сообщение должно быть кратким и не прерывать текущую задачу пользователя | Ошибка отображения при отправке ответа

## <a name="theming"></a>Темы

### <a name="colors"></a>Цвета

Используйте <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">рекомендуемую цветовую схему (фигма)</a> для фоновых изображений, переднего плана и состояний.

### <a name="typography"></a>Шрифтовое оформление

Используйте <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Рекомендуемые размеры и веса шрифтов (фигма)</a> для заголовков, основного текста и текста метаданных.

## <a name="best-practices"></a>Рекомендации

### <a name="responsiveness"></a>Отклика

Макеты вкладок на собрании должны иметь возможность масштабироваться до различных размеров. Рассмотрите способ масштабирования вкладки и получения фигуры до, во время и после собрания.

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-before-meeting.png" alt-text="Иллюстрация, на которой показано, что содержимое вкладки &quot;в собрании&quot; выглядит как вкладка полноэкранного экрана перед собранием и после него." border="false":::

#### <a name="before-the-meeting"></a>Перед собранием

Убедитесь, что макет вкладок можно адаптировать к разметке справа или слева для разных языков, а элементы управления перемещаются в правильное расположение. (Макеты перед собраниями также могут применяться к макетам после собраний.)

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-during-meeting.png" alt-text="Иллюстрация, на которой показано, как содержимое вкладки перед собранием сжимается на вкладке &quot;на собрание&quot; во время собрания." border="false":::

#### <a name="during-the-meeting"></a>Во время собрания

Содержимое вкладки регулируется макетом и расположением вкладок на собрании.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Темы

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-do.png" alt-text="Иллюстрация, на которой показано, как создать вкладку в собрании для темной темы, используемой в собраниях Teams." border="false":::

#### <a name="do-design-for-a-dark-theme"></a>Do: дизайн для темной темы

Собрания Teams оптимизированы для темного режима, что позволяет снизить визуальное и пользовательское шум, чтобы пользователи могли сосредоточиться на обсуждении и общем содержимом.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-dont.png" alt-text="Иллюстрация, на которой показано, что не следует использовать цвета, не кондуЦиве в темную тему Teams." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a>Не используйте незнакомые цвета.

Цвета, которые могут пересекаться со средой для собраний, могут отвлекаться от несущего объема в Teams.

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a>Прокрутки

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-do.png" alt-text="Иллюстрация, на которой показано, следует использовать только вертикальные полосы прокрутки на вкладке на собрании." border="false":::

#### <a name="do-scroll-vertically"></a>Do: вертикальная прокрутка

Пользователи предполагают вертикальную прокрутку в Teams (и в других местах).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-dont.png" alt-text="Иллюстрация, на которой показано, не следует разрешать горизонтальную прокрутку на вкладке на собрании." border="false":::

#### <a name="dont-scroll-horizontally"></a>Не: прокручивать по горизонтали

Горизонтальная полоса прокрутки не является ожидаемым поведением в Teams. Другие холсты в среде проведения собраний прокручиваются вертикально.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Макет

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-do.png" alt-text="Иллюстрация, на которой показан рекомендуемый макет с одним столбцом на вкладке &quot;в собрании&quot;." border="false":::

#### <a name="do-single-columns"></a>Do: Single Columns

При наличии узкой природы вкладки в собрании настоятельно рекомендуется отобразить содержимое в отдельном столбце.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-dont.png" alt-text="Иллюстрация, на которой показано, что макет с двумя столбцами на вкладке на собрании не подходит." border="false":::

#### <a name="dont-multiple-columns"></a>Не: несколько столбцов

Из-за ограниченного пространства вкладки в собрании не рекомендуется использовать макеты с несколькими столбцами.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Навигация

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-do.png" alt-text="Иллюстрация, на которой показано, следует всегда предоставлять кнопку &quot;назад&quot;, если в приложении вкладки на собрании есть несколько уровней навигации." border="false":::

#### <a name="do-have-a-back-button"></a>Do: кнопка "назад"

Если имеется несколько уровней навигации, пользователи должны иметь возможность вернуться к предыдущему представлению.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-dont.png" alt-text="Иллюстрация, на которой показано, как добавление новой кнопки &quot;Закрыть&quot; на вкладке &quot;на собрание&quot; для навигации является избыточной и может привести к возникновению проблем." border="false":::

#### <a name="dont-include-another-close-button"></a>Не: включить еще одну кнопку "Закрыть"

Предоставление возможности закрыть содержимое вкладки собраний может привести к проблемам, так как в заголовке уже есть кнопка Закрыть для закрытия вкладки в собрании.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-caution.png" alt-text="Иллюстрация, на которой показано, что при использовании модальных модальек (например, модулей задач) на вкладке на собрании задано ограниченное пространство." border="false":::

#### <a name="caution-using-dialogs-in-a-narrow-space"></a>Внимание! использование диалоговых окон в узком пространстве

Диалоговые окна, такие как модули задач, на вкладке уже более узкое собрание могут переносить и скрывать содержимое.

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a>Специальные возможности

Сведения о специальных возможностях содержатся в разделе <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">фигма</a>.

## <a name="resources"></a>Ресурсы

* <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Файл фигма для расширений собраний Microsoft Teams</a>
* [Рекомендации по проектированию вкладок](../../tabs/design/tabs.md)
* [Рекомендации по проектированию вкладок для мобильных устройств](../../tabs/design/tabs-mobile.md)

## <a name="validate-your-design"></a>Проверка проекта

Если вы планируете опубликовать свое приложение в AppSource, следует изучить проблемы, которые обычно приводят к сбою приложений во время отправки.

> [!div class="nextstepaction"]
> [Проверка рекомендаций по проверке макета](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
