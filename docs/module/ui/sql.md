# Описания

Sql - клас для быстрого построения запросов
## Использования
```php
<?php
 $DB=new ui_clasess_Sql();
 $DB->select('objid');
 $DB->from('sys_objects');
 $DB->where("objtype = 'sys_ext_modules'");
 $sql=$DB->getSql();
```
## parseSql

Parsing SQL statement

```php
<?php
 $DB=new ui_clasess_Sql();
 $DB->select('objid');
 $DB->from('sys_objects');
 $DB->where("objtype = 'sys_ext_modules'");
 $sql=$DB->parseSql($DB->getSql());
```