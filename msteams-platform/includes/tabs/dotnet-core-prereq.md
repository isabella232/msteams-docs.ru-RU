## <a name="prerequisites"></a>Предварительные требования

- Для выполнения этого руководства вам потребуется клиент Office 365 и группа, настроенная с разрешенной *отправкой пользовательских приложений* . Чтобы узнать больше, ознакомьтесь со статьей [Подготовка клиента Office 365](~/concepts/build-and-test/prepare-your-o365-tenant.md).
  - Если у вас в настоящее время нет учетной записи Office 365, вы можете получить бесплатную подписку в [программе для разработчиков office 365](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program). Подписка останется активной до тех пор, пока вы ее используете для текущей разработки.

- Вы будете использовать приложение App Studio для импорта приложения в Teams. Чтобы установить приложение App Studio **выберите приложение** ![Store](~/assets/images/tab-images/storeApp.png) App Store в левом нижнем углу приложения Teams, а затем выполните поиск в App Studio. Найдя плитку, выберите ее и нажмите кнопку установить в диалоговом окне всплывающее окно.

Кроме того, для этого проекта необходимо установить следующие компоненты в среде разработки:

- Текущая версия Visual Studio IDE с установленной **базовой межплатформенной** рабочей нагрузкой .NET. Если у вас еще нет Visual Studio, вы можете скачать и установить последнюю версию [сообщества Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads) для бесплатной версии.

- Средство обратного прокси-сервера [ngrok](https://ngrok.com) . Вы будете использовать ngrok для создания туннеля к общедоступным конечным точкам HTTPS на локальном веб-сервере. Вы можете [скачать его здесь](https://ngrok.com/download).
