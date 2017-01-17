# Chapter 2 Functions
## Notes

### Variadics
New feature introduced in PHP 5.6 that allowsto explicity denote a function as acepting a variable lenght argument list.
```php
function f($arg1, ...$args) {
}
```
### Argument unpacking
Works on the opposite way of variadics, allowing you to unpack an array-like structure into an argument list when calling a
function or method
## Function definitions

### func_get_arg
Return an item from the argument list.
```php
mixed func_get_arg (int $arg_num)
```

### func_get_args
Retrurn an array comprising a function's argument list.
```php
array func_get_args ( void ) 
```

### func_num_args
Returns the number of arguments passed to the function.
```php 
int funct_num_args ( void )
```
