_v.1.2_
Следующая инструкция показывает как можно настроить работу в [[1С|конфигураторе 1С]] с [[GitHub]].
# Что такое GitHub

[GitHub](https://github.com) - облачная платформа для хостинга IT-проектов и совместной работы над кодом, основанная на системе контроля версий Git.
Платформа предоставляет разработчикам инструменты для хранения, управления и отслеживания изменений в коде, а также позволяет нескольким разработчикам совместно работать над проектами.

Работая со стандартным функционалом 1С, ближайший аналог является "Хранилище" - функционал, который также позволяет вести и отслеживать групповую разработку непосредственно в конфигураторе. При сравнении этих двух вариантов, можно выделить следующие особенности каждого:
- Хранилище:
	- Не требует дополнительных утилит для работы, т.е. можно обойтись только стандартной 1С платформой;
	- Отсутствие конфликтов изменений при совместной работе;
- Git:
	- Точечное отслеживание изменений в коде и метаданных;
	- Распределенная работа;
	- Одновременная работа над одними объектами;
	- Ревью кода перед окончательным внесением.

Если с хранилищем уже всё понятно и мы знаем что от него ожидать, то с Git для неподготовленного пользователя будет сложнее. Поэтому дальше описано как начать вести работу с 1С-Git, а именно используя сервис GitHub.

# Подготовка пространства
## Git
### Где скачать
В первую очередь нам требуется установить на компьютер сам [Git](https://git-scm.com). Скачать его можно бесплатно на [официальном сайте](https://git-scm.com/downloads/win):<img width="973" height="583" alt="Pasted image 20250924155254" src="https://github.com/user-attachments/assets/2168ee9a-3371-4a44-8730-38f2607525f4" />
### Как установить
После скачивания запускаем файл-установщик.
Соглашаемся с лицензионным соглашением: <img width="500" height="393" alt="Pasted image 20250924161624" src="https://github.com/user-attachments/assets/02bb8318-7ce7-4195-83d3-9ce9e7709dce" />
Выбираем директорию установки:<img width="499" height="393" alt="Pasted image 20250924161657" src="https://github.com/user-attachments/assets/988e0142-af1b-4e50-a484-8d0fc4d07558" />
На текущей и последующих страницах можно ничего не изменять: <img width="499" height="392" alt="Pasted image 20250924161748" src="https://github.com/user-attachments/assets/0462f75c-f189-416b-9513-42d6ef50f94c" />
Доходим до финальной страницы, где нажимаем "Install".
После окончания, подтверждаем установку нажимая "Finish" (также снимаем галочки с полей "Launch Git Bash" и "View Release Notes"):<img width="500" height="392" alt="Pasted image 20250924161950" src="https://github.com/user-attachments/assets/afaac59f-13d5-4a0d-8d72-17d6432b5616" />
На это установка Git завершена.
### Начальные настройки
Для начала работы требуется установить в системе настройки по работе с Git. Для этого открываем командную строку от имени администратора и прописываем следующие команды:
- `git config --global user.name <Имя пользователя>`
- `git config --global user.email <Эл. почта пользователя>`
где, `<Имя пользователя>` это имя от которого будут отправляться запросы в Git, `<Эл. почта пользователя>` это электронная почта от которой будут отправляться запросы в Git.
## VS Code
[Visual Studio Code (VS Code)](https://code.visualstudio.com) - бесплатный кастомизируемый редактор кода, разработанный Microsoft. Благодаря расширениям может быть настроен под работу в любой сфере разработки.
Далее рассмотрим как настроить VSC под работу с 1С и GitHub.
### Где скачать
Скачать его можно бесплатно на [официальном сайте](https://code.visualstudio.com): <img width="1355" height="659" alt="Pasted image 20250924163156" src="https://github.com/user-attachments/assets/f7812cfe-4d1b-4e25-8b5f-9ac5112ce682" />
### Как установить
После скачивания запускаем файл-установщик.
Соглашаемся с лицензионным соглашением: <img width="542" height="421" alt="Pasted image 20250924163340" src="https://github.com/user-attachments/assets/c0772ddd-77c3-4348-8874-9d2c6dde5b6c" />
Выбираем директорию установки: <img width="542" height="419" alt="Pasted image 20250924163446" src="https://github.com/user-attachments/assets/44f8f0ae-51c2-450f-93b9-73eca64114f1" />
На текущей и последующих страницах можно ничего не изменять: <img width="542" height="420" alt="Pasted image 20250924163529" src="https://github.com/user-attachments/assets/54409651-4f75-4433-a325-581eb10b8ea6" />
Доходим до финальной страницы, где нажимаем "Установить".
После окончания, подтверждаем установку нажимая "Завершить": <img width="541" height="419" alt="Pasted image 20250924163639" src="https://github.com/user-attachments/assets/648522f0-271c-4273-bec7-4efdf50c9731" />
### Первый запуск
При первом запуске VSC для полноценного начала работы нам требуется установить следующие расширения:
- Для удобной работы с 1С:
	- Language 1C (BSL);
	- 1C (BSL) Extension Pack;
	- 1C Metadata Viewer;
- Для работы с GitHub:
	- GitHub Pull Requests;
	- GitLens - Git supercharged;
#### Как установить расширения
В левой панели инструментов открываем вкладку "Extensions" (Расширения) и переходим к полю поиска: <img width="887" height="536" alt="Pasted image 20250924194252" src="https://github.com/user-attachments/assets/19b7fa16-14da-4e7c-8d10-0f6b0eb3d902" />
Вбиваем в поле поиска требуемое нам расширение, находим его в списке и нажимаем "Install" (Установить): <img width="873" height="266" alt="Pasted image 20250924194603" src="https://github.com/user-attachments/assets/4910aa98-65ad-4ee4-8104-322559b0a2d3" />

#### 1C
##### Language 1C (BSL)
<img width="1231" height="600" alt="Pasted image 20250924194812" src="https://github.com/user-attachments/assets/38b775fe-3357-46bc-b573-057a1f66e777" />
Требуется для подсветки синтаксиса 1С в файлах .bsl и .os, добавляет контекстную подсказку и также имеет функции по проверке кода:
- `1C (BSL)` - встроенный языкы 1С:Предприятие 8 и [OneScript](http://oscript.io/ "http://oscript.io/");
- `1C (Query)` - языка запросов 1С:Предприятие 8.
##### 1C (BSL) Extension Pack
<img width="1232" height="578" alt="Pasted image 20250924195106" src="https://github.com/user-attachments/assets/2904d8c2-f293-4343-9d50-4e3888e7af04" />
Дополнение к предыдущему расширению.
##### 1C Metadata Viewer
<img width="1232" height="578" alt="Pasted image 20250924195202" src="https://github.com/user-attachments/assets/e19c7130-b7e9-4835-b1b0-20fd614ed2cc" />
Требуется для просмотра дерева метаданных 1С в привычном формате.
#### GitHub
##### GitHub Pull Requests
<img width="1232" height="600" alt="Pasted image 20250925093322" src="https://github.com/user-attachments/assets/5f0da78e-ba23-46da-9cff-d2642b5a8d38" />
Требуется для интеграции с GitHub.
##### GitLens - Git supercharged
<img width="1231" height="581" alt="Pasted image 20250925093450" src="https://github.com/user-attachments/assets/01070531-cfa4-4dba-a073-3b744c9d0ef5" />
Дополнение для упрощенным взаимодействием с Git в VSC.
# Начало работы
## GitHub
Чтобы приступить к работе требуется подключиться уже к существующему репозиторию или создать новый. Рассмотрим первый вариант:
### Как подключиться к существующему
Если репозиторий помечен как "Private" (Закрытый), то администратор репозитория должен отправить приглашение для Вашего пользователя. Новые приглашения можно найти на странице уведомлений ("Notifications"): <img width="474" height="301" alt="Pasted image 20250925113754" src="https://github.com/user-attachments/assets/db44475a-b82f-4518-979a-3a10ee26141d" />
При наличии нового приглашения, открываем его и принимаем (кнопка "Accept invitation"): <img width="1260" height="578" alt="Pasted image 20250925125959" src="https://github.com/user-attachments/assets/3c9777cd-1a87-4c35-9a5b-b689e546826a" />
Далее откроется окно с репозиторием, где можно скопировать ссылку для дальнейшего использования: <img width="1584" height="729" alt="Pasted image 20250925144945" src="https://github.com/user-attachments/assets/f968456b-1d51-49fe-aee4-639e7554478c" />
## VS Code
Переходим в VS Code и на вступительной странице нажимаем "Clone Git Repository...": <img width="1919" height="1079" alt="Pasted image 20250925145146" src="https://github.com/user-attachments/assets/4fb0ec18-2014-4fbf-83df-d09d463172bf" />
Вставляем скопированную ранее ссылку на репозиторий и нажимаем Enter: <img width="1919" height="1079" alt="Pasted image 20250925145236" src="https://github.com/user-attachments/assets/39e45f29-9280-4fea-ba80-2526451357b9" />
В открывшимся окне выбираем директорию для хранения файлов (сохраняем путь, так как он понадобится нам в дальнейшем): <img width="948" height="534" alt="Pasted image 20250925145419" src="https://github.com/user-attachments/assets/6ed7c823-b908-479b-9572-b618b8231318" />
Далее нажимаем "Open" (Открыть): <img width="510" height="125" alt="Pasted image 20250925145653" src="https://github.com/user-attachments/assets/768acb07-5483-4d5b-9f55-311614907a14" />
На этом мы подключили VS Code к выбранному репозиторию и готовы начать работу с файлами.
# 1С - GitHub
После всех проведенных настроек мы готовы начать работу в 1С.
## Работа с основной веткой "Main"
### Конфигуратор
#### Описание конфигурации
Для примера возьмем небольшую конфигурацию содержащую следующие объекты:
- Справочник;
- Общий модуль;
<img width="575" height="808" alt="Pasted image 20250925150702" src="https://github.com/user-attachments/assets/560330ef-308f-44f3-8972-2180e94f0901" />
#### Как выгрузить конфигурацию
Чтобы выгрузить конфигурацию в GitHub не подойдет использование стандартного файла .cf, поэтому проделываем следующие действия:
Открываем панель "Конфигурация" и нажимаем на "Выгрузить конфигурацию в файлы...": <img width="705" height="664" alt="Pasted image 20250925151326" src="https://github.com/user-attachments/assets/3933f8bc-5c2c-4491-9eee-6ff60db3c75e" />
В открывшимся окне выбираем "XML-файлы", прописываем ранее выбранную директорию хранения репозитория и нажимаем "Выгрузить": <img width="363" height="259" alt="Pasted image 20250925151508" src="https://github.com/user-attachments/assets/6684296f-bc11-46e0-8949-2e58d4ce39bb" />
### VS Code
Возвращаемся в VS Code и во вкладке "Source Control" мы можем увидеть наши изменения: <img width="1206" height="809" alt="Pasted image 20250925151747" src="https://github.com/user-attachments/assets/65f56459-b0c9-4659-8821-f39439d5d278" />
Чтобы зафиксировать, какие изменения мы хотим подтвердить для отправки, нажимаем на команду "Stage All Changes" (Знак +): <img width="417" height="292" alt="Pasted image 20250925151933" src="https://github.com/user-attachments/assets/aae1705d-2cef-4d26-b080-981a763484e4" />
Мы можем увидеть что все выбранные изменения перешли во вкладу "Changes". Заполняем комментарий и нажимаем на "Commit": <img width="396" height="318" alt="Pasted image 20250925152253" src="https://github.com/user-attachments/assets/4a1db41e-2eba-444b-886d-d0eab334f613" />
Теперь мы можем увидеть состояние нашего коммита - сейчас коммит "Выгрузка всей конфигурации" находится в локальном репозитории: <img width="988" height="849" alt="Pasted image 20250925152501" src="https://github.com/user-attachments/assets/c2d4860c-b1d2-4de8-aa92-1c029ba519a9" />
Нажимаем "Sync Changes" и отправляем изменения в основную ветку "Main" в GitHub. Теперь мы можем увидеть нашу конфигурацию в GitHub: <img width="1878" height="1004" alt="Pasted image 20250925152748" src="https://github.com/user-attachments/assets/c032b1f2-5032-4465-8ad1-f4273449b053" />
## Дополнительные ветки
При совместной работе нескольких разработчиков во избежание конфликтов и минимальных рисках повреждения данных основной ветки нам потребуется функции по работе с дополнительными ветками.
### Как создать дополнительную ветку
Чтобы создать дополнительную ветку наводимся на требуемый коммит во вкладке "Graph" и в контекстном меню выбираем "Create Branch...": <img width="997" height="1079" alt="Pasted image 20250925154317" src="https://github.com/user-attachments/assets/cd783d1b-ccef-45b2-ba3f-6e1e2ed45b44" />
Вводим название новой ветки - название должно состоять из латиницы и не содержать пробелов: <img width="1346" height="1079" alt="Pasted image 20250925154438" src="https://github.com/user-attachments/assets/97901d64-e9a9-4f9a-b64d-9720b6e0878a" />
Теперь мы находимся в дополнительной ветке (в примере "test_branch"). Это можно проверить нижней панели: <img width="774" height="1079" alt="Pasted image 20250925154957" src="https://github.com/user-attachments/assets/b3e8e131-95e8-49e7-87f9-ba2982795d53" />
### Работа в дополнительных ветках
Для примера добавим в общий модуль следующий код: <img width="815" height="296" alt="Pasted image 20250925160106" src="https://github.com/user-attachments/assets/b102d54b-af75-4b7a-b501-d1007081d3bd" />
После сохранения конфигурации проводим операции указанные [[Что требуется чтобы начать работать с Git#Как выгрузить конфигурацию|ранее]] для выгрузки конфигурации в директорию репозитория.
Возвращаемся в VSC и видим новые изменения: <img width="1919" height="1079" alt="Pasted image 20250925160401" src="https://github.com/user-attachments/assets/5b6547a5-102a-4bb4-a2b9-fc70e8ca58bd" />
Также как и ранее, вводим комментарий к коммиту; далее для скорости работы нажимаем "Commit & Push": <img width="548" height="342" alt="Pasted image 20250925160653" src="https://github.com/user-attachments/assets/b67446e8-463e-4ef1-9e45-30cb5bf49227" />
VSC предупреждает нас об отсутствии нашей ветки в Git и предлагает нам опубликовать новую. Может нажать на "OK, Don't Ask Again": <img width="537" height="128" alt="Pasted image 20250925160840" src="https://github.com/user-attachments/assets/d0bfeed6-2752-4fe6-9252-7ea17b48852e" />
После выполненных действий, мы внесли изменения в нашей ветке и опубликовали их в GitHub.
### Слияние веток
Теперь, когда мы хотим внести наши изменения в основную ветку, мы должны выполнить "Pull Request". Переходим в левой панели инструментов во вкладку "GitHub" где нажимаем на команду "Create Pull Request": <img width="394" height="328" alt="Pasted image 20250925161751" src="https://github.com/user-attachments/assets/78ab3fed-82db-45d5-97f0-b874b8e1e728" />
Заполняем название и описание новой заявки, устанавливаем ответственное лицо командой "Add Assignees", и нажимаем "Create": <img width="393" height="471" alt="Pasted image 20250925162632" src="https://github.com/user-attachments/assets/fb1368df-9bd5-4bba-9739-f4b91e666c47" />

В результате всех действий была создана заявка, которая отправляется на проверку ответственному лицу. Мы можем отслеживать состояние заявки на вкладке "GitHub": <img width="1626" height="793" alt="Pasted image 20250925162908" src="https://github.com/user-attachments/assets/a9a3a5a5-0809-4907-b36b-e749d3944df3" />

