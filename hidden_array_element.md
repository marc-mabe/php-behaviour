Hidden array elements
=====================

In PHP you can cast an object into an array.
(See http://www.php.net/manual/language.types.array.php#language.types.array.casting)
> If an object is converted to an array, the result is an array whose elements are the
> object's properties. The keys are the member variable names.

With the dynamic object property notation you can create properties with numeric names like `123`.
Now if you cast such an object to an array you can't access such numeric properties because numeric
array keys wil be converted to integer.

Example:
--------
(http://3v4l.org/6uFqf)

```php
$obj = new stdClass();
$obj->{123}   = "foo";
$obj->{'456'} = "bar";

$arr = (array)$obj;

var_dump($arr);
var_dump($arr['123'], $arr[123]);
var_dump($arr['456'], $arr[456]);
```

```
array(2) {
    ["123"] => string(3) "foo"
    ["456"] => string(3) "bar"
}

Notice: Undefined offset: 123 in ... on line 10
Notice: Undefined offset: 123 in ... on line 10
NULL
NULL

Notice: Undefined offset: 456 in ... on line 11
Notice: Undefined offset: 456 in ... on line 11
NULL
NULL
```
