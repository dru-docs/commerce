# Процесс (Pipeline) обмена.

* За обмен файлами отвечает cmlexchange, 1С приходит на один из адресов:
  - /cmlexchange - инкрементальная выгрузка
  - /cmlexchange/full - полная выгрузка 
* Открытие роута запускает `\Drupal::service('cmlexchange.protocol')->init();`
  - Проверяется авторизация
  - Передаются файлы
  - Запускается `import_pipeline`
* `import_pipeline` проверяет необходимость unZip `\Drupal::service('cmlexchange.import_pipeline')->process();`
  - проверяем необходимость unZip
  - проверяем наличие модуля `cmlmigrations` и конфиг-галочки `cmlexchange.settings.cmlmigrations`
  - запускаем `mlmigrations.pipeline`
  - или завершаем процесс если не требуется импорт данных: отвечаем `success` и ставим `success`-статус у `$cml`
* `mlmigrations.pipeline` отвечает за миграции `\Drupal::service('mlmigrations.pipeline')->init();`
  - проверяем наличие незавершённых предыдущий миграций (со статусом `progress`) `$this->query('progress')` и делаем их текущими.
  - TODO (такое ощущение что в этом месте могли что-то забыть)
  - сохраняем текущий cml-id в `cmlmigrations.settings.runing_cml`
  - получаем информацию о миграциях `$migrations` ($migrations[list] список, $migrations[status] - все миграции в Idle?)
  - переходим в $this->import($cml, $migrations)
* Переключатель статусов
