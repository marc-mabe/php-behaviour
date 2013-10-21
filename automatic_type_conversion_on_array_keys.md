Automatic type conversion on array keys
=======================================

Only strings and integers are allowed as array keys.

NULLs, floating point numbers and booleans will be automatically converted without any notice.
(Already defined keys with the same name will be overwritten without any notice.)

Numeric strings will also be converted into integers without any notice.
(Already defined keys with the same name will be overwritten without any notice.)

Other types will trigger a warning and no array entry will be generated.

Example:
--------
(http://3v4l.org/m3SGv)

```php
echo "Numeric strings will be converted into an integer:\n";
var_dump(array(
    -1    => -1,
    1     => 1,

    '1'   => '1',
    '-1'  => '-1',
    '1.1' => '1.1',
    's1'  => 's1',
));

echo "Floating point numbers will be converted into an integer:\n";
var_dump(array(
    -1  => -1,
    0   => 0,
    1   => 1,

    -1.9 => -1.9,
	0.9  => 0.9,
	1.9  => 1.9
));

echo "Booleans will be converted into an integer:\n";
var_dump(array(
    0     => 0,
    1     => 1,

    true  => true,
    false => false,
));

echo "NULL will be converted into an empty string:\n";
var_dump(array(
    ''   => '',
    null => null,
));
```

```
Numeric strings will be converted into an integer:
array(4) {
    [-1]    => string(2) "-1"
    [1]     => string(1) "1"
    ["1.1"] => string(3) "1.1"
    ["s1"]  => string(2) "s1"
}

Floating point numbers will be converted into an integer:
array(3) {
    [-1] => float(-1.9)
    [0]  => float(0.9)
    [1]  => float(1.9)
}

Booleans will be converted into an integer:
array(2) {
    [0] => bool(false)
    [1] => bool(true)
}

NULL will be converted into an empty string:
array(1) {
    [""] => NULL
}
```
