Hidden array elements
=====================

**Note:** This has been fixed in PHP 7.2.0.

With *hidden array elements* I mean array elements you can't access anymore.
They will be still displayed using debugging functions like `var_dump`.

Short description
-----------------

On creating object properties with numeric names and casting such an object into an array
the numeric object properties are hidden array elements.

Long description
----------------

In PHP you can cast an object into an array.
(See http://www.php.net/manual/language.types.array.php#language.types.array.casting)
> If an object is converted to an array, the result is an array whose elements are the
> object's properties. The keys are the member variable names.

Normally object propertie names can't be numeric because something like `$obj->123` isn't valid.
But if you use dynmaic object property notation like `$obj->{123}` it's possible.

Now if you cast such an object into an array the key becomes the numeric property name as a string
and because numeric array keys will be converted into integers you can't acces such numeric strings.

PS: Object properties will be strings even if you create it as an integer.

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
