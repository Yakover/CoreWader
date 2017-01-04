# Описания

Altairtable - клас служит для отображенния даных из DB или Array
## Использования из DB

Для получения даних используется  [ui_clasess_Sql](sql.md)
он хранится в свойстве 
```php
<?php
 $List = new ui_clasess_Altairtable('');
 $List->q=new ui_clasess_Sql();
```
Пример использования

```php
<?php
 $List = new ui_clasess_Altairtable('');
 $List->q->select('objid', 'objid');
 $List->q->from('sys_objects');
 $List->q->where("objtype = 'sys_ext_modules'");
 $List->router();
```

### Использования из Array



```php
<?php
 $List = new ui_clasess_Altairtable('');
 $List->addColumn('key','name');
 $List->addData(['key'=>'test']);
 $List->router();
```


### Установка урла получения даних

Пример:
```php
<?php

 $List = new ui_clasess_Altairtable('');
 $List->setListUrl('myUrlList');
 
```
