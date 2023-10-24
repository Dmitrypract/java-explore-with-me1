Explore With Me
Стек: Java 11, Spring Boot, Spring Data JPA, PostgreSQL, Docker, Maven
Свободное время — ценный ресурс. Ежедневно мы планируем, как его потратить — куда и с кем сходить. Сложнее всего в таком планировании поиск информации и переговоры. Нужно учесть много деталей: какие намечаются мероприятия, свободны ли в этот момент друзья, как всех пригласить и где собраться. Explore With Me — афиша. В этой афише можно предложить какое-либо событие от выставки до похода в кино и собрать компанию для участия в нём.

Микросервисная архитектура
Приложение состоит из 2 сервисов:

stats-service - часть приложения, которая собирает, хранит и отдает по запросу статистику по просмотрам.
main-service - основная часть приложения, в которой происходит вся логика приложения.
Жизненный цикл события включает в себя несколько этапов:

Создание
Ожидание публикации. Событие переходит в состояние ожидания публикации сразу после его создания
Публикация. Администратор переводит событие в это состояние
Отмена публикации. Событие переходит в это состояние в двух случаях. Первый - если администратор решил, что оно не должно быть опубликовано. Второй - если инициатор события решил отменить его на стадии ожидания публикации
Основной сервис и сервис статистики сохраняют и загружают данные из разных баз данных. Взаимодействие сервисов в момент сохранения информации о запросе к API осуществляется с помощью клиента сервиса статистики

Схема БД main-service: 

![image](https://github.com/Dmitrypract/java-explore-with-me/assets/118967478/8c410760-6989-4541-b575-0772124648b5)


Схема БД stats-service:

![image](https://github.com/Dmitrypract/java-explore-with-me/assets/118967478/97592bc9-bda8-49c0-9eb5-396353c5cdff)


Установка и запуск проекта

1 вариант:
Необходимо настроенная система виртуализации, установленный Docker Desktop(скачать и установить можно с официального сайта https://www.docker.com/products/docker-desktop/)

Клонируйте репозиторий проекта на свою локальную машину:
git clone git@github.com:Dmitrypract/java-explore-with-me.git
Запустите командную строку и перейдите в корень директории с проектом.
Соберите проект
mvn clean package
Введите следующую команду, которая подготовит и запустит приложение на вашей локальной машине
$  docker-compose up
Приложение будет запущено на порту 8080. Вы можете открыть свой веб-браузер и перейти по адресу http://localhost:8080, чтобы получить доступ к приложению ExploreWithMe.

2 вариант:

Установите Java Development Kit (JDK) версии 11 или выше, если у вас его еще нет.

Установите PostgreSQL и создайте базу данных для проекта.

Клонируйте репозиторий проекта на свою локальную машину:

git clone git@github.com:Dmitrypract/java-explore-with-me.git
Откройте проект в вашей IDE.

Настройте файл application.properties, расположенный в директории src/main/resources, чтобы указать данные для подключения к вашей базе данных PostgreSQL.

Запустите приложение, выполнив следующую команду в корневой директории проекта:

mvn spring-boot:run
Приложение будет запущено на порту 8080. Вы можете открыть свой веб-браузер и перейти по адресу http://localhost:8080, чтобы получить доступ к приложению Explore With Me.
