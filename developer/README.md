# Developer

## Описание функционала.

### CmlAPI
CmlAPI https://www.drupal.org/project/cmlapi

* Сущность "обмен" `cml`: 
  - `uuid` = `cookies` обмена для 1С
  - `state` - статус обмена  [zip|new|progress|success|busy|failure]
  - `type` - тип обмена [catalog|sale]
  - `field_file` - переданные во время обмена файлы, кроме картинок
  - `login`, `ip`, `created`,	`changed` - параметры обмена
* Работа с сущностью
  - views со списком сущностей `/admin/structure/cml`
  - просмотрщик каталога `/admin/structure/cml/ID/catalog`
  - просмотрщик товаров `/admin/structure/cml/ID/product`
  - просмотрщик вариаций `/admin/structure/cml/ID/product-variaton`
* Крон:
  - удаление пустых обменов (которые не содежрат файлы)
  - удаление старых обменов (старше чем хх)
* Сервис
* Парсер-сервис
* Реализация 

### Cml Exchange
Обмен файлами с 1С https://www.drupal.org/project/cmlexchange
* Реализация протокола обмена
*


### Cml Migrations

Импорт 1С-файлов https://www.drupal.org/project/cmlmigrations
*
*
