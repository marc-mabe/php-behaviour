Change boolean constants TRUE/FALSE (within a namespace)
========================================================

**NOTE: This has been fixed in PHP-7**

Because TRUE and FALSE are constants of the root namespace
you can define your own constants within another namespace.

Example:
--------
(http://3v4l.org/hq7Jj)

```php
namespace Foo;
define('Foo\\true', \false);
define('Foo\\false', \true);

var_dump(array(
    'true'  => true,
    'false' => false,
    '1===1' => 1===1,
    '1!==1' => 1!==1,
));
```

```
array(4) {
    ["true"]  => bool(false),
    ["false"] => bool(true),
    ["1===1"] => bool(true),
    |"1!==1"] => bool(false)
}
```
