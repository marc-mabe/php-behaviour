Overwriting $this when using references
=======================================

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
