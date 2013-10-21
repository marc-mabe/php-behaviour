Late constant binding
=====================

Class constants will be initialized on first read instead of compile-time.

On defining a class constant linking to another constant you will get the following:

 * *No* notice about an undefined constant on compile time
 * Reading your class constant *before* defining the linked constant changes constant value (and triggers a notice)

Example:
--------
(http://3v4l.org/PPTks)

```php
// define class constant linking to a not defined constant
class Foo {
    const FOO = FOO;
}

class Bar {
    const BAR = BAR;
}

echo "Define the linked constant AFTER reading:\n";
Foo::FOO;
define('FOO', 'Value of FOO');
var_dump(Foo::FOO);

echo "Define the linked constant BEFORE reading:\n";
define('BAR', 'Value of BAR');
var_dump(Bar::BAR);
```

```
Define the linked constant AFTER reading:

Notice: Use of undefined constant FOO - assumed 'FOO' in ... on line 13
string(3) "FOO"
Define the linked constant BEFORE reading:
string(12) "Value of BAR" 
```
