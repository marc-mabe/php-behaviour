Numeric string comparison
=========================

TODO: description

Example:
--------
(http://3v4l.org/ndJDo)

```php
echo "Compare non numeric string to string 0:        ('str' == '0')                 = " . ('str' == '0' ? 'true' : 'false') . "\n";
echo "Compare non numeric string to integer 0:       ('str' == 0)                   = " . ('str' == 0 ? 'true' : 'false') . "\n";

echo "Compare evtl. numeric string to string:        ('1string' == '1')             = " . ('1string' == '1' ? 'true' : 'false') . "\n";
echo "Compare evtl. numeric string to number:        ('1string' == 1)               = " . ('1string' == 1 ? 'true' : 'false') . "\n";

echo "Compare two numeric strings (same semantic 1): ('1e1' == '10')                = " . ('1e1' == '10' ? 'true' : 'false') . "\n";
echo "Compare two numeric strings (same semantic 2): ('1E1' == '10')                = " . ('1E1' == '10' ? 'true' : 'false') . "\n";
echo "Compare two numeric strings (same semantic 3): ('1e-1' == '0.1')              = " . ('1e-1' == '0.1' ? 'true' : 'false') . "\n";
echo "Compare two numeric strings (same semantic 4): ('1E-1' == '0.1')              = " . ('1E-1' == '0.1' ? 'true' : 'false') . "\n";
echo "Compare two numeric strings (same semantic 5): ('+1' == '1')                  = " . ('+1' == '1' ? 'true' : 'false') . "\n";
echo "Compare two numeric strings (same semantic 6): ('+0' == '-0')                 = " . ('+0' == '-0' ? 'true' : 'false') . "\n";

echo "Compare two numeric strings (precision 1):     ('0.99999999999999994' == '1') = " . ('0.99999999999999994' == '1' ? 'true' : 'false') . "\n";
echo "Compare two numeric strings (precision 2):     ('0.99999999999999995' == '1') = " . ('0.99999999999999995' == '1' ? 'true' : 'false') . "\n";

echo "Compare two numeric strings (hex):             ('0x0A' == '10')               = " . ('0x0A' == '10' ? 'true' : 'false') . "\n";
```

```
Compare non numeric string to string 0:        ('str' == '0')                 = false
Compare non numeric string to integer 0:       ('str' == 0)                   = true
Compare evtl. numeric string to string:        ('1string' == '1')             = false
Compare evtl. numeric string to number:        ('1string' == 1)               = true
Compare two numeric strings (same semantic 1): ('1e1' == '10')                = true
Compare two numeric strings (same semantic 2): ('1E1' == '10')                = true
Compare two numeric strings (same semantic 3): ('1e-1' == '0.1')              = true
Compare two numeric strings (same semantic 4): ('1E-1' == '0.1')              = true
Compare two numeric strings (same semantic 5): ('+1' == '1')                  = true
Compare two numeric strings (same semantic 6): ('+0' == '-0')                 = true
Compare two numeric strings (precision 1):     ('0.99999999999999994' == '1') = false
Compare two numeric strings (precision 2):     ('0.99999999999999995' == '1') = true
Compare two numeric strings (hex):             ('0x0A' == '10')               = true
```
