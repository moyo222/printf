ALX Software Engineering Team Project ( Printf)
------------------------------------------------
This is a group project for the C programming language called Printf. It is a printf function that takes various inputs and arguments based on exactly how the standard library function printf operates.

Summary
--------
This function _printf() writes output to stdout, the standard output stream with the format and options without making use of any of the standard library files. The function writes under the control of a format string which is composed of zero or more directives. It was written to use a local buffer of 1024 bytes when printing; it can print larger sets of data.

Prototype: `int _printf(const char *format, . . . );`

Return Value
-------------
The _printf() function returns the total number of characters printed to the stdout(excluding the null byte at the end of strings) after a successful execution. If an output error is encountered, a negative value of -1 is returned.

Format of the Argument String
-----------------------------
The format string argument is a constant character string composed of zero or more directives: ordinary characters (not %) which are copied unchanged to the output stream; and conversion specifications, each of which results in fetching zero or more subsequent arguments. Conversion specification is introduced by the character % and ends with a conversion specifier. In between the % character and conversion specifier, there may be (in order) zero or more flags, an optional minimum field width, an optional precision and an optional length modifier. The arguments must correspond with the conversion specifier, and are used in the order given.

Flag Characters
---------------
| Flag | Description |
| --- | --- |
| # | For o conversions the first character of the output string is made zero (by prefixing a 0 if it was not zero already). For x and X conversions, a nonzero result has the string "0x" or "0X" respectively added. |
| - | (Minus sign, not implemented yet) The converted value is to be left adjusted on the field boundary, (Default is right justification) and padded with blanks in the right rather than on the left with blanks or zeros. This flag overrides 0 if both are given. |
| 0 | (Not implemented yet) The value should be zero padded. For d, i, o, u, x, and X the converted value is padded on the left with zeros. If the 0 and - flags both appear,the 0 flag is ignored. If a precision is given with a numeric conversion, the 0 flag is ignored. |
| + | A sign (+ or -) should always be placed before a number produced with a signed conversion. By default, only negative numbers have this sign. |
| ' '| (Blank Space) The argument is padded with a single blank space before a positive number or empty string produced by a signed conversion. |

Field Width
-----------
After flags, a minimum field width may be specified by a decimal digit string The first digit must be non-zero. If the converted value has fewer characters than the provided width, the output is padded on the left or right with spaces (depending on whether the - flag was provided).

Example ```main.c```:
```
int main(void)
{
    _printf("%6d\n", 6);
}
```
Output:
```
   6
```
On the other hand, width may be provied as an argument using the * character For example, in the following:
```
_printf("%*d\n", 8, 2);
```
the argument 8 is considered the width for the conversion of the decimal 2.

The Precision
--------------
After any provided width or flags, a precision may be specified by a `.` A negative precision is taken as if the precision were omitted. For d, i, o, u, x, and X conversions, the precision specifies the minimum number of digits to appear. For s and S conversions, the precision specifies the maximum characters to be printed.

Example `main.c`:

```
int main(void)
{
    _printf("%.8d\n", 8);
}
```
Output:
```
00000008
```
Also, a character * can be used instead of a decimal string. In this case, an argument passed to the function will be taken as the precision value. for example, `_printf("%.*d\n", 8, 1);` the argument `8` is considered the precision for the conversion of the decimal `1`.

Length Modifiers
----------------
| Modifier | Description |
| --- | --- |
| h | It specifies that an integer conversion corresponds to a `short int` or `unsigned short int` argument. |
| l | It specifies that an integer conversion corresponds to a `long int` or `unsigned long int` argument. |

Conversion specifier
------------------------
| Specifier | Description |
| --- | --- |
| d,i | The `int` argument is converted to a signed decimal notation. If precision is present,it gives the minimum number of digits that must appear; if the converted value requires fewer digits, then it is padded with zeros on the left. Default precision is 1.
| o, u, x, X | The unsigned int argument is converted to unsigned octal `(o)`, unsigned decimal `(u)`, or unsigned hexadecimal `(x and X)`. The letters `abcdef` are used for `x` conversions and the letters `ABCDEF` are used for `X` conversions. |
| b | The `unsigned int` argument is converted to a signed decimal notation. |
| c | The `int` argument is converted to an `unsigned char` and the resulting character is written. |
| s | The `const char *` argument is expected to be a pointer to a character array (i.e. pointer to a string). Characters from the array are written starting from the first element of the array and ending at, but not including, the terminating null byte `(\0)`. |
| S | The argument received is expected to be a pointer type char * to an array of characters. Characters from this array are printed up to (but not including) a null byte `('\0')`. Non printable `characters (0 < ASCII value < 32 or >= 127)` are printed this way: `\x`, followed by the ASCII code value in hexadecimal (upper case - always 2 characters).
| r | The argument received is expected to be a pointer type `char *` to an array of characters. Characters from this array are printed in reverse order up to (but not including) a null byte `('\0')`. |
| R | The argument received is expected to be a pointer type `char *` to an array of characters. |
| % | A `%` character is written and no conversion is made. |
| p | A void * pointer argument is printed as hexadecimal in lower caps representing an adress in memory. |

Authors
-------
- Oladele Daniel
- Moyo Bankole


