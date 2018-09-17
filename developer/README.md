# Developer

## Описание функционала.

### CmlAPI  https://www.drupal.org/project/cmlapi

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
  - 
* Крон и сервис `cmlapi.cleaner`:
  - удаление пустых обменов (которые не содежрат файлы)
  - удаление старых обменов (старше чем хх)
* Сервис доступа к обмену `cmlapi.cml`
  - текущий обмен
  - актуальный обмен
* Парсер-сервисы
  - `cmlapi.xml_parser` - разбор XML
  - `cmlapi.parser_catalog` - вытащить из XML-объекта каталоги и другую таксономию
  - `cmlapi.parser_product` - вытащить из XML-объекта товары в соответсвии с мапингом
  - `cmlapi.parser_offers` - вытащить из XML-объекта оферы в соответствии с мапингом
* Настройка мапинга для `parser_product` и `parser_offers`
  - стандартный мапинг
  - дополнительный мапинг
* Реализация 
#### Стандартный мапинг `parser_product`
```yml
Ид:
Артикул:
Штрихкод:
Наименование:
ПометкаУдаления:
БазоваяЕдиница: {type: 'attr', skip: 1, attr: 'НаименованиеПолное'}
Группы: {type: []}
Категория:
Описание:
Картинка:
Изготовитель: {type: 'keyval'}
СтавкиНалогов: {type: 'keyval', skip: 1}
ЗначенияСвойств: {type: 'keyval'}
ЗначенияРеквизитов: {type: 'keyval'}
```
#### Стандартный мапинг `parser_offers`
```yml
Ид:
Наименование:
БазоваяЕдиница: {type: 'attr', skip: 1, attr: 'НаименованиеПолное'}
Количество:
Склад: {type: 'attr', attr: 'КоличествоНаСкладе'}
Цены: {type: []}
```

### Cml Exchange
Обмен файлами с 1С https://www.drupal.org/project/cmlexchange
* Реализация протокола обмена
*


### Cml Migrations

Импорт 1С-файлов https://www.drupal.org/project/cmlmigrations
*
*
