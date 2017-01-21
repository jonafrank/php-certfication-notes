# Chapter 3 Strings

## Workging with strings
The standard PHP string function work on a per-byte basis, not per-character basis. If you wish to work with multibyte strings, you should look at the `iconv` an `mbstring` extensions.

## Using strings as Arrays
You can access individual characters of a string as if they were members of an array. For example:
```php
$string = 'abcdef';
echo $string[1]; // Outputs 'b'
```

## Simple searching functionality.

The simplest way to search inside a string is to use the `strpos()` and `strstr()` families of functions. The former allows yo to find the position of a substring (needle) inside a string
(haystack). It returns either the numeric position of the needle's first occurrence within the haystack, or `false`.

The `strstr()` returns the portion of the haystack that sarts with the needle instead of the latter's position.

> In general, `strstr()` is slower than `strpos()`.

`strpos()` and `strstr()` are case sensitive and start looking for the needle from the beginning of the haystack. But PHP also provides variants that work in a case-insensitive way or start looking for the needle from the end of the haystack. For Example:
* [`stripos()`](http://php.net/manual/en/function.stripos.php)
* [`stristr()`](http://php.net/manual/en/function.stristr.php)
* [`strrpos()`](http://php.net/manual/en/function.strrpos.php)


## Functions Definitions

### strlen
Get the string lenght in bytes.
```php
int strlen ( string $string )
```

### strtr
Translate characters or replace substrings.
```php
string strtr ( string $str, string $from, string $to)

string strtr ( string $str, array $replace_pairs)
```

### strcmp
Binary safe string comparison. Returns 0 if both strings are equal.
```php
int strcmp ( string $str1, string $str2 )
```

### strcasecmp
Binary safe case-insensitive string coomparision. Returns 0 if both strings are insensitive equal.
```php
int strcasecmp ( string $str1, string $str2)
```

### strncasecmp
Binary safe case-insensitive string comparison of the first n characters.
```php
int strncasecmp( string $str1, string $str2, int $len)
```
Returns < 0 if **str1** is less than **str2**; > 0 if **str1** is grater than **str2**, and 0 if they are equal.

### strpos
Find the position of the first occurrence of a substring in a string.
```php
mixed strpos ( string $haystack , mixed $needle [, int $offset = 0 ] )
```
Returns the position of where the needle exists relative to the beginning of the **haystack** string (independent of the offset ). Rturns **FALSE** if the needle was not found.

### strstr
Find the first occurrence of a string.
```php
string strstr ( string $haystack , mixed $needle [, bool $before_needle = false ] )
```
Returns part of the **haystack** string starting from and including the first occurrence of the **needle** to the end of **haystack*
