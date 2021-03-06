### <a name="use-app-studio-to-update-the-app-package"></a>Обновление пакета приложения с помощью App Studio

App Studio — это приложение Teams, которое можно установить из хранилища Teams. Он упрощает создание и регистрацию приложения.

Чтобы установить приложение App Studio в Teams, щелкните значок магазин приложений в нижней части левой панели и найдите приложение App Studio.

<img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

Найдя плитку для App Studio, щелкните ее и выберите пункт *установить* в появившемся диалоговом окне.

<img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

После установки App Studio щелкните вкладку редактор манифеста, чтобы приступить к созданию пакета приложения для приложения Teams.

<img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

Пример сопровождается собственным манифестом и предназначен для создания пакета приложения при построении проекта. В .NET это делается в Visual Studio, а на узле JS это делается путем ввода в `gulp` командной строке корневого каталога проекта.

```bash
$ gulp
[13:39:27] Using gulpfile ~\documents\github\msteams-samples-hello-world-nodejs\gulpfile.js
[13:39:27] Starting 'clean'...
[13:39:27] Starting 'generate-manifest'...
[13:39:27] Finished 'generate-manifest' after 11 ms
[13:39:27] Finished 'clean' after 21 ms
[13:39:27] Starting 'default'...
Build completed. Output in manifest folder
[13:39:27] Finished 'default' after 62 μs
```

Имя созданного пакета приложения — *helloworldapp.zip*. Вы можете выполнить поиск этого файла, если расположение не было ясно в используемом средстве.

В следующей части пошагового руководства вы собираетесь изменить этот пакет приложения, выбрав в редакторе манифеста *Импорт имеющейся плитки приложения* .

<img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

После импорта пакета приложений приложение Studio Studio должно выглядеть следующим образом:

<img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

Щелкните плитку для нового импортированного приложения *Hello World*.

<img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

В левой части редактора манифеста есть список шагов, а в правом списке свойств, которые необходимо заполнить для каждого из этих шагов. С момента начала работы с примером приложения многие сведения уже заполнены. Дальнейшие действия помогут изменить те части, которые все еще нуждаются в обновлении.

#### <a name="app-details"></a>Сведения о приложении

В разделе *Details*(сведения о приложении) щелкните запись *сведения о приложении* . Нажмите кнопку *создать* , чтобы создать новый идентификатор приложения.

Новый идентификатор приложения должен выглядеть примерно так: `2322041b-72bf-459d-b107-f4f335bc35bd` .

Просмотрите остальные сведения о приложении в правой области и ознакомьтесь с некоторыми из таких записей, как *сведения об авторе* и *фирменная символика*. Эти разделы важны, если вы пишете новое приложение для распространения.

#### <a name="capabilities-tabs"></a>Возможности: вкладки

Вкладки находятся среди самых простых элементов, добавляемых в приложение Teams. Пример приложения уже поддерживает несколько вкладок, и вы можете включить их следующим образом.

##### <a name="team-tab"></a>Вкладка "Группа"

Ваше приложение может иметь только одну вкладку группы.

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

В этом примере на вкладке Группа размещается страница настройки. Щелкните символ *..* . в конце записи и выберите команду *изменить* в раскрывающемся списке. Измените URL-адрес `https://yourteamsapp.ngrok.io/configure` , на который `yourteamsapp.ngrok.io` следует заменить URL-адрес, который использовался при размещении приложения.

##### <a name="personal-tabs"></a>Личные вкладки

Ваше приложение может иметь до 16 вкладок, в том числе вкладку "Группа".

Личные вкладки представлены по-разному на вкладке Группа. *Вкладка Привет* должна отображаться в списке личные вкладки. В данный момент он имеет значение заполнителя `com.contoso.helloworld.hellotab` . Щелкните символ *..* . в конце записи и выберите команду *изменить* в раскрывающемся списке. Появится следующее диалоговое окно.

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Существует два поля, которые необходимо обновить с помощью URL-адреса приложения.

- Изменить URL-адрес контента на `https://yourteamsapp.ngrok.io/hello`
- Измените URL-адрес веб-сайта на `https://yourteamsapp.ngrok.io/hello`

Где `yourteamsapp.ngrok.io` следует заменять на URL-адрес, который вы использовали при размещении приложения.

#### <a name="bots"></a>Боты

Боты — это наиболее распространенный способ добавления функциональных возможностей в приложение. В примере Hello World уже есть Bot в составе примера, но он пока не зарегистрирован в Майкрософт.

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

