## Обмен данными с интернет магазином общие правила
Для организации обмена между "1С: Предприятие" и интернет-магазином разработан и опубликован протокол, в котором используется стандарт обмена коммерческой информацией в формате XML - CommerceML2

### Штатная процедура обмена коммерческими данными функционально делится на 2 блока:

* выгрузка на сайт каталога продукции, торговых предложение, данных об остатках, данных о ценах
* обмен информацией о заказах

Инициатором обмена в обоих случаях выступает система "1С: Предприятие". При инициализации взаимодействия устанавливается HTTP соединение. Система "1С:Предприятие" запрашивает у сайта необходимые параметры, такие, как максимальный объем пакета, поддержка сжатия и др.. На основании этих данных система "1С:Предприятие" формирует XML сообщения и передает их на сайт.

### Алгоритм выгрузки данных на сайт
В процессе выгрузки данных сайт возвращает ответы:

* При выгрузке файлов на сайт:

  * success - файл доставлен

  * failure, или отсутствие ответа - файл не доставлен

* Ожидание окончания обработки данных

  * progress - файл обрабатывается (на следующей строке ответа указано на каком этапе)

  * success - файл успешно обработан

  * failure, или отсутствие ответа - файл не обработан.
  
 ### Порядок импорта файлов:
 * в одном запросе оба файла: import.xml, offers.xml
 * либо 2 запроса и порядок выгрузки: offers.xml затем import.xml

### Правила автоматической загрузки данных на сайт
* Автоматический режим "выгружать изменения".
Полезен для быстрой актуализации
  * рекомендуем делать раз в 30 минут.
  * минимум 15 минут, максимум 1 день.
* Автоматический режимвыгружать "все данные"
ОБЯЗАТЕЛЕН ДЛЯ КОНСИСТЕНТНОСТИ ДАННЫХ
  * рекомендуем делать раз в неделю
  * минимум 1 раз в день ночью, максимум 1 раз в 2 недели.

