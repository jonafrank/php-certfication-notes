# Chapter 3 Strings

## Workging with strings
The standard PHP string function work on a per-byte basis, not per-character basis. If you wish to work with multibyte strings, you should look at the `iconv` an `mbstring` extensions.

## Using strings as Arrays
You can access individual characters of a string as if they were members of an array. For example:
```php
$string = 'abcdef';
echo $string[1]; // Outputs 'b'
```

### Simple searching functionality.

The simplest way to search inside a string is to use the `strpos()` and `strstr()` families of functions. The former allows yo to find the position of a substring (needle) inside a string
(haystack). It returns either the numeric position of the needle's first occurrence within the haystack, or `false`.

The `strstr()` returns the portion of the haystack that sarts with the needle instead of the latter's position.

> In general, `strstr()` is slower than `strpos()`.

`strpos()` and `strstr()` are case sensitive and start looking for the needle from the beginning of the haystack. But PHP also provides variants that work in a case-insensitive way or start looking for the needle from the end of the haystack. For Example:
* [`stripos()`](http://php.net/manual/en/function.stripos.php)
* [`stristr()`](http://php.net/manual/en/function.stristr.php)
* [`strrpos()`](http://php.net/manual/en/function.strrpos.php)

### Matching against a Mask
You can use the [`strspn`](http://php.net/manual/en/function.strspn.php) function to match a string against a "whitelist" mask of allowed characters. Returns the length of the initial
segment of the string that contains any of the characters specified in the mask.

```php
 $string = '133445abcdef';
 $mask = '12345'
 echo strspn($string, $mask); // Outputs 6
```
> The [`strcspn()`](http://php.net/manual/en/function.strcspn.php) function works just like `strspn()`, but uses a blacklist approach instead.

Both `strspn()` and `strcspn()` accept two optional parameters that define the starting position and the length of the string to examine.

### Simple Search and Replace Operations
Simple substitutions are performed using [`str_replace()`](http://php.net/manual/en/function.str-replace.php) --[`str_ireplace()`](http://php.net/manual/en/function.str-ireplace.php)
for case insensitive-- and [`substr_replace()`](http://php.net/manual/en/function.substr-replace.php).

```php
// Outputs Hello Reader
echo str_replace('World', 'Reader', 'Hello World');

// Also outputs Hello Reader
echo str-ireplace ('world', 'Reader', 'Hello Reader');
```

The function takes three parameters: a needle, a replacement string and a haystack. Optionally, you can specify a third parameter, passed by reference, that the function fill, upon return, with the number of substitutions made.

If you need to search and replace more than one needle at a time, you can pass the first two arguments to `str_replace()` in the form of arrays.

To replace a portion of the needle of which yo already know the starting and ending point, you can use `substr_replace()`.

```php
echo substr_replace( 'Hello World', 'Reader', 6);
echo substr-replace(
  'Canned tomatoes are good', 'potatoes', 7, 8
);
```
the third argument is our starting point. You can also pass an optional fourth parameter to define the end of the substring that will be replaced.

### Extracting substrings

[`substr()`](http://php.net/manual/en/function.substr.php) function allows you to extract a substring from a larger string. I takes three parameters: the string to be worked on, a
starting index and optional length. The starting index can be specified as either a positive integer (meaning the index of a character in the string starting from the beginning) or a
negative integer (meaning the index of a character starting from the end).

```php
$x = '1234567';
echo substr($x, 0, 3); // 123
echo substr($x, 1, 1); // 2
echo substr($x, -2) // 67
echo substr($x, 1) // 234567
echo substr($x -2, 1) // 6 
```

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
