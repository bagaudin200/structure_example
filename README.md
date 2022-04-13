<h1 align="center">Telegram-bot Hotel finder

[![Telegram URL](https://www.dampftbeidir.de/mediafiles/tpl/icon-telegram.png)](https://t.me/YourPersonallyHelperBot) 
</h1>

***

## Краткое описание

[Телеграмм бот](@the_best_hotelss_bot) позволяет найти выгодное предложение на платформе [Hotels.com](https://hotels.com/).
<br> Пользователь с помощью специальных команд бота может выполнить следующие действия (получить следующую информацию): <br/>
- Узнать топ самых дешёвых отелей в городе (**команда /lowprice**). 
- Узнать топ самых дорогих отелей в городе (**команда /highprice**). 
- Узнать топ отелей, наиболее подходящих по цене и расположению от центра (самые дешёвые и находятся ближе всего к центру) (**команда /bestdeal**). 
- Узнать историю поиска отелей (**команда /history**)


**Для разработки и функционирования проекта используется открытый API Hotels, который расположен на сайте [rapidapi.com](https://rapidapi.com/apidojo/api/hotels4/).**

***


## Интересные реализации
<ul>
	<li>Все данные пользователя хранятся в персональной БД (файлы формата .json), что позволяет в случае непредвиденного завершения работы скрипта сохранить все введенные ранее данные.
	<li>Работа телеграмм бота реализована на двух языках:
 		<ul>
			<li>Русский (ru_RU)</li>
			<li>Английский (en_US)</li>
		</ul>
	<li>Реализована генерация следующих URL-ссылок
		<ul>
			<li>на персональную страницу запроса (в соответствии с введенными пользователем параметрами поиска)</li>
			<li>на страницу объекта размещения (отеля)</li>
			<li>на страницу Google Maps с точкой на объект размещения в соответствии с его координатами на Hotels Api</li>
		</ul>
	</li>
</ul>

***

## Локальная установка
Эти инструкции помогут вам развернуть проект на локальном компьютере для разработки и тестирования

**Перед тем, как начать:**
- Если вы не пользуетесь `Python 3`, вам нужно установить инструмент `virtualenv` при помощи `pip install virtualenv`. 
Если вы используете `Python 3`, у вас уже установлен модуль [venv](https://docs.python.org/3/library/venv.html) в стандартной библиотеке.


### Запуск проекта (на примере Windows)

- Создайте на своем компютере папку проекта
- Склонируйте этот репозиторий в папку проекта `git clone https://github.com/...`
- Создайте файл `.env` и добавьте в него переменные окружения:
- Активируйте виртуальное окружение `pipenv shell`
- Установите все зависимости `pipenv install --ignore-Pipfile`
```
TOKEN=*YourBotToken*
RAPIDHOST=hotels4.p.rapidapi.com
RAPIDAPIKEY=*YourRapidKey*
```
- Запустите бота командой `pipenv run main.py` из Терминала из папки с проектом 

***

## Описание работы команд

### Команда /start 

После ввода команды у пользователя запрашивается: 
1. Город, где будет проводиться поиск
2. Количество отелей, которые необходимо вывести в результате (не больше заранее определённого максимума)
3. Необходимость загрузки и вывода фотографий для каждого отеля (“Да/Нет”). При положительном ответе пользователь также вводит количество необходимых фотографий (не больше заранее определённого максимума)

### Команда /lowprice 

После ввода команды у пользователя запрашивается: 
1. Город, где будет проводиться поиск 
2. Количество отелей, которые необходимо вывести в результате (не больше заранее определённого максимума)
3. Необходимость загрузки и вывода фотографий для каждого отеля (“Да/Нет”). При положительном ответе пользователь также вводит количество необходимых фотографий (не больше заранее определённого максимума)

### Команда /highprice

После ввода команды у пользователя запрашивается: 
1. Город, где будет проводиться поиск
2. Количество отелей, которые необходимо вывести в результате (не больше заранее определённого максимума)
3. Необходимость загрузки и вывода фотографий для каждого отеля (“Да/Нет”). При положительном ответе пользователь также вводит количество необходимых фотографий (не больше заранее определённого максимума

### Команда /bestdeal

После ввода команды у пользователя запрашивается: 
1. Город, где будет проводиться поиск
2. Диапазон цен
3. Диапазон расстояния, на котором находится отель от центра
4. Количество отелей, которые необходимо вывести в результате (не больше заранее определённого максимума)
5. Необходимость загрузки и вывода фотографий для каждого отеля (“Да/Нет”). При положительном ответе пользователь также вводит количество необходимых фотографий (не больше заранее определённого максимума)

### Команда /history

После ввода команды пользователю выводится история поиска отелей. Сама история содержит: 
1. Команду, которую вводил пользователь (с гиперссылкой на страницу запроса)
2. Город, где проводился поиск
3. Дату и время ввода команды
4. Отели, которые были найдены (с гиперссылкой на страницу отеля)

Дополнительно доступны две кнопки для работы с историей поиска:
1. Очистить (очищает историю поиска и скрывает сообщения, содержащие историю поиска)
2. Скрыть (скрывает сообщения, содержащие историю поиска)

### Команда /settings

После ввода команды пользователю предлагается установить следующие параметры: 
 - Язык (русский, английский)
 - Валюта (рубли, доллары, евро)

***

## Описание внешнего вида и UI
Окно Telegram-бота при запущенном Python-скрипте воспринимает следующие команды: 
- /help — помощь по командам бота 
- /lowprice — вывод самых дешёвых отелей в городе
- /highprice — вывод самых дорогих отелей в городе 
- /bestdeal — вывод отелей, наиболее подходящих по цене и расположению от центра
- /history — вывод истории поиска отелей
- /settings — установка параметров

Для команд lowprice, highprice и bestdeal сообщение с результатом содержит краткую информацию по каждому отелю. 
В эту информацию входит: 
- Название отеля
- Адрес (с гиперссылкой на Google Maps) 
- Ближайшие ориентиры (в т.ч. как далеко расположен от центра)
- Цена за ночь (в валюте, заданной пользователем или определенной автоматически)
- N фотографий отеля (если пользователь счёл необходимым их вывод)
- Гиперссылка на страницу отеля на Hotels.com
- Гиперссылка на страницу Hotels.com с персональным запросом пользователя

***
## Примеры использования

Реализация команд `/settings`, `/history`

<p>

<img src="https://i.imgur.com/Sfun6Ad.gif" width="30%"> <img src="https://i.imgur.com/HYZ2Wke.gif" width="30%">
</p>

***

## В разработке использованы

- [Python 3.9](https://www.python.org/)
- [pyTelegramBotAPI](https://pypi.org/project/pyTelegramBotAPI/)
- [requests](https://pypi.org/project/requests/)
- [python-decouple](https://pypi.org/project/python-decouple/)
- [arrow](https://pypi.org/project/arrow/)
- [HotelsApi](https://rapidapi.com/apidojo/api/hotels4/)
