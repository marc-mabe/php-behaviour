Callable type-hint not directly callable
========================================

Arguments marked with the callable type-hint aren't directly callable
because a string to a static method `"Class::method"` will be interpreted
as a normal function.

To resolve that, you have to call `call_user_func[_array]()`.

Example:
--------
(http://3v4l.org/rGc3F)

```php
class Foo {
    public static function bar() {
        return __METHOD__;
    }
}

function call(callable $func) {
    return $func();
}

// works
$callable = array('Foo', 'bar');
var_dump($callable());
var_dump(call($callable));

// Call to undefined function Foo::bar()
$callable = 'Foo::bar';
var_dump(call($callable)); // or var_dump($callable());
```

```
string(8) "Foo::bar"
string(8) "Foo::bar"

Fatal error: Call to undefined function Foo::bar() in ... on line 10
```

Note the message `... undefined function ...`.
On calling an undefined static method the message will be `... undefined method ...`.
