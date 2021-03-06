## <a name="upload-your-tab-to-teams-with-app-studio"></a>Отправка вкладки в Teams с помощью App Studio

>[!NOTE]
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

- В разделе *Идентификация* нажмите **создать** , чтобы создать новый идентификатор приложения.

- В разделе *сведения для разработчиков* обновите поле URL- **адрес веб-сайта** с помощью URL-адреса *ngrok* HTTPS.

- В *разделе URL-адреса приложений* обновите `https://<yourngrokurl>/privacy` заявление **о конфиденциальности** и условия `https://<yourngrokurl>/tou` его **использования** для>.

#### <a name="capabilities-tabs"></a>Возможности: вкладки

В разделе *вкладки* :

- На *вкладке Группа* нажмите кнопку **Добавить**.

- Во всплывающем окне вкладки команды обновите *URL-адрес конфигурации* до `https://<yourngrokurl>/tab`.

- И, наконец, убедитесь, что вы *можете обновить конфигурацию? Флажки группа и* *Групповая беседа* отмечены и нажмите кнопку **сохранить**.

#### <a name="finish-domains-and-permissions"></a>Готово: домены и разрешения

В разделе *домены и разрешения* *домены из поля вкладки* должны содержать URL-адрес NGROK без префикса HTTPS `<yourngrokurl>.ngrok.io/`.

#### <a name="finish-test-and-distribute"></a>Готово: тестирование и распределение

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
