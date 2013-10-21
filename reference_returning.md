Reference returning
===================

Functions returning a reference requires to be assigned by reference to have an effect.

Example:
--------
(http://3v4l.org/i79WC)

```php
function & retRef()
{
    global $foo;
    return $foo;
}

// don't assign by reference doesn't result in a reference
$foo = 'init';
$bar = retRef();
$bar = 'bar';
var_dump($foo, $bar);

// reset variables
unset($foo, $bar);

// requires to assign the function call by reference
$foo = 'init';
$bar = & retRef();
$bar = 'bar';
var_dump($foo, $bar);
```

```
string(4) "init"
string(3) "bar"
string(3) "bar"
string(3) "bar"
```
