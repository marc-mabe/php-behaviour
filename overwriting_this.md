Overwriting $this when using references
=======================================

**NOTE: This has been fixed in PHP-7.1**

It's possible to change the special variable `$this` (used to reference the current object).

Example:
--------
(http://3v4l.org/2eNuB)

```php
class x
{
    public function __construct()
    {
        $x =& $this;
        $x = new stdClass;
        var_dump($this);
    }
}
var_dump(new x);
```

Output:
```
object(stdClass)#2 (0) { }
object(x)#1 (0) { }
```

Expected:
```
object(x)#1 (0) { }
object(x)#1 (0) { }
```
