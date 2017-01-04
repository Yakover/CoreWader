# Использования

```php
<?php
 $List = new ui_clasess_Altairtable('');
 $List->addColumn('key','name');
 $List->addData(['key'=>'test']);
 $List->router();
```


## Установка урла даних

Пример:
```php
<?php

 $List = new ui_clasess_Altairtable('');
 $List->addColumn('key','name');
 $List->addData(['key'=>'test']);
 $List->setListUrl('myUrlList');
 $List->router();
 
```
