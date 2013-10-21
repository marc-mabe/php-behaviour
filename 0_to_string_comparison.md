0 to string comparison
======================

On compare an integer `0` with a string you'll get `TRUE` if the string isn't `"1"`.

(See PHP documentation of [Loose comparisons with ==](http://php.net/manual/en/types.comparisons.php#types.comparisions-loose))

Example:
--------
(http://3v4l.org/e1i2O)

```php
var_dump(array(
    '0 == "one"'  => (0 == "one"),
    '0 == "null"' => (0 == "null"),
    '0 == "1"'    => (0 == "1"),
    '0 == "0"'    => (0 == "0"),
    '0 == ""'     => (0 == ""),
));

```

```
array(5) {
    ["0 == "one""]  => bool(true),
    ["0 == "null""] => bool(true),
    ["0 == "1""]    => bool(false),
    ["0 == "0""]    => bool(true),
    ["0 == """]     => bool(true),
}
```
