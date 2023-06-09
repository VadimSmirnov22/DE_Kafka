### Задача

Агрегатор для доставки еды набирает популярность и вводит новую опцию — подписку. Она открывает для пользователей ряд возможностей, одна из них которых — добавлять рестораны в избранное. Только тогда пользователю будут поступать уведомления о специальных акциях с ограниченным сроком действия. Систему, которая поможет реализовать это обновление, вам и нужно будет создать.
Благодаря обновлению рестораны смогут привлечь новую аудиторию, получить фидбэк на новые блюда и акции, продать профицит товара и увеличить продажи в непиковые часы. Акции длятся недолго, всего несколько часов, и часто бывают ситуативными, а значит, важно быстро доставить их кругу пользователей, у которых ресторан добавлен в избранное.  

Система работает так:
1. Ресторан отправляет через мобильное приложение акцию с ограниченным предложением. Например, такое: «Вот и новое блюдо — его нет в обычном меню. Дарим на него скидку 70% до 14:00! Нам важен каждый комментарий о новинке».
2. Сервис проверяет, у кого из пользователей ресторан находится в избранном списке.
3. Сервис формирует заготовки для push-уведомлений этим пользователям о временных акциях. Уведомления будут отправляться только пока действует акция.

#### План выполнения

1. Проверить работу потока.
2. Прочитать данные об акциях из Kafka.
3. Прочитать данные о подписчиках из Postgres.
4. Преобразование JSON в датафейм. 
5. Провести JOIN потоковых и статичных данных.
6. Отправить результаты JOIN в Postgres для аналитики фидбэка.
7. Отправить данные, сериализованные в формат JSON, в Kafka для push-уведомлений.
8. Персистентность датафрейма.

### Использованные инструменты
Python, Kafka, PySpark, json