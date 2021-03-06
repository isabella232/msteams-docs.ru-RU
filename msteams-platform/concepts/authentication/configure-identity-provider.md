---
title: Настройка поставщиков удостоверений OAuth 2,0
description: В этой статье описывается настройка поставщиков удостоверений с фокусом на Azure AD
keywords: поставщик удостоверений AAD OAuth для проверки подлинности Teams
ms.openlocfilehash: 799b0c20cda64456a4610acbdbedf758989bee55
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "41675549"
---
# <a name="configuring-identity-providers"></a>Настройка поставщиков удостоверений

## <a name="configuring-an-application-to-use-azure-active-directory-as-an-identity-provider"></a>Настройка приложения для использования Azure Active Directory в качестве поставщика удостоверений

Поставщики удостоверений, поддерживающие OAuth 2,0, не будут выполнять проверку подлинности запросов от неизвестных приложений; приложения должны быть зарегистрированы заранее. Чтобы сделать это с помощью Azure AD, выполните указанные ниже действия.

1. Откройте [портал регистрации приложений](https://ms.portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade).

2. Выберите свое приложение, чтобы просмотреть его свойства, или нажмите кнопку "создать регистрацию". Найдите раздел **URI перенаправления** для приложения.

3. Убедитесь, что в раскрывающемся меню выбран пункт **веб** . Обновите URL-адрес конечной точки проверки подлинности. Для примеров приложений TypeScript/Node. js и C# на сайте GitHub URL-адреса перенаправления будут выглядеть следующим образом:

    URL-адреса перенаправления:`https://<hostname>/bot-auth/simple-start`

Замените `<hostname>` фактическим узлом. Это может быть выделенный сайт, такой как Azure, сбой, или ngrok туннель для localhost на компьютере для разработки, `abcd1234.ngrok.io`например. Эта информация может отсутствовать, если вы не выполнили или не развернули ваше приложение (или пример приложения, упомянутого выше), но всегда можете вернуться на эту страницу, если эта информация известна.

## <a name="other-authentication-providers"></a>Другие поставщики проверки подлинности

* **LinkedIn** Следуйте инструкциям в статье [Настройка приложения LinkedIn](https://developer.linkedin.com/docs/oauth2)

* **Google** Получение учетных данных клиента OAuth 2,0 из [консоли Google API](https://console.developers.google.com/)
