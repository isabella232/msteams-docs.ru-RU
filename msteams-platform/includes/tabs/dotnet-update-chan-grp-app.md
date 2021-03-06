### <a name="_layoutcshtml"></a>_Layout. cshtml

Чтобы вкладка отображалась в Teams, необходимо включить **клиентский пакет SDK Microsoft Teams** для `microsoftTeams.initialize()` JavaScript и включить вызов после загрузки страницы. Это способ общения вкладки и клиента teams:

- Перейдите к **общей** папке, откройте **_layout. cshtml**и добавьте следующий `<head>` тег в тег:

```html
<script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
```

>[!IMPORTANT]
>Не копируйте `<script src="...">` URL-адреса с этой страницы, так как они могут не представлять последнюю версию. Чтобы получить последнюю версию пакета SDK, всегда переходите по адресу: [API JavaScript для Microsoft Teams](https://www.npmjs.com/package/@microsoft/teams-js.com).

### <a name="tabcshtml"></a>TAB. cshtml

Откройте **вкладку. cshtml** и обновите внедренный `<script>` код следующим образом:

- В верхней части сценария вызовите метод `microsoftTeams.initialize()`.

- Обновите `websiteUrl` значения `contentUrl` и значения в каждой функции с помощью URL-адреса ngrok HTTPS на вкладке.

Теперь код должен выглядеть следующим образом с помощью **y8rCgT2b** , заменяя URL-адресом ngrok:

```javascript
    microsoftTeams.initialize();

    let saveGray = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                entityId: "grayIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }

    let saveRed = () => {
        microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
            microsoftTeams.settings.setSettings({
                websiteUrl: `https://y8rCgT2b.ngrok.io`,
                contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                entityId: "redIconTab",
                suggestedDisplayName: "MyNewTab"
            });
            saveEvent.notifySuccess();
        });
    }
```

Обязательно сохраните обновленный элемент **TAB. cshtml**.

## <a name="build-and-run-your-application"></a>Построение и запуск приложения

- В Visual Studio нажмите клавишу **F5**или в меню **Отладка** выберите команду **начать отладку** . Убедитесь, что **ngrok** работает и правильно работает, открыв браузер и перейдя на страницу содержимого с помощью URL-адреса ngrok HTTPS, который был предоставлен в окне командной строки.

>[!TIP]
>Для выполнения этого краткого руководства необходимо одновременное выполнение приложения в Visual Studio и ngrok. Если вам нужно прекратить работу приложения в Visual Studio для работы с ним, **продолжите работу ngrok**. Он будет продолжать прослушивать и возобновить маршрутизацию запроса приложения при его перезапуске в Visual Studio. Если вам потребуется перезапустить службу ngrok, она вернет новый URL-адрес, и вам потребуется обновить свое приложение с помощью нового URL-адреса.

## <a name="upload-your-tab-to-teams-with-app-studio"></a>Отправка вкладки в Teams с помощью App Studio

>[!Note]
> Мы используем приложение App Studio, чтобы изменить файл **manifest. JSON** и отправить завершенный пакет в Teams. Вы также можете вручную изменить файл **manifest. JSON** , если вы предпочитаете. Если вы сделаете это, не забудьте создать решение еще раз, чтобы создать ZIP-файл **Tab** для отправки.

- Откройте клиент Microsoft Teams. Если вы используете [версию на основе веб-сайта](https://teams.microsoft.com) , вы можете проверить интерфейсный код с помощью [средств разработчика](~/tabs/how-to/developer-tools.md)в браузере.

- Откройте приложение App Studio и выберите вкладку **редактор манифестов** .

- В редакторе манифеста выберите **импортировать существующую** плитку приложения, чтобы начать обновление пакета приложения для вкладки. Исходный код сопровождается собственным частично завершенным манифестом. Имя пакета приложения — **TAB. zip**. Его можно найти здесь:

```bash
/bin/Debug/netcoreapp2.2/tab.zip
```

- Отправка **вкладки** в App Studio. zip.

### <a name="update-your-app-package-with-manifest-editor"></a>Обновление пакета приложения с помощью редактора манифеста

После того как вы отправили пакет приложений в приложение App Studio, вам потребуется завершить его настройку.

- На правой панели страницы приветствия редактора манифеста выберите плитку для вновь импортированной вкладки.

В левой части редактора манифеста есть список действий, а справа — список свойств, значения которых должны быть заданы для каждого из этих шагов. Многие из этих сведений предоставлены в файле *manifest. JSON* , но существует несколько полей, которые необходимо обновить:

#### <a name="details-app-details"></a>Сведения: сведения о приложении

- В разделе *Идентификация* выберите ***создать*** , чтобы заменить замещающий идентификатор на требуемый идентификатор GUID для вкладки.

- В разделе *сведения для разработчиков* обновите поле URL- **адрес веб-сайта** с помощью URL-адреса *ngrok* HTTPS.

- В разделе *URL-адреса приложений* обновите заявление **о конфиденциальности** и **условия использования** URL-адресов с помощью URL-адреса *ngrok* HTTPS. Не забудьте включить пути */приваци* и */Тау* в конце URL-адресов.

#### <a name="capabilities-tabs"></a>Возможности: вкладки

В разделе *вкладки* :

- На *вкладке Группа* нажмите кнопку **Добавить**.

- Во всплывающем окне вкладки команды обновите *URL-адрес конфигурации* до `https://<yourngrokurl>/tab`.

- И, наконец, убедитесь, что вы *можете обновить конфигурацию? Флажки группа и* *Групповая беседа* отмечены и нажмите кнопку **сохранить**.

#### <a name="finish-domains-and-permissions"></a>Готово: домены и разрешения

В разделе *домены и разрешения* *домены из поля вкладки* должны содержать URL-адрес NGROK без префикса HTTPS `<yourngrokurl>.ngrok.io/`.

#### <a name="test-and-distribute-test-and-distribute"></a>Тестирование и распределение: тестирование и распределение

>[!IMPORTANT]
>В поле **Описание** справа появится следующее предупреждение:
>
>&#9888; "**массив" валиддомаинс "не может содержать туннельный сайт...**"
>
>Это предупреждение можно игнорировать при тестировании вкладки.

В разделе " *тестирование и распространение* ":

- Нажать кнопку **Установить**.

- Во всплывающем окне *Добавление в группу или в* поле "разговор" введите команду и нажмите кнопку **установить**.

- В следующем всплывающем окне выберите канал команды, в котором будет отображаться вкладка, и нажмите кнопку **настроить**.

- В последнем всплывающем окне выберите значение для вкладки (красный или серый значок) и нажмите кнопку **сохранить**.

Чтобы просмотреть вкладку, перейдите к группе, в которой она была установлена, и выберите ее в панели вкладок. Должна отобразиться страница, выбранная во время настройки.
