## <a name="prerequisites"></a>Предварительные требования

- Для выполнения этого руководства вам потребуется клиент Office 365 и группа, настроенная с разрешенной *отправкой пользовательских приложений* . Чтобы узнать больше, ознакомьтесь со статьей [Подготовка клиента Office 365](~/concepts/build-and-test/prepare-your-o365-tenant.md).

  - Если у вас в настоящее время нет учетной записи Office 365, вы можете получить бесплатную подписку в программе для разработчиков Office 365. Подписка останется активной до тех пор, пока вы ее используете для текущей разработки. Ознакомьтесь со статьей [Добро пожаловать в программу для разработчиков Office 365](/OfficeDev/office-dev-program-docs/docs/office-365-developer-program.md).

Кроме того, для этого проекта необходимо установить следующие компоненты в среде разработки:

- Любой текстовый редактор или IDE. Вы можете установить и использовать [Visual Studio Code](https://code.visualstudio.com/download) бесплатно.

- [Node. js/NPM](https://nodejs.org/en/). Следует использовать последнюю версию LTS. Диспетчер пакетов узла (NPM) будет установлен в системе с установкой Node. js.

- После успешной установки Node. js установите пакеты [Yeoman](https://yeoman.io/) и [gulp – CLI](https://www.npmjs.com/package/gulp-cli) , введя в командной строке следующую команду:

```bash
npm install yo gulp-cli --global
```

- Установите генератор приложений Microsoft Teams, введя в командной строке следующую команду:

```bash
npm install generator-teams --global
```

## <a name="generate-your-project"></a>Создание проекта

- Откройте командную строку и создайте новый каталог для проекта со вкладками.

- Чтобы запустить генератор, перейдите к новому каталогу и введите следующую команду:

```bash
yo teams
```

- Далее вы задаете ряд значений, которые будут использоваться в файле **manifest. JSON** приложения:

![снимок экрана открытия генератора](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

**Имя вашего решения**

Это имя проекта. Вы можете принять предложенное имя, нажав клавишу ВВОД.

**Где следует разместить файлы?**

В настоящее время вы находитесь в каталоге проекта. Нажмите клавишу ВВОД.

**Название проекта приложения Microsoft Teams?**

Это имя пакета приложения, которое будет использоваться в манифесте и описании приложения.

**Имя вашей компании? (максимум 32 символов)**

В манифесте приложения будет использоваться название вашей компании.

<br>**Какую версию манифеста вы хотите использовать?**

Выберите схему по умолчанию.

**Введите свой идентификатор партнера Майкрософт (если он есть). (Оставьте пустым для пропуска)**

Это поле не является обязательным и должно использоваться только в том случае, если вы уже участвуете в [сети партнерской корпорации Майкрософт](https://partner.microsoft.com).

**Что вы хотите добавить в проект?**

Выберите ( &ast; ) вкладку.

**URL-адрес, на котором будет размещаться это решение?**

По умолчанию генератор предлагает URL-адрес веб-сайтов Azure. Вы будете тестировать ваше приложение только локально, поэтому для этого краткого руководства не требуется действительный URL-адрес.

**Вы хотите включить тестовую платформу и начальные тесты? (y/N)**

Выберите вариант **не** включать тестовую платформу для этого проекта. Значение по умолчанию: Да; Введите **n**.

**Вы хотите использовать для телеметрии Azure Application Insights? (y/N)**

**Не** включайте [Azure Application Insights](/azure-docs/articles/azure-monitor/app/app-insights-overview.md). Значение по умолчанию — нет; Введите **n**.

**Имя вкладки по умолчанию (максимум 16 символов)?**

Присвойте вкладке имя. Это имя вкладки будет использоваться в рамках проекта в качестве компонента файла или URL-пути.