У ленты, импортированной из примера, нет идентификатора приложения, связанного с ним. Вам потребуется создать новый робот, чтобы приложение App Studio могло создать новый идентификатор приложения и зарегистрировать его в корпорации Майкрософт. Обратите внимание, что это идентификатор приложения для Bot, который отличается от идентификатора приложения, созданного для приложения на предыдущем шаге. Каждому интерфейсу Bot в приложении необходим свой идентификатор приложения.

Нажмите кнопку *Удалить* рядом с *импортированной* страницей ленты в списке "bot".

Теперь нет Боты, оставшихся для отображения. Нажмите кнопку *Настройка*. Отобразится диалоговое окно *Настройка ленты* .

<img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

Добавьте имя ленты `Contoso bot` , например, и выберите все три кнопки в *области область*.

Нажмите кнопку *создать Bot* , чтобы выйти из диалогового окна. Приложение Studio Studio потратит время на регистрацию ленты в Майкрософт, а затем отобразит новый элемент Bot в списке "bot". Теперь самое время открыть текстовый файл в блокноте и скопировать и вставить в него новый идентификатор Bot. Этот идентификатор потребуется позже.

Нажмите *создать новый пароль*и запишите пароль в том же текстовом файле, в котором был указан идентификатор приложения для ленты. Это единственный срок, в течение которого будет отображаться пароль, поэтому обязательно сделайте это сейчас.

Измените *адрес конечной точки ленты* `https://yourteamsapp.ngrok.io/api/messages` , `yourteamsapp.ngrok.io` указав URL-адрес, который вы использовали при размещении приложения.

Теперь рекомендуется сохранить текстовый файл, если это еще не сделано. Вы добавите эти сведения в размещенное приложение позже в этом пошаговом руководстве, которое позволит защитить связь с сервером Bot.

#### <a name="messaging-extensions"></a>расширения для обмена сообщениями;

Расширения обмена сообщениями позволяют пользователям запрашивать информацию из вашей службы и отправлять эти сведения в форме карточек прямо в беседу канала. Расширения обмена сообщениями отображаются в нижней части поля "создание".

Чтобы приступить к настройке расширения системы обмена сообщениями, щелкните ссылку *расширения системы обмена сообщениями* в разделе *возможности* в левом столбце приложения Studio.

<img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

Образец расширения обмена сообщениями отображается в области справа в разделе *расширения обмена сообщениями*. Нажмите кнопку *Удалить* еще раз, чтобы удалить эту запись, а затем нажмите кнопку *настроить* , чтобы выполнить те же действия, что и для Боты. Отобразится диалоговое окно *расширения сообщения* .

Установите флажок *использовать существующую вкладку ленты* , а затем *выберите один из существующих Боты*. В раскрывающемся меню выберите элемент Bot, созданный в предыдущем разделе. Добавьте *имя Bot* и нажмите кнопку *сохранить* , чтобы закрыть диалоговое окно.

В разделе *команда* нажмите кнопку *Добавить*. Мы добавим команду на основе поиска, поэтому выберите параметр *Разрешить пользователям запрашивать службу...* .

В диалоговом окне *Создание команды* введите указанные ниже значения.

В разделе *Новая команда*:

- *Идентификатор команды*  = жетрандомтекст
- *Title*       = получить некоторый произвольный текст для развлечений
- *Description* = получает произвольный текст и изображения

В разделе *параметр*:

- *Name*        = кардтитле
- *Title*       = название карточки
- *Description* = название карты, которое будет использоваться

После ввода данных нажмите кнопку *сохранить* , чтобы закрыть диалоговое окно.

#### <a name="register-your-app-in-teams"></a>Регистрация приложения в Teams

Теперь вы ввели сведения о вашем приложении, но не можете выполнить два действия. Сначала необходимо использовать раздел "тестирование и распределение" приложения "App Studio", чтобы установить приложение в Teams, а затем необходимо обновить размещенное приложение с помощью идентификатора приложения и пароля для ленты. Помните, что в примере предполагается использование одного и того же идентификатора и пароля приложения для почтового расширения Bot и сообщения.

Щелкните *тест и распределить* элемент под заголовком *Готово* в левом столбце App Studio.

<img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

Чтобы отправить приложение в Teams, нажмите кнопку *установить* в разделе *Проверка и распространение*.

<img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

Щелкните поле *поиска* в разделе *Добавить в группу* и выберите группу, в которую добавляется пример приложения. Обычно для тестирования потребуется настроить специальную команду.

Нажмите кнопку *Install (установить* ) в нижней части диалогового окна.

В этом пошаговом руководстве для App Studio будет завершена эта часть. Теперь вы должны увидеть ваше приложение, работающее в Teams, но не будет работать, пока вы не обновите среду размещенных приложений, чтобы узнать, какие идентификаторы и пароли приложений.

<img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>
