[Pop-out for expression functions](https://adfdataflowexecutor.azurewebsites.net)

**NOTE: For Regular Expressions, you currently must escape backslashes. Eg: samples below listed as \d+ must be entered in the ADF Data Flow Expression Builder as \\d+**

*********************************
isNull
==============================
<b>isNull(<i>&lt;value1&gt;</i> : any) => boolean</b><br/><br/>
Checks if the value is NULL
* isNull(NULL()) -> true
* isNull('') -> false'
*********************************
null
==============================
<b>null() => null</b><br/><br/>
Returns a NULL value. Use the function syntax(null()) if there is a column name named 'null'. Any operation that uses will result in a NULL
* custId = NULL (for derived field)
* custId == NULL -> NULL
* 'nothing' + NULL -> NULL
* 10 * NULL -> NULL'
* NULL == '' -> NULL'
*********************************
iif
==============================
<b>iif(<i>&lt;condition&gt;</i> : boolean, <i>&lt;true_expression&gt;</i> : any, [<i>&lt;false_expression&gt;</i> : any]) => any</b><br/><br/>
Based on a condition applies one value or the other. If other is unspecified it is considered NULL. Both the values must be compatible(numeric, string...)
* iif(custType == 'Premium', 10, 4.5)
* iif(amount > 100, 'High')
* iif(dayOfWeek(saleDate) == 6, 'Weekend', 'Weekday')
*********************************
case
==============================
<b>case(<i>&lt;condition&gt;</i> : boolean, <i>&lt;true_expression&gt;</i> : any, <i>&lt;false_expression&gt;</i> : any, ...) => any</b><br/><br/>
Based on alternating conditions applies one value or the other. If the number of inputs are even, the other is NULL for last condition
* case(custType == 'Premium', 10, 4.5)
* case(custType == 'Premium', price*0.95, custType == 'Elite',   price*0.9, price*2)
* case(dayOfWeek(saleDate) == 1, 'Sunday', dayOfWeek(saleDate) == 6, 'Saturday')
*********************************
equalsIgnoreCase
==============================
<b>equalsIgnoreCase(<i>&lt;value1&gt;</i> : string, <i>&lt;value2&gt;</i> : string) => boolean</b><br/><br/>
Comparison equals operator ignoring case. Same as <=> operator
* 'abc'=='abc' -> true
* equalsIgnoreCase('abc', 'Abc') -> true
*********************************
concat
==============================
<b>concat(<i>&lt;this&gt;</i> : string, <i>&lt;that&gt;</i> : string, ...) => string</b><br/><br/>
Concatenates a variable number of strings together. Same as the + operator with strings
* concat('Awesome', 'Cool', 'Product') -> 'AwesomeCoolProduct'
* 'Awesome' + 'Cool' + 'Product' -> 'AwesomeCoolProduct'
* concat(addrLine1, ' ', addrLine2, ' ', city, ' ', state, ' ', zip)
* addrLine1 + ' ' + addrLine2 + ' ' + city + ' ' + state + ' ' + zip
*********************************
concatWS
==============================
<b>concatWS(<i>&lt;separator&gt;</i> : string, <i>&lt;this&gt;</i> : string, <i>&lt;that&gt;</i> : string, ...) => string</b><br/><br/>
Concatenates a variable number of strings together with a separator. The first parameter is the separator
* concatWS(' ', 'Awesome', 'Cool', 'Product') -> 'Awesome Cool Product'
* concatWS(' ' , addrLine1, addrLine2, city, state, zip) ->
* concatWS(',' , toString(order_total), toString(order_discount))
*********************************
trim
==============================
<b>trim(<i>&lt;string to trim&gt;</i> : string, [<i>&lt;trim characters&gt;</i> : string]) => string</b><br/><br/>
Trims a string of leading and trailing characters. If second parameter is unspecified, it trims whitespace. Else it trims any character specified in the second parameter
* trim('!--!wor!ld!', '-!') -> 'wor!ld'
*********************************
ltrim
==============================
<b>ltrim(<i>&lt;string to trim&gt;</i> : string, <i>&lt;trim characters&gt;</i> : string) => string</b><br/><br/>
Left trims a string of leading characters. If second parameter is unspecified, it trims whitespace. Else it trims any character specified in the second parameter
* ltrim('!--!wor!ld!', '-!') -> 'wor!ld!'
*********************************
rtrim
==============================
<b>rtrim(<i>&lt;string to trim&gt;</i> : string, <i>&lt;trim characters&gt;</i> : string) => string</b><br/><br/>
Right trims a string of leading characters. If second parameter is unspecified, it trims whitespace. Else it trims any character specified in the second parameter
* rtrim('!--!wor!ld!', '-!') -> '!--!wor!ld'
*********************************
substring
==============================
<b>substring(<i>&lt;string to subset&gt;</i> : string, <i>&lt;from 1-based index&gt;</i> : integral, [<i>&lt;number of characters&gt;</i> : integral]) => string</b><br/><br/>
Extracts a substring of a certain length from a position. Position is 1 based. If the length is omitted, it is defaulted to end of the string
* substring('Cat in the hat', 5, 2) -> 'in'
* substring('Cat in the hat', 5, 100) -> 'in the hat'
* substring('Cat in the hat', 5) -> 'in the hat'
* substring('Cat in the hat', 100, 100) -> ''
*********************************
lower
==============================
<b>lower(<i>&lt;value1&gt;</i> : string) => string</b><br/><br/>
Lowercases a string
* lower('GunChus') -> 'gunchus'
*********************************
upper
==============================
<b>upper(<i>&lt;value1&gt;</i> : string) => string</b><br/><br/>
Uppercases a string
* upper('bojjus') -> 'BOJJUS'
*********************************
length
==============================
<b>length(<i>&lt;value1&gt;</i> : string) => integer</b><br/><br/>
Returns the length of the string
* length('kiddo') -> 5
*********************************
rpad
==============================
<b>rpad(<i>&lt;string to pad&gt;</i> : string, <i>&lt;final padded length&gt;</i> : integral, <i>&lt;padding&gt;</i> : string) => string</b><br/><br/>
Right pads the string by the supplied padding until it is of a certain length. If the string is equal or greater than the length it is a no-op
* rpad('great', 10, '-') -> 'great-----'
* rpad('great', 4, '-') -> 'great'
* rpad('great', 8, '<>') -> 'great<><'
*********************************
lpad
==============================
<b>lpad(<i>&lt;string to pad&gt;</i> : string, <i>&lt;final padded length&gt;</i> : integral, <i>&lt;padding&gt;</i> : string) => string</b><br/><br/>
Left pads the string by the supplied padding until it is of a certain length. If the string is equal or greater than the length it is a no-op
* lpad('great', 10, '-') -> '-----great'
* lpad('great', 4, '-') -> 'great'
* lpad('great', 8, '<>') -> '<><great'
*********************************
left
==============================
<b>left(<i>&lt;string to subset&gt;</i> : string, <i>&lt;number of characters&gt;</i> : integral) => string</b><br/><br/>
Extracts a substring start at index 1 with number of characters. Same as SUBSTRING(str, 1, n)
* left('bojjus', 2) -> 'bo'
* left('bojjus', 20) -> 'bojjus'
*********************************
right
==============================
<b>right(<i>&lt;string to subset&gt;</i> : string, <i>&lt;number of characters&gt;</i> : integral) => string</b><br/><br/>
Extracts a substring with number of characters from the right. Same as SUBSTRING(str, LENGTH(str) - n, n)
* right('bojjus', 2) -> 'us'
* right('bojjus', 20) -> 'bojjus'
*********************************
startsWith
==============================
<b>startsWith(<i>&lt;string&gt;</i> : string, <i>&lt;substring to check&gt;</i> : string) => boolean</b><br/><br/>
Checks if the string starts with the supplied string
* startsWith('great', 'gr') -> true
*********************************
endsWith
==============================
<b>endsWith(<i>&lt;string&gt;</i> : string, <i>&lt;substring to check&gt;</i> : string) => boolean</b><br/><br/>
Checks if the string ends with the supplied string
* endsWith('great', 'eat') -> true
*********************************
locate
==============================
<b>locate(<i>&lt;substring to find&gt;</i> : string, <i>&lt;string&gt;</i> : string, [<i>&lt;from index - 1-based&gt;</i> : integral]) => integer</b><br/><br/>
Finds the position(1 based) of the substring within a string starting a certain position. If the position is omitted it is considered from the beginning of the string. 0 is returned if not found
* locate('eat', 'great') -> 3
* locate('o', 'microsoft', 6) -> 7
* locate('bad', 'good') -> 0
*********************************
instr
==============================
<b>instr(<i>&lt;string&gt;</i> : string, <i>&lt;substring to find&gt;</i> : string) => integer</b><br/><br/>
Finds the position(1 based) of the substring within a string. 0 is returned if not found
* instr('great', 'eat') -> 3
* instr('microsoft', 'o') -> 7
* instr('good', 'bad') -> 0
*********************************
translate
==============================
<b>translate(<i>&lt;string to translate&gt;</i> : string, <i>&lt;lookup characters&gt;</i> : string, <i>&lt;replace characters&gt;</i> : string) => string</b><br/><br/>
Replace one set of characters by another set of characters in the string. Characters have  1 to 1 replacement
* translate('(Hello)', '()', '[]') -> '[Hello]'
* translate('(Hello)', '()', '[') -> '[Hello'
*********************************
reverse
==============================
<b>reverse(<i>&lt;value1&gt;</i> : string) => string</b><br/><br/>
Reverses a string
* reverse('gunchus') -> 'suhcnug'
*********************************
initCap
==============================
<b>initCap(<i>&lt;value1&gt;</i> : string) => string</b><br/><br/>
Converts the first letter of every word to uppercase. Words are identified as separated by whitespace
* initCap('cool iceCREAM') -> 'Cool IceCREAM'
*********************************
replace
==============================
<b>replace(<i>&lt;string&gt;</i> : string, <i>&lt;substring to find&gt;</i> : string, <i>&lt;substring to replace&gt;</i> : string) => string</b><br/><br/>
Replace all occurences of a substring with another substring in the given string
* replace('doggie dog', 'dog', 'cat') -> 'catgie cat'
* replace('doggie dog', 'dog', '') -> 'gie'
*********************************
regex_replace
==============================
<b>regex_replace(<i>&lt;string&gt;</i> : string, <i>&lt;regex to find&gt;</i> : string, <i>&lt;substring to replace&gt;</i> : string) => string</b><br/><br/>
Replace all occurences of a regex pattern with another substring in the given string
* regex_replace('100 and 200', '(\d+)', 'digits') -> 'digits and digits'
*********************************
regex_extract
==============================
<b>regex_extract(<i>&lt;string&gt;</i> : string, <i>&lt;regex to find&gt;</i> : string, [<i>&lt;match group 1-based index&gt;</i> : integral]) => string</b><br/><br/>
Extract a matching substring for a given regex pattern. The last parameter identifies the match group and is defaulted to 1 if omitted
* regex_extract('Cost is between 600 and 800 dollars', '(\d+) and (\d+)', 2) -> '800'
*********************************
regex_match
==============================
<b>regex_match(<i>&lt;string&gt;</i> : string, <i>&lt;regex to match&gt;</i> : string) => boolean</b><br/><br/>
Checks if the string matches the given regex pattern
* regex_match('200.50', '(\d+).(\d+)') -> true
*********************************
like
==============================
<b>like(<i>&lt;string&gt;</i> : string, <i>&lt;pattern match&gt;</i> : string) => boolean</b><br/><br/>
The pattern is a string which is matched literally, with exception to the following special symbols:  _ matches any one character in the input (similar to . in posix regular expressions)
  % matches zero or more characters in the input (similar to .* in posix regular expressions).
  The escape character is ''. If an escape character precedes a special symbol or another escape character, the following character is matched literally. It is invalid to escape any other character.
* like('icecream', 'ice%') -> true
*********************************
rlike
==============================
<b>rlike(<i>&lt;string&gt;</i> : string, <i>&lt;pattern match&gt;</i> : string) => boolean</b><br/><br/>
Checks if the string matches the given regex pattern
* rlike('200.50', '(\d+).(\d+)') -> true
*********************************
in
==============================
<b>in(<i>&lt;array of items&gt;</i> : array, <i>&lt;item to find&gt;</i> : any) => boolean</b><br/><br/>
Checks if an item is in the array
* in([10, 20, 30], 10) -> true
* in(['good', 'kid'], 'bad') -> false
*********************************
toString
==============================
<b>toString(<i>&lt;value&gt;</i> : any, [<i>&lt;number format/date format&gt;</i> : string]) => string</b><br/><br/>
Converts a primitive datatype to a string. For numbers and date a format can be specified. If unspecified the system default is picked.Java decimal format is used for numbers. Default date format is yyyy-mm-dd
* toString(10) -> '10'
* toString('engineer') -> 'engineer'
* toString(123456.789, '##,###.##') -> '123,456.79'
* toString(123.78, '000000.000') -> '000123.780'
* toString(12345, '##0.#####E0') -> '12.345E3'
* toString(toDate('2018-12-31')) -> '2018-12-31'
* toString(toDate('2018-12-31'), 'mm/dd/yy') -> '12/31/18'
* toString(4 == 20) -> 'false'
*********************************
split
==============================
<b>split(<i>&lt;string to split&gt;</i> : string, <i>&lt;split characters&gt;</i> : string) => array</b><br/><br/>
Splits a string based on a delimiter and returns an array of strings
* split('100,200,300', ',') -> ['100', '200', '300']
* split('100,200,300', '|') -> ['100,200,300']
* split('100, 200, 300', ', ') -> ['100', '200', '300']
* split('100200300', ',') -> ['100200300']
*********************************
regex_split
==============================
<b>regex_split(<i>&lt;string to split&gt;</i> : string, <i>&lt;regex expression&gt;</i> : string) => array</b><br/><br/>
Splits a string based on a delimiter based on regex and returns an array of strings
* regex_split('oneAtwoBthreeC', '[CAB]') -> ['one', 'two', 'three']
*********************************
soundex
==============================
<b>soundex(<i>&lt;value1&gt;</i> : string) => string</b><br/><br/>
Gets the soundex code for the string
* soundex('genius') -> 'G520'
*********************************
levenshtein
==============================
<b>levenshtein(<i>&lt;from string&gt;</i> : string, <i>&lt;to string&gt;</i> : string) => integer</b><br/><br/>
Gets the levenshtein distance between two strings
* levenshtein('boys', 'girls') -> 4
*********************************
slice
==============================
<b>slice(<i>&lt;array to slice&gt;</i> : array, <i>&lt;from 1-based index&gt;</i> : integral, [<i>&lt;number of items&gt;</i> : integral]) => array</b><br/><br/>
Extracts a subset of an array from a position. Position is 1 based. If the length is omitted, it is defaulted to end of the string
* slice([10, 20, 30, 40], 1, 2) -> [10, 20]
* slice([10, 20, 30, 40], 2) -> [20, 30, 40]
* slice([10, 20, 30, 40], 8) -> []
*********************************
true
==============================
<b>true() => boolean</b><br/><br/>
Always returns a true value. Use the function syntax(true()) if there is an column name named 'true'
* isDiscounted == true()
* isDiscounted() == true
*********************************
false
==============================
<b>false() => boolean</b><br/><br/>
Always returns a false value. Use the function syntax(false()) if there is a column name named 'false'
* isDiscounted == false()
* isDiscounted() == false
*********************************
toBoolean
==============================
<b>toBoolean(<i>&lt;value1&gt;</i> : string) => boolean</b><br/><br/>
Converts a value of ('t', 'true', 'y', 'yes', '1') to true and ('f', 'false', 'n', 'no', '0') to false and NULL for any other value
* toBoolean('true') -> true
* toBoolean('n') -> false
* toBoolean('truthy') -> NULL
*********************************
add
==============================
<b>add(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => any</b><br/><br/>
Adds a pair of strings or numbers. Adds a date to a number of days. Appends one array of similar type to another. Same as the + operator
* add(10, 20) -> 30
* 10 + 20 -> 30
* add('ice', 'cream') -> 'icecream'
* 'ice' + 'cream' + ' cone' -> 'icecream cone'
* add(toDate('2012-12-12'), 3) -> 2012-12-15 (date value)
* toDate('2012-12-12') + 3 -> 2012-12-15 (date value)
* [10, 20] + [30, 40] => [10, 20, 30, 40]
*********************************
minus
==============================
<b>minus(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => any</b><br/><br/>
Substracts numbers. Substract from a date number of days. Same as the - operator
* minus(20, 10) -> 10
* 20 - 10 -> 10
* minus(toDate('2012-12-15'), 3) -> 2012-12-12 (date value)
* toDate('2012-12-15') - 3 -> 2012-12-13 (date value)
*********************************
multiply
==============================
<b>multiply(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => any</b><br/><br/>
Multiplies pair of numbers. Same as the * operator
* multiply(20, 10) -> 200
* 20 * 10 -> 200
*********************************
divide
==============================
<b>divide(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => any</b><br/><br/>
Divides pair of numbers. Same as the / operator
* divide(20, 10) -> 2
* 20 / 10 -> 2
*********************************
mod
==============================
<b>mod(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => any</b><br/><br/>
Modulus of pair of numbers. Same as the % operator
* mod(20, 8) -> 4
* 20 % 8 -> 4
*********************************
pMod
==============================
<b>pMod(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => any</b><br/><br/>
Positive Modulus of pair of numbers.
* pmod(-20, 8) -> 4
*********************************
abs
==============================
<b>abs(<i>&lt;value1&gt;</i> : number) => number</b><br/><br/>
Positive Modulus of pair of numbers.
* abs(-20) -> 20
* abs(10) -> 10
*********************************
and
==============================
<b>and(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : boolean) => boolean</b><br/><br/>
Logical AND operator. Same as &&
* and(true, false) -> false
* true && false -> false
*********************************
or
==============================
<b>or(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : boolean) => boolean</b><br/><br/>
Logical OR operator. Same as ||
* or(true, false) -> true
* true || false -> true
*********************************
xor
==============================
<b>xor(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : boolean) => boolean</b><br/><br/>
Logical XOR operator. Same as ^ operator
* xor(true, false) -> true
* xor(true, true) -> false
* true ^ false -> true
*********************************
not
==============================
<b>not(<i>&lt;value1&gt;</i> : boolean) => boolean</b><br/><br/>
Logical negation operator
* not(true) -> false
* not(premium)
*********************************
typeMatch
==============================
<b>typeMatch(<i>&lt;type&gt;</i> : string, <i>&lt;base type&gt;</i> : string) => boolean</b><br/><br/>
Matches the type of the column. Can only be used in pattern expressions.number matches short, integer, long, double, float or decimal, integral matches short, integer, long, fractional matches double, float, decimal and datetime matches date or timestamptype
* typeMatch(type, 'number') -> true
* typeMatch('date', 'number') -> false
*********************************
toShort
==============================
<b>toShort(<i>&lt;value&gt;</i> : any, [<i>&lt;format&gt;</i> : string]) => short</b><br/><br/>
Converts any numeric or string to a short value. An optional Java decimal format can be used for the conversion.Truncates any integer, long, float, double
* toShort(123) -> 123
* toShort('123') -> 123
* toShort('$123', '$###') -> 123
*********************************
toInteger
==============================
<b>toInteger(<i>&lt;value&gt;</i> : any, [<i>&lt;format&gt;</i> : string]) => integer</b><br/><br/>
Converts any numeric or string to a integer value. An optional Java decimal format can be used for the conversion.Truncates any long, float, double
* toInteger(123) -> 123
* toInteger('123') -> 123
* toInteger('$123', '$###') -> 123
*********************************
toLong
==============================
<b>toLong(<i>&lt;value&gt;</i> : any, [<i>&lt;format&gt;</i> : string]) => long</b><br/><br/>
Converts any numeric or string to a long value. An optional Java decimal format can be used for the conversion.Truncates any float, double
* toLong(123) -> 123
* toLong('123') -> 123
* toLong('$123', '$###') -> 123
*********************************
toFloat
==============================
<b>toFloat(<i>&lt;value&gt;</i> : any, [<i>&lt;format&gt;</i> : string]) => float</b><br/><br/>
Converts any numeric or string to a float value. An optional Java decimal format can be used for the conversion.Truncates any double
* toFloat(123.45) -> 123.45
* toFloat('123.45') -> 123.45
* toFloat('$123.45', '$###.00') -> 123.45
*********************************
toDouble
==============================
<b>toDouble(<i>&lt;value&gt;</i> : any, [<i>&lt;format&gt;</i> : string]) => double</b><br/><br/>
Converts any numeric or string to a double value. An optional Java decimal format can be used for the conversion.
* toDouble(123.45) -> 123.45
* toDouble('123.45') -> 123.45
* toDouble('$123.45', '$###.00') -> 123.45
*********************************
toDecimal
==============================
<b>toDecimal(<i>&lt;value&gt;</i> : any, [<i>&lt;format&gt;</i> : integral], [<i>&lt;value3&gt;</i> : integral], [<i>&lt;value4&gt;</i> : string]) => decimal(10,0)</b><br/><br/>
Converts any numeric or string to a decimal value. If precision and scale are not specified, it is defaulted to (10,2).An optional Java decimal format can be used for the conversion.
* toDecimal(123.45) -> 123.45
* toDecimal('123.45', 8, 4) -> 123.4500
* toDecimal('$123.45', 8, 4,'$###.00') -> 123.4500
*********************************
equals
==============================
<b>equals(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => boolean</b><br/><br/>
Comparison equals operator. Same as == operator
* equals(12, 24) -> false
* 12==24 -> false
* 'abc'=='abc' -> true
*********************************
notEquals
==============================
<b>notEquals(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => boolean</b><br/><br/>
Comparison not equals operator. Same as != operator
* 12!=24 -> true
* 'abc'!='abc' -> false
*********************************
greater
==============================
<b>greater(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => boolean</b><br/><br/>
Comparison greater operator. Same as > operator
* greater(12, 24) -> false
* 'abcd' > 'abc' -> true
*********************************
lesser
==============================
<b>lesser(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => boolean</b><br/><br/>
Comparison less operator. Same as < operator
* lesser(12 < 24) -> true
* 'abcd' < 'abc' -> false
*********************************
greaterOrEqual
==============================
<b>greaterOrEqual(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => boolean</b><br/><br/>
Comparison greater than or equal operator. Same as >= operator
* greaterOrEqual(12, 12) -> false
* 'abcd' >= 'abc' -> true
*********************************
lesserOrEqual
==============================
<b>lesserOrEqual(<i>&lt;value1&gt;</i> : any, <i>&lt;value2&gt;</i> : any) => boolean</b><br/><br/>
Comparison lesser than or equal operator. Same as <= operator
* lesserOrEqual(12, 12) -> true
* 'abcd' <= 'abc' -> false
*********************************
greatest
==============================
<b>greatest(<i>&lt;value1&gt;</i> : any, ...) => any</b><br/><br/>
Returns the greatest value among the list of values as input. Returns null if all inputs are null
* greatest(10, 30, 15, 20) -> 30
* greatest(toDate('12/12/2010'), toDate('12/12/2011'), toDate('12/12/2000')) -> '12/12/2011'
*********************************
least
==============================
<b>least(<i>&lt;value1&gt;</i> : any, ...) => any</b><br/><br/>
Comparison lesser than or equal operator. Same as <= operator
* least(10, 30, 15, 20) -> 10
* least(toDate('12/12/2010'), toDate('12/12/2011'), toDate('12/12/2000')) -> '12/12/2000'
*********************************
power
==============================
<b>power(<i>&lt;value1&gt;</i> : number, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Raises one number to the power of another
* power(10, 2) -> 100
*********************************
sqrt
==============================
<b>sqrt(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates the square root of a number
* sqrt(9) -> 3
*********************************
cbrt
==============================
<b>cbrt(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculate the cube root of a number
* cbrt(8) -> 2.0
*********************************
negate
==============================
<b>negate(<i>&lt;value1&gt;</i> : number) => number</b><br/><br/>
Negates a number. Turns positive numbers to negative and vice versa
* negate(13) -> -13
*********************************
cos
==============================
<b>cos(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a consine value
* cos(10) -> -0.83907152907
*********************************
acos
==============================
<b>acos(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a consine inverse value
* acos(1) -> 0.0
*********************************
cosh
==============================
<b>cosh(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a hyperbolic cosine of a value
* cosh(0) -> 1.0
*********************************
sin
==============================
<b>sin(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a sine value
* sin(2) -> 0.90929742682
*********************************
asin
==============================
<b>asin(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a inverse sine value
* asin(0) -> 0.0
*********************************
sinh
==============================
<b>sinh(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a hyperbolic sine value
* sinh(0) -> 0.0
*********************************
tan
==============================
<b>tan(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a tangent value
* tan(0) -> 0.0
*********************************
atan
==============================
<b>atan(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a inverse tangent value
* atan(0) -> 0.0
*********************************
tanh
==============================
<b>tanh(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates a hyperbolic tangent value
* tanh(0) -> 0.0
*********************************
atan2
==============================
<b>atan2(<i>&lt;value1&gt;</i> : number, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Returns the angle in radians between the positive x-axis of a plane and the point given by the coordinates
* atan2(0, 0) -> 0.0
*********************************
factorial
==============================
<b>factorial(<i>&lt;value1&gt;</i> : number) => long</b><br/><br/>
Calculate the factorial of a number
* factorial(5) -> 120
*********************************
floor
==============================
<b>floor(<i>&lt;value1&gt;</i> : number) => number</b><br/><br/>
Returns the largest integer not greater than the number
* floor(-0.1) -> -1
*********************************
ceil
==============================
<b>ceil(<i>&lt;value1&gt;</i> : number) => number</b><br/><br/>
Returns the smallest integer not smaller than the number
* ceil(-0.1) -> 0
*********************************
degrees
==============================
<b>degrees(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Converts radians to degrees
* degrees(3.141592653589793) -> 180
*********************************
log
==============================
<b>log(<i>&lt;value1&gt;</i> : number, [<i>&lt;value2&gt;</i> : number]) => double</b><br/><br/>
Calculates log value. An optional base can be supplied else a euler number if used
* log(100, 10) -> 2
*********************************
log10
==============================
<b>log10(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Calculates log value based on 10 base
* log10(100) -> 2
*********************************
round
==============================
<b>round(<i>&lt;number&gt;</i> : number, [<i>&lt;scale to round&gt;</i> : number], [<i>&lt;rounding option&gt;</i> : integral]) => double</b><br/><br/>
Rounds a number given a optional scale and a optional rounding mode. If the scale is omitted it is defaulted to 0.  If the mode is omitted it is defaulted to ROUND_HALF_UP(5). The values for rounding include
1 - ROUND_UP
2 - ROUND_DOWN
3 - ROUND_CEILING
4 - ROUND_FLOOR
5 - ROUND_HALF_UP
6 - ROUND_HALF_DOWN
7 - ROUND_HALF_EVEN
8 - ROUND_UNNECESSARY
* round(100.123) -> 100.0
* round(2.5, 0) -> 3.0
* round(5.3999999999999995, 2, 7) -> 5.40
*********************************
currentDate
==============================
<b>currentDate([<i>&lt;value1&gt;</i> : string]) => date</b><br/><br/>
Gets the current date when this job starts to run. You can pass a optional timezone in the form of 'GMT', 'PST', 'UTC', 'America/Cayman'. The local timezone is used as the default.
* currentDate() -> 12-12-2030
* currentDate('PST') -> 12-31-2050
*********************************
currentTimestamp
==============================
<b>currentTimestamp() => timestamp</b><br/><br/>
Gets the current timestamp when the job starts to run with local time zone
* currentTimestamp() -> 12-12-2030T12:12:12
*********************************
toDate
==============================
<b>toDate(<i>&lt;string&gt;</i> : any, [<i>&lt;date format&gt;</i> : string]) => date</b><br/><br/>
Converts a string to a date given a optional date format. If the date format is omitted, combinations of the following are accepted. [ yyyy, yyyy-[m]m, yyyy-[m]m-[d]d, yyyy-[m]m-[d]d, yyyy-[m]m-[d]d, yyyy-[m]m-[d]dT* ]
* toDate('2012-8-8') -> 2012-8-8
* toDate('12/12/2012', 'mm/dd/yyyy') -> 2012-12-12
*********************************
toTimestamp
==============================
<b>toTimestamp(<i>&lt;string&gt;</i> : any, [<i>&lt;timestamp format&gt;</i> : string], [<i>&lt;time zone&gt;</i> : string]) => timestamp</b><br/><br/>
Converts a string to a date given a optional timestamp format. If the timestamp is omitted the default pattern yyyy-[m]m-[d]d hh:mm:ss[.f...] is used
* toTimestamp('2016-12-31 00:12:00') -> 2012-8-8T00:12:00
* toTimestamp('2016/12/31T00:12:00', 'mm/dd/yyyyThh:mm:ss') -> 2012-12-12T00:12:00
*********************************
toUTC
==============================
<b>toUTC(<i>&lt;value1&gt;</i> : timestamp, [<i>&lt;value2&gt;</i> : string]) => timestamp</b><br/><br/>
Converts the timestamp to UTC. You can pass a optional timezone in the form of 'GMT', 'PST', 'UTC', 'America/Cayman'. It is defaulted to the current timezone
* toUTC(currentTimeStamp()) -> 12-12-2030T19:18:12
* toUTC(currentTimeStamp(), 'Asia/Seoul') -> 12-13-2030T11:18:12
*********************************
currentUTC
==============================
<b>currentUTC([<i>&lt;value1&gt;</i> : string]) => timestamp</b><br/><br/>
Gets the current the timestamp as UTC. You can pass a optional timezone in the form of 'GMT', 'PST', 'UTC', 'America/Cayman'. It is defaulted to the current timezone
* currentUTC() -> 12-12-2030T19:18:12
* currentUTC('Asia/Seoul') -> 12-13-2030T11:18:12
*********************************
month
==============================
<b>month(<i>&lt;value1&gt;</i> : datetime) => integer</b><br/><br/>
Gets the month value of a date or timestamp
* month(toDate('2012-8-8')) -> 8
*********************************
year
==============================
<b>year(<i>&lt;value1&gt;</i> : datetime) => integer</b><br/><br/>
Gets the year value of a date
* year(toDate('2012-8-8')) -> 2012
*********************************
hour
==============================
<b>hour(<i>&lt;value1&gt;</i> : timestamp, [<i>&lt;value2&gt;</i> : string]) => integer</b><br/><br/>
Gets the hour value of a timestamp. You can pass a optional timezone in the form of 'GMT', 'PST', 'UTC', 'America/Cayman'. The local timezone is used as the default.
* hour(toTimestamp('2009-07-30T12:58:59')) -> 12
* hour(toTimestamp('2009-07-30T12:58:59'), 'PST') -> 12
*********************************
minute
==============================
<b>minute(<i>&lt;value1&gt;</i> : timestamp, [<i>&lt;value2&gt;</i> : string]) => integer</b><br/><br/>
Gets the minute value of a timestamp. You can pass a optional timezone in the form of 'GMT', 'PST', 'UTC', 'America/Cayman'. The local timezone is used as the default.
* minute(toTimestamp('2009-07-30T12:58:59')) -> 58
* minute(toTimestamp('2009-07-30T12:58:59', 'PST')) -> 58
*********************************
second
==============================
<b>second(<i>&lt;value1&gt;</i> : timestamp, [<i>&lt;value2&gt;</i> : string]) => integer</b><br/><br/>
Gets the second value of a date. You can pass a optional timezone in the form of 'GMT', 'PST', 'UTC', 'America/Cayman'. The local timezone is used as the default.
* second(toTimestamp('2009-07-30T12:58:59')) -> 59
*********************************
dayOfMonth
==============================
<b>dayOfMonth(<i>&lt;value1&gt;</i> : datetime) => integer</b><br/><br/>
Gets the day of the month given a date
* dayOfMonth(toDate('2018-06-08')) -> 08
*********************************
dayOfWeek
==============================
<b>dayOfWeek(<i>&lt;value1&gt;</i> : datetime) => integer</b><br/><br/>
Gets the day of the week given a date. 1 - Sunday, 2 - Monday ..., 7 - Saturday
* dayOfWeek(toDate('2018-06-08')) -> 7
*********************************
dayOfYear
==============================
<b>dayOfYear(<i>&lt;value1&gt;</i> : datetime) => integer</b><br/><br/>
Gets the day of the year given a date
* dayOfYear(toDate('2016-04-09')) -> 100
*********************************
weekOfYear
==============================
<b>weekOfYear(<i>&lt;value1&gt;</i> : datetime) => integer</b><br/><br/>
Gets the week of the year given a date
* weekOfYear(toDate('2008-02-20')) -> 8
*********************************
lastDayOfMonth
==============================
<b>lastDayOfMonth(<i>&lt;value1&gt;</i> : datetime) => date</b><br/><br/>
Gets the last date of the month given a date
* lastDayOfMonth(toDate('2009-01-12')) -> 2009-01-31
*********************************
monthsBetween
==============================
<b>monthsBetween(<i>&lt;from date/timestamp&gt;</i> : datetime, <i>&lt;to date/timestamp&gt;</i> : datetime, [<i>&lt;time zone&gt;</i> : string]) => double</b><br/><br/>
Gets the number of months between two datesYou can pass a optional timezone in the form of 'GMT', 'PST', 'UTC', 'America/Cayman'. The local timezone is used as the default.
* monthsBetween(toDate('1997-02-28 10:30:00'), toDate('1996-10-30')) -> 3.94959677
*********************************
addMonths
==============================
<b>addMonths(<i>&lt;date/timestamp&gt;</i> : datetime, <i>&lt;months to add&gt;</i> : integral) => datetime</b><br/><br/>
Add months to a date or timestamp
* addMonths(toDate('2016-08-31'), 1) -> 2016-09-30
* addMonths(toTimestamp('2016-09-30 10:10:10'), -1) -> 2016-08-31 10:10:10
*********************************
addDays
==============================
<b>addDays(<i>&lt;date/timestamp&gt;</i> : datetime, <i>&lt;days to add&gt;</i> : integral) => datetime</b><br/><br/>
Add days to a date or timestamp. Same as the + operator for date
* addDays(toDate('2016-08-08'), 1) -> 2016-08-09
*********************************
subDays
==============================
<b>subDays(<i>&lt;date/timestamp&gt;</i> : datetime, <i>&lt;days to subtract&gt;</i> : integral) => datetime</b><br/><br/>
Subtract months from a date. Same as the - operator for date
* subDays(toDate('2016-08-08'), 1) -> 2016-08-09
*********************************
subMonths
==============================
<b>subMonths(<i>&lt;date/timestamp&gt;</i> : datetime, <i>&lt;months to substract&gt;</i> : integral) => datetime</b><br/><br/>
Subtract months from a date or timestamp
* subMonths(toDate('2016-09-30'), 1) -> 2016-08-31
*********************************
nextSequence
==============================
<b>nextSequence() => long</b><br/><br/>
Returns the next unique sequence. The number is consecutive only within a partition and is prefixed by the partitionId
* nextSequence() -> 12313112
*********************************
md5
==============================
<b>md5(<i>&lt;value1&gt;</i> : any, ...) => string</b><br/><br/>
Calculates the MD5 digest of set of column of varying primitive datatypes and returns a 32 character hex string. It can be used to calculate a fingerprint for a row
* md5(5, 'gunchus', 8.2, 'bojjus', true, toDate('2010-4-4')) -> 'c1527622a922c83665e49835e46350fe'
*********************************
sha1
==============================
<b>sha1(<i>&lt;value1&gt;</i> : any, ...) => string</b><br/><br/>
Calculates the SHA-1 digest of set of column of varying primitive datatypes and returns a 40 character hex string. It can be used to calculate a fingerprint for a row
* sha1(5, 'gunchus', 8.2, 'bojjus', true, toDate('2010-4-4')) -> '63849fd2abb65fbc626c60b1f827bd05573f0cea'
*********************************
sha2
==============================
<b>sha2(<i>&lt;value1&gt;</i> : integer, <i>&lt;value2&gt;</i> : any, ...) => string</b><br/><br/>
Calculates the SHA-2 digest of set of column of varying primitive datatypes given a bit length which can only be of values 0(256), 224, 256, 384, 512. It can be used to calculate a fingerprint for a row
* sha2(256, 'gunchus', 8.2, 'bojjus', true, toDate('2010-4-4')) -> 'd3b2bff62c3a00e9370b1ac85e428e661a7df73959fa1a96ae136599e9ee20fd'
*********************************
crc32
==============================
<b>crc32(<i>&lt;value1&gt;</i> : any, ...) => long</b><br/><br/>
Calculates the CRC32 hash of set of column of varying primitive datatypes given a bit length which can only be of values 0(256), 224, 256, 384, 512. It can be used to calculate a fingerprint for a row
* crc32(256, 'gunchus', 8.2, 'bojjus', true, toDate('2010-4-4')) -> 3630253689
*********************************
isInsert
==============================
<b>isInsert([<i>&lt;value1&gt;</i> : integer]) => boolean</b><br/><br/>
Checks if the row is marked for insert. For transformations taking more than one input stream you can pass the (1-based) index of the stream. Default value for the stream index is 1
* isInsert() -> true
* isInsert(1) -> false
*********************************
isUpdate
==============================
<b>isUpdate([<i>&lt;value1&gt;</i> : integer]) => boolean</b><br/><br/>
Checks if the row is marked for update. For transformations taking more than one input stream you can pass the (1-based) index of the stream. Default value for the stream index is 1
* isUpdate() -> true
* isUpdate(1) -> false
*********************************
isDelete
==============================
<b>isDelete([<i>&lt;value1&gt;</i> : integer]) => boolean</b><br/><br/>
Checks if the row is marked for delete. For transformations taking more than one input stream you can pass the (1-based) index of the stream. Default value for the stream index is 1
* isDelete() -> true
* isDelete(1) -> false
*********************************
isMatch
==============================
<b>isMatch([<i>&lt;value1&gt;</i> : integer]) => boolean</b><br/><br/>
Checks if the row is matched at lookup. For transformations taking more than one input stream you can pass the (1-based) index of the stream. Default value for the stream index is 1
* isMatch() -> true
* isMatch(1) -> false
*********************************
isError
==============================
<b>isError([<i>&lt;value1&gt;</i> : integer]) => boolean</b><br/><br/>
Checks if the row is marked as error. For transformations taking more than one input stream you can pass the (1-based) index of the stream. Default value for the stream index is 1
* isError() -> true
* isError(1) -> false
*********************************
isIgnore
==============================
<b>isIgnore([<i>&lt;value1&gt;</i> : integer]) => boolean</b><br/><br/>
Checks if the row is marked to be ignored. For transformations taking more than one input stream you can pass the (1-based) index of the stream. Default value for the stream index is 1
* isIgnore() -> true
* isIgnore(1) -> false
*********************************
sum
==============================
<b>sum(<i>&lt;value1&gt;</i> : number) => number</b><br/><br/>
Gets the aggregate sum of a numeric column
* sum(col) -> value
*********************************
sumIf
==============================
<b>sumIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => number</b><br/><br/>
Based on criteria gets the aggregate sum of a numeric column. The condition can be based on any column
* sumIf(state == 'CA' && commission < 10000, sales) -> value
* sumIf(true, sales) -> SUM(sales)
*********************************
sumDistinct
==============================
<b>sumDistinct(<i>&lt;value1&gt;</i> : number) => number</b><br/><br/>
Gets the aggregate sum of distinct values of a numeric column
* sumDistinct(col) -> value
*********************************
sumDistinctIf
==============================
<b>sumDistinctIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => number</b><br/><br/>
Based on criteria gets the aggregate sum of a numeric column. The condition can be based on any column
* sumDistinctIf(state == 'CA' && commission < 10000, sales) -> value
* sumDistinctIf(true, sales) -> SUM(sales)
*********************************
count
==============================
<b>count([<i>&lt;value1&gt;</i> : any]) => long</b><br/><br/>
Gets the aggregate count of values. If the optional column(s) is specified, it ignores NULL values in the count
* count(custId) -> 100
* count(custId, custName) -> 50
* count() -> 125
* count(iif(isNull(custId), 1, NULL)) -> 5
*********************************
countIf
==============================
<b>countIf(<i>&lt;value1&gt;</i> : boolean, [<i>&lt;value2&gt;</i> : any]) => long</b><br/><br/>
Based on a criteria gets the aggregate count of values. If the optional column is specified, it ignores NULL values in the count
* countIf(state == 'CA' && commission < 10000, name) -> 100
*********************************
countDistinct
==============================
<b>countDistinct(<i>&lt;value1&gt;</i> : any, [<i>&lt;value2&gt;</i> : any], ...) => long</b><br/><br/>
Gets the aggregate count of distinct values of a set of columns
* countDistinct(custId, custName) -> 60
*********************************
avg
==============================
<b>avg(<i>&lt;value1&gt;</i> : number) => number</b><br/><br/>
Gets the average of values of a column
* avg(sales) -> 7523420.234
*********************************
avgIf
==============================
<b>avgIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => number</b><br/><br/>
Based on a criteria gets the average of values of a column
* avgIf(region == 'West', sales) -> 7523420.234
*********************************
mean
==============================
<b>mean(<i>&lt;value1&gt;</i> : number) => number</b><br/><br/>
Gets the mean of values of a column. Same as AVG
* mean(sales) -> 7523420.234
*********************************
meanIf
==============================
<b>meanIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => number</b><br/><br/>
Based on a criteria gets the mean of values of a column. Same as avgIf
* meanIf(region == 'West', sales) -> 7523420.234
*********************************
min
==============================
<b>min(<i>&lt;value1&gt;</i> : any) => any</b><br/><br/>
Gets the minimum value of a column
* min(sales) -> 00.01
* min(orderDate) -> 12/12/2000
*********************************
minIf
==============================
<b>minIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : any) => any</b><br/><br/>
Based on a criteria, gets the minimum value of a column
* minIf(region == 'West', sales) -> 00.01
*********************************
max
==============================
<b>max(<i>&lt;value1&gt;</i> : any) => any</b><br/><br/>
Gets the maximum value of a column
* MAX(sales) -> 12312131.12
*********************************
maxIf
==============================
<b>maxIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : any) => any</b><br/><br/>
Based on a criteria, gets the maximum value of a column
* maxIf(region == 'West', sales) -> 99999.56
*********************************
stddev
==============================
<b>stddev(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Gets the standard deviation of a column
* stdDev(sales) -> 122.12
*********************************
stddevIf
==============================
<b>stddevIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the standard deviation of a column
* stddevIf(region == 'West', sales) -> 122.12
*********************************
stddevPopulation
==============================
<b>stddevPopulation(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Gets the population standard deviation of a column
* stddevPopulation(sales) -> 122.12
*********************************
stddevPopulationIf
==============================
<b>stddevPopulationIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the population standard deviation of a column
* stddevPopulationIf(region == 'West', sales) -> 122.12
*********************************
stddevSample
==============================
<b>stddevSample(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Gets the sample standard deviation of a column
* stddevSample(sales) -> 122.12
*********************************
stddevSampleIf
==============================
<b>stddevSampleIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the sample standard deviation of a column
* stddevSampleIf(region == 'West', sales) -> 122.12
*********************************
variance
==============================
<b>variance(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Gets the variance of a column
* variance(sales) -> 122.12
*********************************
varianceIf
==============================
<b>varianceIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the variance of a column
* varianceIf(region == 'West', sales) -> 122.12
*********************************
variancePopulation
==============================
<b>variancePopulation(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Gets the population variance of a column
* variancePopulation(sales) -> 122.12
*********************************
variancePopulationIf
==============================
<b>variancePopulationIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the population variance of a column
* variancePopulationIf(region == 'West', sales) -> 122.12
*********************************
varianceSample
==============================
<b>varianceSample(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Gets the unbiased variance of a column
* varianceSample(sales) -> 122.12
*********************************
varianceSampleIf
==============================
<b>varianceSampleIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the unbiased variance of a column
* varianceSampleIf(region == 'West', sales) -> 122.12
*********************************
covariancePopulation
==============================
<b>covariancePopulation(<i>&lt;value1&gt;</i> : number, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Gets the population covariance of a column
* covariancePopulation(sales) -> 122.12
*********************************
covariancePopulationIf
==============================
<b>covariancePopulationIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the population covariance of a column
* covariancePopulationIf(region == 'West', sales) -> 122.12
*********************************
covarianceSample
==============================
<b>covarianceSample(<i>&lt;value1&gt;</i> : number, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Gets the sample covariance of a column
* covarianceSample(sales) -> 122.12
*********************************
covarianceSampleIf
==============================
<b>covarianceSampleIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the sample covariance of a column
* covarianceSampleIf(region == 'West', sales) -> 122.12
*********************************
kurtosis
==============================
<b>kurtosis(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Gets the kurtosis of a column
* kurtosis(sales) -> 122.12
*********************************
kurtosisIf
==============================
<b>kurtosisIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the kurtosis of a column
* kurtosisIf(region == 'West', sales) -> 122.12
*********************************
skewness
==============================
<b>skewness(<i>&lt;value1&gt;</i> : number) => double</b><br/><br/>
Gets the skewness of a column
* skewness(sales) -> 122.12
*********************************
skewnessIf
==============================
<b>skewnessIf(<i>&lt;value1&gt;</i> : boolean, <i>&lt;value2&gt;</i> : number) => double</b><br/><br/>
Based on a critera, gets the skewness of a column
* skewnessIf(region == 'West', sales) -> 122.12
*********************************
first
==============================
<b>first(<i>&lt;value1&gt;</i> : any, [<i>&lt;value2&gt;</i> : boolean]) => any</b><br/><br/>
Gets the first value of a column group. If the second parameter ignoreNulls is omitted, it is assumed false
* first(sales) -> 12233.23
* first(sales, false) -> NULL
*********************************
last
==============================
<b>last(<i>&lt;value1&gt;</i> : any, [<i>&lt;value2&gt;</i> : boolean]) => any</b><br/><br/>
Gets the last value of a column group. If the second parameter ignoreNulls is omitted, it is assumed false
* last(sales) -> 523.12
* last(sales, false) -> NULL
*********************************
lag
==============================
<b>lag(<i>&lt;value&gt;</i> : any, [<i>&lt;number of rows to look before&gt;</i> : number], [<i>&lt;default value&gt;</i> : any]) => any</b><br/><br/>
Gets the value of the first parameter evaluated n rows before the current row. The second parameter is the number of rows to look backand the default value is 1. If there are not as many rows a value of null is returned unless a default value is specified
* lag(amount, 2) -> 60
* lag(amount, 2000, 100) -> 100
*********************************
lead
==============================
<b>lead(<i>&lt;value&gt;</i> : any, [<i>&lt;number of rows to look after&gt;</i> : number], [<i>&lt;default value&gt;</i> : any]) => any</b><br/><br/>
Gets the value of the first parameter evaluated n rows after the current row. The second parameter is the number of rows to look forwardand the default value is 1. If there are not as many rows a value of null is returned unless a default value is specified
* lead(amount, 2) -> 60
* lead(amount, 2000, 100) -> 100
*********************************
cumeDist
==============================
<b>cumeDist() => integer</b><br/><br/>
The CumeDist function computes the position of a value relative to all values in the partition.The result is the number of rows preceding or equal to the current row in the ordering of the partition divided by the total number of rows in the window partition. Any tie values in the  ordering will evaluate to the same position.
* cumeDist() -> 1
*********************************
nTile
==============================
<b>nTile() => integer</b><br/><br/>
The NTile function divides the rows for each window partition into `n` buckets ranging from 1 to at most `n`. Bucket values will differ by at most 1. If the number of rows in the partition does not divide evenly into the number of buckets, then the remainder values are distributed one per bucket, starting with the first bucket. The NTile function is particularly useful for the calculation of tertiles, quartiles, deciles and other common summary statistics The function calculates two variables during initialization: The size of a regular bucket, and the number of buckets that will have one extra row added to it (when the rows do not evenly fit into the number of buckets); both variables are based on the size of the current partition. During the calculation process the function keeps track of the current row number, the current bucket number, and the row number at which the bucket will change (bucketThreshold). When the current row number reaches bucket threshold, the bucket value is increased by one and the threshold is increased by the bucket size (plus one extra if the current bucket is padded).
* cumeDist() -> 1
*********************************
rank
==============================
<b>rank(<i>&lt;value1&gt;</i> : any, ...) => integer</b><br/><br/>
Computes the rank of a value in a group of values. The result is one plus the number of rows preceding or equal to the current row in the ordering of the partition. The values will produce gaps in the sequence. Rank works even when data is not sorted and looks for change in values
* rank(salesQtr, salesAmt) -> 1
*********************************
denseRank
==============================
<b>denseRank(<i>&lt;value1&gt;</i> : any, ...) => integer</b><br/><br/>
Computes the rank of a value in a group of values. The result is one plus the number of rows preceding or equal to the current row in the ordering of the partition. The values will not produce gaps in the sequence. Dense Rank works even when data is not sorted and looks for change in values
* denseRank(salesQtr, salesAmt) -> 1
