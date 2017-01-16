# Описание класса Altairtable

**_Altairtable_** - класc, который предоставляет разработчику инструментарий для отображенния списков из DB или Array.

## Использование из DB

Для получения данных из базы данных используется [ui_clasess_Sql](sql.md)
он хранится в свойстве класса
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

Таким образом, из примера выше видно, что с помощью класса [ui_clasess_Sql](sql.md) можно написать абсолютно любой SQL запрос.

## Использования из Array

```php
<?php
 $List = new ui_clasess_Altairtable('');
 $List->addColumn('key','name');
 $List->addData(['key'=>'test']);
 $List->router();
```

## Возможности класса

Данный класс предоставляет инструментарий для кастомизации получаемого поля.
Для этого необходимо добавить 3й параметр (formater) в строку получаемого поля, как указано в примере

```php
<?php
    /*...some code...*/
    
    $List->q->select('o.url', Lang::get('url'), ['formater' => 'urlSite']);
    
    /*...some code...*/
    
    function formater_urlSite($contentColum, $columInfo, $countRow, $countCell)
    {
        /*...some logic...*/
    }
?>
```

$contentColum - значение текущего поля.
$columInfo - массив ключей и значений всех полей, которые указаны в запросе.

При отображении конечного списка, вывод данных будет с учетом отработки функции formater




## Установка урла получения даних

Пример:
```php
<?php

 $List = new ui_clasess_Altairtable('');
 $List->setListUrl('myUrlList');
 
```
