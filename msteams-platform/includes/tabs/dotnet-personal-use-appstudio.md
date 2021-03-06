## <a name="upload-your-tab-to-teams-with-app-studio"></a>Отправка вкладки в Teams с помощью App Studio

>[!NOTE]
> Мы используем приложение App Studio, чтобы изменить файл **manifest. JSON** и отправить завершенный пакет в Teams. Вы также можете вручную изменить **манифест. JSON** , если хотите. Если вы сделаете это, не забудьте создать решение еще раз, чтобы создать ZIP-файл **Tab** для отправки.

- Откройте клиент Microsoft Teams. Если вы используете [версию на основе веб-сайта](https://teams.microsoft.com) , вы можете проверить интерфейсный код с помощью [средств разработчика](~/tabs/how-to/developer-tools.md)в браузере.

- Откройте приложение App Studio и выберите вкладку **редактор манифестов** .

- В редакторе манифеста выберите **импортировать существующую** плитку приложения, чтобы начать обновление пакета приложения для вкладки. Исходный код сопровождается собственным частично завершенным манифестом. Имя пакета приложения — **TAB. zip**. Его можно найти здесь:

```bash
/bin/Debug/netcoreapp2.2/Tab.zip
```

- Отправка **вкладки** в App Studio. zip.

### <a name="update-your-app-package-with-manifest-editor"></a>Обновление пакета приложения с помощью редактора манифеста

После того как вы отправили пакет приложений в приложение App Studio, вам потребуется завершить его настройку.

- На правой панели страницы приветствия редактора манифеста выберите плитку для вновь импортированной вкладки.

В левой части редактора манифеста есть список действий, а справа — список свойств, значения которых должны быть заданы для каждого из этих шагов. Многие из этих сведений предоставлены в файле *manifest. JSON* , но существует несколько полей, которые необходимо обновить:

#### <a name="details-app-details"></a>Сведения: сведения о приложении

В разделе *сведения о приложении* :

- В разделе *Идентификация* нажмите **создать** , чтобы создать новый идентификатор приложения.

- В разделе *сведения для разработчиков* обновите URL- **адрес веб-сайта** с помощью URL-адреса *ngrok* HTTPS.

- В *разделе URL-адреса приложений* обновите `https://<yourngrokurl>/privacy` заявление **о конфиденциальности** и условия `https://<yourngrokurl>/tou` его **использования** для>.

#### <a name="capabilities-tabs"></a>Возможности: вкладки

В разделе *вкладки* :

- В разделе *Добавление личной вкладки* нажмите кнопку ***Добавить***. Откроется всплывающее диалоговое окно.

- Заполните поле *имя* .

- Заполните поле " *идентификатор сущности* ".

- Обновите поле *URL-адрес содержимого* с помощью `https://<yourngrokurl>/personalTab`.

- Оставьте поле *URL-адрес веб-сайта* пустым.

- Нажмите кнопку ***Сохранить***.

#### <a name="finish-domains-and-permissions"></a>Готово: домены и разрешения

В разделе *домены и разрешения* *домены из поля вкладки* должны содержать URL-адрес NGROK без префикса HTTPS `<yourngrokurl>.ngrok.io/`.

##### <a name="finish-test-and-distribute"></a>Готово: тестирование и распределение

>[!IMPORTANT]
>В поле **Описание** справа появится следующее предупреждение:
>
>&#9888; "**массив" валиддомаинс "не может содержать туннельный сайт...**"
>
>Это предупреждение можно игнорировать при тестировании вкладки.

В разделе " *тестирование и распространение* ":

- Нажать кнопку **Установить**.

- Во всплывающем окне убедитесь, что *для параметра Добавить для вас* задано значение *Да* , а для *команды Добавить в группу или чат* задано значение *нет*.

- Нажать кнопку **Установить**.

- В следующем всплывающем окне выберите **Открыть** , и вкладка отобразится.

## <a name="view-your-personal-tab"></a>Просмотр личной вкладки

- В области навигации, расположенной в левом углу приложения Teams, выберите `...` меню. Вы увидите список личных приложений.

- Выберите вкладку в списке, чтобы просмотреть его.
