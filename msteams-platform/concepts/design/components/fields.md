---
title: Справочные материалы по проектированию
description: Описывает рекомендации по использованию полей и всплывающих подменю в приложениях
keywords: рекомендации по проектированию Teams ссылаются на поля и всплывающие элементы
ms.openlocfilehash: 0f62d38bf961ae79b05c599638cefb3c76f46ed4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "41675597"
---
# <a name="fields-and-flyouts"></a>Поля и всплывающие окна

---

## <a name="fields"></a>Fields

Поля — это области, в которых пользователи могут вводить текст.

### <a name="padding-and-size"></a>Заполнение и размер

Однострочные текстовые поля — это фиксированная высота интервалами по 32, соответствующая высоте других компонентов. Некоторые текстовые поля, такие как поля описания, могут быть вертикально вертикально, что позволяет увеличить количество текста.
[!include[Padding and size](~/includes/design/fields-image-padding.html)]

### <a name="states"></a>Состояния

Ниже приведены состояния наших текстовых полей. Текстовые поля существуют в разных состояниях. У нас есть определенные макеты, предназначенные для девяти возможных сценариев, включая (сверху вниз): размещает текстовое поле, клавиатуру в фокусе и курсоре внутри поля, клавиатуры в фокусе с введенным текстом, обработка ошибок завершена, ошибка обработки, очистка текста поле (включая значок X), поле поиска (включая значок поиска), загрузку поля и отключенное поле.
[!include[Field states](~/includes/design/fields-image-states.html)]

### <a name="formatting-help-text-and-labels"></a>Форматирование текста справки и меток

Поля могут содержать замещающий текст, чтобы получить пример требуемого типа информации. Кроме того, они могут содержать метки, которые предоставляют пользователю дополнительные контексты. В поле текст всегда должен быть выровнен по левому краю. Кроме того, мы используем прописные и строчные буквы.

Мы используем регулярный пользовательский интерфейс в 12 пт (заголовок) и $app-серый-02 для меток. Чтобы получить текст справки, мы используем пользовательский интерфейс Segoe с частотой 14 пт (базовый) и $app-серый-02.
[!include[Fields typography](~/includes/design/fields-image-typography.html)]

---

## <a name="flyouts"></a>Всплывающие окна

Всплывающие окна являются более легковесными, чем диалоговые окна, и их можно быстро закрыть. Они могут содержать кнопки, поля и другие компоненты.
[!include[Flyouts](~/includes/design/flyouts-image.html)]

### <a name="sizing-and-padding"></a>Размер и заполнение

Рекомендуется использовать заполнение 16px слева и справа от содержимого.
[!include[Flyouts size and padding](~/includes/design/flyouts-image-sizepadding.html)]

### <a name="placement"></a>Размещение

Всплывающие окна являются контекстными, и их следует поместить над элементом, вызвавшим его, под ним или рядом с ним.

### <a name="scrolling"></a>Прокрутки

Верхний колонтитул остается на месте, чтобы предоставить контекст для прокручиваемого контента.
[!include[Flyouts scrolling](~/includes/design/flyouts-image-scrolling.html)]

## <a name="mobile"></a>Mobile

Поля — это поля ввода текста, которые принимают ввод от пользователей. Всплывающие меню — это горизонтальные всплывающие окна, отображаемые в верхней области и которые можно использовать для отображения более подробных сведений об элементе.

### <a name="field-controls"></a>Элементы управления поля

[!include[Mobile fields](~/includes/design/fields-mobile-image.html)]

### <a name="flyout-menu-list-controls"></a>Элементы управления списком всплывающих меню

[!include[Mobile flyout menu controls](~/includes/design/flyout-menu-mobile-image.html)]
