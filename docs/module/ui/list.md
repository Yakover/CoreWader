# Описание класса Altairtable

**_Altairtable_** - класc, который предоставляет разработчику инструментарий для отображенния списков из DB или Array.
## Использование из DB

Для получения данных используется [ui_clasess_Sql](sql.md)
он хранится в свойстве 
```php
<?php
    $List = new ui_clasess_Altairtable('');
    $List->q = new ui_clasess_Sql();
?>
```
Простой пример использования

```php
<?php
    $List = new ui_clasess_Altairtable('');
    $List->q->select('objid', 'objid');
    $List->q->from('sys_objects');
    $List->q->where("objtype = 'sys_ext_modules'");
    $List->router();
?>
```

Более сложный пример использования 

```php
<?php
    $List = new ui_clasess_Altairtable('');
    $List->q->select('o.id');
    $List->q->select('o.avatar');
    $List->q->select('o.name');
    $List->q->from('wprod_categories o');
    $List->q->leftjoin('wprod_categories p', 'o.parent=p.id');
    $List->q->where("o.id<>'0'");
    $List->q->orderby('o.id ');
    $List->router();
?>
```

Есть возможность кастомизировать столбец под свои нужды.
Для этого необходимо добавить 3й параметр как указано в примере

```php
<?php
    /*...some code...*/
    $List->q->select('o.url', Lang::get('url'), ['formater' => 'urlSite']);
    /*...some code...*/
    function formater_urlSite($contentColum, $columInfo, $countRow, $countCell)
    {
        if ($contentColum) {
            $url = Routing::url($contentColum);
            return '<a target="_blank" href="' . $url . '"><i class="material-icons">launch</i></a>';
        } else {
            return '<i class="material-icons">warning</i>';
        }
    }
?>
```


## Использования из Array



```php
<?php
 $List = new ui_clasess_Altairtable('');
 $List->addColumn('key','name');
 $List->addData(['key'=>'test']);
 $List->router();
```


## Установка урла получения даних

Пример:
```php
<?php

 $List = new ui_clasess_Altairtable('');
 $List->setListUrl('myUrlList');
 
```
