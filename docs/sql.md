# Описания

Sql - клас для доступа к БД
## Использования
```php
<?php
 $DB=new ui_clasess_Sql();
 $DB->select('objid');
 $DB->from('sys_objects');
 $DB->where("objtype = 'sys_ext_modules'");
 
```
