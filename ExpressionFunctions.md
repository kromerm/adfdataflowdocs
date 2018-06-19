[Pop-out for expression functions](https://adfdataflowexecutor.azurewebsites.net)


******************************************************
Function: isnull(<value1> : any) => boolean
Description: Checks if the value is NULL
Examples:
1. IS_NULL(NULL()) -> true
2. IS_NULL('') -> false'
******************************************************
Function: null() => null
Description: Returns a NULL value. Use the function syntax(null()) if there is a column name named 'null'. Any operation that uses will result in a NULL
Examples:
1. custId = NULL (for derived field)
2. custId == NULL -> NULL
3. 'nothing' + NULL -> NULL
4. 10 * NULL -> NULL'
5. NULL == '' -> NULL'
******************************************************
Function: iif(<condition> : boolean, <true_expression> : any, [<false_expression> : any]) => any
Description: Based on a condition applies one value or the other. If other is unspecified it is considered NULL. Both the values must be compatible(numeric, string...)
Examples:
1. IIF(custType == 'Premium', 10, 4.5)
2. IIF(amount > 100, 'High')
3. IIF(DAY_OF_WEEK(saleDate) == 6, 'Weekend', 'Weekday')
******************************************************
Function: case(<condition> : boolean, <true_expression> : any, <false_expression> : any, ...) => any
Description: Based on alternating conditions applies one value or the other. If the number of inputs are even, the other is NULL for last condition
Examples:
1. CASE(custType == 'Premium', 10, 4.5)
2. CASE(custType == 'Premium', price*0.95, custType == 'Elite',   price*0.9, price*2)
3. CASE(DAY_OF_WEEK(saleDate) == 1, 'Sunday', DAY_OF_WEEK(saleDate) == 6, 'Saturday')
******************************************************
Function: concat(<this> : string, <that> : string, ...) => string
Description: Concatenates a variable number of strings together. Same as the + operator with strings
Examples:
1. CONCAT('Awesome', 'Cool', 'Product') -> 'AwesomeCoolProduct'
2. 'Awesome' + 'Cool' + 'Product' -> 'AwesomeCoolProduct'
3. CONCAT(addrLine1, ' ', addrLine2, ' ', city, ' ', state, ' ', zip)
4. addrLine1 + ' ' + addrLine2 + ' ' + city + ' ' + state + ' ' + zip
******************************************************
Function: concat_ws(<separator> : string, <this> : string, <that> : string, ...) => string
Description: Concatenates a variable number of strings together with a separator. The first parameter is the separator
Examples:
1. CONCAT_WS(' ', 'Awesome', 'Cool', 'Product') -> 'Awesome Cool Product'
2. CONCAT_WS(' ' , addrLine1, addrLine2, city, state, zip) -> 
3. CONCAT_WS(',' , TO_STRING(order_total), TO_STRING(order_discount))
******************************************************
Function: trim(<string to trim> : string, [<trim characters> : string]) => string
Description: Trims a string of leading and trailing characters. If second parameter is unspecified, it trims whitespace. Else it trims any character specified in the second parameter
Examples:
1. TRIM('!--!wor!ld!, '-!') -> 'wor!ld'
2. TRIM(addressLine)
******************************************************
Function: ltrim(<string to trim> : string, <trim characters> : string) => string
Description: Left trims a string of leading characters. If second parameter is unspecified, it trims whitespace. Else it trims any character specified in the second parameter
Examples:
1. LTRIM('!--!wor!ld!, '-!') -> 'wor!ld!'
2. LTRIM(addressLine)
******************************************************
Function: rtrim(<string to trim> : string, <trim characters> : string) => string
Description: Right trims a string of leading characters. If second parameter is unspecified, it trims whitespace. Else it trims any character specified in the second parameter
Examples:
1. RTRIM('!--!wor!ld!, '-!') -> '!--!wor!ld'
2. RTRIM(addressLine)
******************************************************
Function: substring(<string to subset> : string, <from 1-based index> : integral, [<number of characters> : integral]) => string
Description: Extracts a substring of a certain length from a position. Position is 1 based. If the length is omitted, it is defaulted to end of the string
Examples:
1. SUBSTRING('Cat in the hat', 5, 2) -> 'in'
2. SUBSTRING('Cat in the hat', 5, 100) -> 'in the hat'
3. SUBSTRING('Cat in the hat', 5) -> 'in the hat'
4. SUBSTRING('Cat in the hat', 100, 100) -> ''
******************************************************
Function: lower(<value1> : string) => string
Description: Lowercases a string
Examples:
1. LOWER('HELLO') -> 'hello'
2. LOWER(name)
******************************************************
Function: upper(<value1> : string) => string
Description: Uppercases a string
Examples:
1. UPPER('Hello') -> 'HELLO'
2. UPPER(name)
******************************************************
Function: length(<value1> : string) => integer
Description: Returns the length of the string
Examples:
1. LENGTH('kiddo') -> 5
******************************************************
Function: rpad(<string to pad> : string, <final padded length> : integral, <padding> : string) => string
Description: Right pads the string by the supplied padding until it is of a certain length. If the string is equal or greater than the length it is a no-op
Examples:
1. RPAD('great', 10, '-') -> 'great-----'
2. RPAD('great', 4, '-') -> 'great'
3. RPAD('great', 8, '<>') -> 'great<><'
******************************************************
Function: lpad(<string to pad> : string, <final padded length> : integral, <padding> : string) => string
Description: Left pads the string by the supplied padding until it is of a certain length. If the string is equal or greater than the length it is a no-op
Examples:
1. LPAD('great', 10, '-') -> '-----great'
2. LPAD('great', 4, '-') -> 'great'
3. LPAD('great', 8, '<>') -> '<><great'
******************************************************
Function: left(<string to subset> : string, <number of characters> : integral) => string
Description: Extracts a substring start at index 1 with number of characters. Same as SUBSTRING(str, 1, n)
Examples:
1. LEFT('bojjus', 2) -> 'bo'
2. LEFT('bojjus', 20) -> 'bojjus'
******************************************************
Function: right(<string to subset> : string, <number of characters> : integral) => string
Description: Extracts a substring with number of characters from the right. Same as SUBSTRING(str, LENGTH(str) - n, n)
Examples:
1. RIGHT('bojjus', 2) -> 'us'
2. RIGHT('bojjus', 20) -> 'bojjus'
******************************************************
Function: startsWith(<string> : string, <substring to check> : string) => boolean
Description: Checks if the string starts with the supplied string
Examples:
1. STARTS_WITH('great', 'gr') -> true
******************************************************
Function: endsWith(<string> : string, <substring to check> : string) => boolean
Description: Checks if the string ends with the supplied string
Examples:
1. ENDS_WITH('great', 'eat') -> true
******************************************************
Function: locate(<substring to find> : string, <string> : string, [<from index - 1-based> : integral]) => integer
Description: Finds the position(1 based) of the substring within a string starting a certain position. If the position is omitted it is considered from the beginning of the string. 0 is returned if not found
Examples:
1. LOCATE('eat', 'great') -> 3
2. LOCATE('o', 'microsoft', 6) -> 7
3. LOCATE('bad', 'good') -> 0
******************************************************
Function: instr(<string> : string, <substring to find> : string) => integer
Description: Finds the position(1 based) of the substring within a string. 0 is returned if not found
Examples:
1. INSTR('great', 'eat') -> 3
2. INSTR('microsoft', 'o') -> 7
3. INSTR('good', 'bad') -> 0
******************************************************
Function: translate(<string to translate> : string, <lookup characters> : string, <replace characters> : string) => string
Description: Replace one set of characters by another set of characters in the string. Characters have  1 to 1 replacement
Examples:
1. TRANSLATE('(Hello)', '()', '[]') -> '[Hello]'
2. TRANSLATE('(Hello)', '()', '[') -> '[Hello)'
******************************************************
Function: reverse(<value1> : string) => string
Description: Reverses a string
Examples:
1. REVERSE('gunchus') -> 'suhcnug'
******************************************************
Function: replace(<string> : string, <substring to find> : string, <substring to replace> : string) => string
Description: Replace all occurences of a substring with another substring in the given string
Examples:
1. REPLACE('doggie dog', 'dog', 'cat') -> 'catgie cat'
2. REPLACE('doggie dog', 'dog', '') -> 'gie'
******************************************************
Function: regex_replace(<string> : string, <regex to find> : string, <substring to replace> : string) => string
Description: Replace all occurences of a regex pattern with another substring in the given string
Examples:
1. REGEX_REPLACE('100 and 200', '(\d+)', 'digits') -> 'digits and digits'
******************************************************
Function: regex_extract(<string> : string, <regex to find> : string, [<match group 1-based index> : integral]) => string
Description: Extract a matching substring for a given regex pattern. The last parameter identifies the match group and is defaulted to 1 if omitted
Examples:
1. REGEX_EXTRACT('Cost is between 600 and 800 dollars', '(\d+) and (\d+)', 2) -> '800'
******************************************************
Function: regex_match(<string> : string, <regex to match> : string) => boolean
Description: Checks if the string matches the given regex pattern
Examples:
1. REGEX_MATCH('200.50', '(\d+).(\d+)') -> true
******************************************************
Function: like(<string> : string, <pattern match> : string) => boolean
Description: The pattern is a string which is matched literally, with exception to the following special symbols:_ matches any one character in the input (similar to . in posix regular expressions) 
% matches zero or more characters in the input (similar to .* in posix regular expressions).The escape character is ''. If an escape character precedes a special symbol or another escape character, the following character is matched literally. It is invalid to escape any other character.
Examples:
1. LIKE('icecream', 'ice%') -> true
******************************************************
Function: rlike(<string> : string, <pattern match> : string) => boolean
Description: Checks if the string matches the given regex pattern
Examples:
1. RLIKE('200.50', '(\d+).(\d+)') -> true
******************************************************
Function: in(<array of items> : array, <item to find> : any) => boolean
Description: Checks if an item is in the array
Examples:
1. IN([10, 20, 30], 10) -> true
2. IN(['good', 'kid'], 'bad') -> false
******************************************************
Function: to_string(<value> : any, [<number format/date format> : string]) => string
Description: Converts a primitive datatype to a string. For numbers and date a format can be specified. If unspecified the system default is picked.Java decimal format is used for numbers. Default date format is yyyy-mm-dd
Examples:
1. TO_STRING(10) -> '10'
2. TO_STRING('engineer') -> 'engineer'
3. TO_STRING(123456.789, '##,###.##') -> '123,456.79'
4. TO_STRING(123.78, '000000.000') -> '000123.780'
5. TO_STRING(12345, '##0.#####E0') -> '12.345E3'
6. TO_STRING(TO_DATE('2018-12-31')) -> '2018-12-31'
7. TO_STRING(TO_DATE('2018-12-31'), 'mm/dd/yy') -> '12/31/18'
8. TO_STRING(4 == 20) -> 'false'
******************************************************
Function: split(<string to split> : string, <split characters> : string) => array
Description: Splits a string based on a delimiter and returns an array of strings
Examples:
1. SPLIT('100,200,300', ',') -> ['100', '200', '300']
2. SPLIT('100,200,300', '|') -> ['100,200,300']
3. SPLIT('100, 200, 300', ', ') -> ['100', '200', '300']
4. SPLIT('100200300', ',') -> ['100200300']
******************************************************
Function: regex_split(<string to split> : string, <regex expression> : string) => array
Description: Splits a string based on a delimiter based on regex and returns an array of strings
Examples:
1. REGEX_SPLIT('oneAtwoBthreeC', '[CAB]') -> ['one', 'two', 'three']
******************************************************
Function: soundex(<value1> : string) => string
Description: Gets the soundex code for the string
Examples:
1. SOUNDEX('genius') -> 'G520'
******************************************************
Function: levenshtein(<from string> : string, <to string> : string) => integer
Description: Gets the levenshtein distance between two strings
Examples:
1. LEVENSHTEIN('boys', 'girls') -> 4
******************************************************
Function: to_boolean(<value1> : string) => boolean
Description: Converts a value of ('t', 'true', 'y', 'yes', '1') to true and ('f', 'false', 'n', 'no', '0') to false and NULL for any other value
Examples:
1. TO_BOOLEAN('true') -> true
2. TO_BOOLEAN('n') -> false
3. TO_BOOLEAN('truthy') -> NULL
******************************************************
Function: add(<value1> : any, <value2> : any) => any
Description: Adds a pair of strings or numbers. Adds a date to a number of days. Same as the + operator
Examples:
1. ADD(10, 20) -> 30
2. 10 + 20 -> 30
3. ADD('ice', 'cream') -> 'icecream'
4. 'ice' + 'cream' + ' cone' -> 'icecream cone'
5. ADD(TO_DATE('2012-12-12'), 3) -> 2012-12-15 (date value)
6. TO_DATE('2012-12-12') + 3 -> 2012-12-15 (date value)
******************************************************
Function: minus(<value1> : any, <value2> : any) => any
Description: Substracts numbers. Substract from a date number of days. Same as the - operator
Examples:
1. MINUS(20, 10) -> 10
2. 20 - 10 -> 10
3. ADD('ice', 'cream') -> 'icecream'
4. MINUS(TO_DATE('2012-12-15'), 3) -> 2012-12-12 (date value)
5. TO_DATE('2012-12-15') - 3 -> 2012-12-13 (date value)
******************************************************
Function: multiply(<value1> : any, <value2> : any) => any
Description: Multiplies pair of numbers. Same as the * operator
Examples:
1. MULTIPLY(20, 10) -> 200
2. 20 * 10 -> 200
******************************************************
Function: divide(<value1> : any, <value2> : any) => any
Description: Divides pair of numbers. Same as the / operator
Examples:
1. DIVIDE(20, 10) -> 2
2. 20 / 10 -> 2
******************************************************
Function: mod(<value1> : any, <value2> : any) => any
Description: Modulus of pair of numbers. Same as the % operator
Examples:
1. MOD(20, 8) -> 4
2. 20 % 8 -> 4
******************************************************
Function: and(<value1> : boolean, <value2> : boolean) => boolean
Description: Logical AND operator. Same as &&
Examples:
1. AND(true, false) -> false
2. true && false -> false
******************************************************
Function: or(<value1> : boolean, <value2> : boolean) => boolean
Description: Logical OR operator. Same as ||
Examples:
1. OR(true, false) -> true
2. true || false -> true
******************************************************
Function: xor(<value1> : boolean, <value2> : boolean) => boolean
Description: Logical XOR operator. Same as ^ operator
Examples:
1. XOR(true, false) -> true
2. XOR(true, true) -> false
3. true ^ false -> true
******************************************************
Function: not(<value1> : boolean) => boolean
Description: Logical negation operator
Examples:
1. NOT(true) -> false
2. NOT(premium)
******************************************************
Function: to_short(<value1> : any) => short
Description: Converts any numeric or string to a short value. Truncates any integer, long, float, double
Examples:
1. TO_SHORT(123) -> 123
2. TO_SHORT('123') -> 123
******************************************************
Function: to_integer(<value1> : any) => integer
Description: Converts any numeric or string to a integer value. Truncates any long, float, double
Examples:
1. TO_INTEGER(123) -> 123
2. TO_INTEGER('123') -> 123
******************************************************
Function: to_long(<value1> : any) => long
Description: Converts any numeric or string to a integer value. Truncates any long, float, double
Examples:
1. TO_LONG(123) -> 123
2. TO_LONG('123') -> 123L
******************************************************
Function: to_float(<value1> : any) => float
Description: Converts any numeric or string to a float value. Truncates any double
Examples:
1. TO_FLOAT(123.45) -> 123.45
2. TO_FLOAT('123.45') -> 123.45
******************************************************
Function: to_double(<value1> : any) => double
Description: Converts any numeric or string to a double value
Examples:
1. TO_DOUBLE(123.45) -> 123.45
2. TO_DOUBLE('123.45') -> 123.45
******************************************************
Function: equals(<value1> : any, <value2> : any) => boolean
Description: Comparison equals operator. Same as == operator
Examples:
1. 12==24 -> false
2. 'abc'=='abc' -> true
******************************************************
Function: notEquals(<value1> : any, <value2> : any) => boolean
Description: Comparison not equals operator. Same as != operator
Examples:
1. 12!=24 -> true
2. 'abc'!='abc' -> false
******************************************************
Function: greater(<value1> : any, <value2> : any) => boolean
Description: Comparison greater operator. Same as > operator
Examples:
1. 12 > 24 -> false
2. 'abcd' > 'abc' -> true
******************************************************
Function: lesser(<value1> : any, <value2> : any) => boolean
Description: Comparison less operator. Same as < operator
Examples:
1. 12 < 24 -> true
2. 'abcd' < 'abc' -> false
******************************************************
Function: greater_equal(<value1> : any, <value2> : any) => boolean
Description: Comparison greater than or equal operator. Same as >= operator
Examples:
1. 12 >= 12 -> false
2. 'abcd' >= 'abc' -> true
******************************************************
Function: lesser_equal(<value1> : any, <value2> : any) => boolean
Description: Comparison lesser than or equal operator. Same as <= operator
Examples:
1. 12 <= 12 -> true
2. 'abcd' <= 'abc' -> false
******************************************************
Function: power(<value1> : number, <value2> : number) => double
Description: Raises one number to the power of another
Examples:
1. POWER(10, 2) -> 100
******************************************************
Function: sqrt(<value1> : number) => double
Description: Calculates the square root of a number
Examples:
1. SQRT(9) -> 3
******************************************************
Function: negate(<value1> : number) => number
Description: Negates a number. Turns positive numbers to negative and vice versa
Examples:
1. NEGATE(13) -> -13
******************************************************
Function: cos(<value1> : number) => double
Description: Calculates a consine value
Examples:
1. COS(10) -> -0.83907152907
******************************************************
Function: acos(<value1> : number) => double
Description: Calculates a consine inverse value
Examples:
1. ACOS(1) -> 0.0
******************************************************
Function: cosh(<value1> : number) => double
Description: Calculates a hyperbolic cosine of a value
Examples:
1. COSH(0) -> 1.0
******************************************************
Function: sin(<value1> : number) => double
Description: Calculates a sine value
Examples:
1. SIN(2) -> 0.90929742682
******************************************************
Function: asin(<value1> : number) => double
Description: Calculates a inverse sine value
Examples:
1. ASIN(0) -> 0.0
******************************************************
Function: sinh(<value1> : number) => double
Description: Calculates a hyperbolic sine value
Examples:
1. SINH(0) -> 0.0
******************************************************
Function: tan(<value1> : number) => double
Description: Calculates a tangent value
Examples:
1. TAN(0) -> 0.0
******************************************************
Function: atan(<value1> : number) => double
Description: Calculates a inverse tangent value
Examples:
1. ATAN(0) -> 0.0
******************************************************
Function: tanh(<value1> : number) => double
Description: Calculates a hyperbolic tangent value
Examples:
1. TANH(0) -> 0.0
******************************************************
Function: atan2(<value1> : number, <value2> : number) => double
Description: Returns the angle in radians between the positive x-axis of a plane and the point given by the coordinates
Examples:
1. ATAN2(0, 0) -> 0.0
******************************************************
Function: factorial(<value1> : number) => long
Description: Calculate the factorial of a number
Examples:
1. FACTORIAL(5) -> 120
******************************************************
Function: floor(<value1> : number) => number
Description: Returns the largest integer not greater than the number
Examples:
1. FLOOR(-0.1) -> -1
******************************************************
Function: ceil(<value1> : number) => number
Description: Returns the smallest integer not smaller than the number
Examples:
1. FLOOR(-0.1) -> 0
******************************************************
Function: degrees(<value1> : number) => double
Description: Converts radians to degrees
Examples:
1. DEGREES(3.141592653589793) -> 180
******************************************************
Function: log(<value1> : number, [<value2> : number]) => double
Description: Calculates log value. An optional base can be supplied else a euler number if used
Examples:
1. LOG(100, 10) -> 2
******************************************************
Function: log10(<value1> : number) => double
Description: Calculates log value based on 10 base
Examples:
1. LOG10(100) -> 2
******************************************************
Function: round(<number> : number, [<scale to round> : number], [<rounding option> : integral]) => double
Description: Rounds a number given a optional scale and a optional rounding mode. If the scale is omitted it is defaulted to 0.If the mode is omitted it is defaulted to ROUND_HALF_UP(5). The values for rounding include
1 - ROUND_UP 
2 - ROUND_DOWN 
3 - ROUND_CEILING 
4 - ROUND_FLOOR 
5 - ROUND_HALF_UP 
6 - ROUND_HALF_DOWN 
7 - ROUND_HALF_EVEN 
8 - ROUND_UNNECESSARY
Examples:
1. ROUND(100.123) -> 100.0
2. ROUND(2.5, 0) -> 3.0
3. ROUND(5.3999999999999995, 2, 7) -> 5.40
******************************************************
Function: current_date() => date
Description: Gets the current date
Examples:
1. CURRENT_DATE() -> 12-12-2030
******************************************************
Function: current_time() => timestamp
Description: Gets the current timestamp
Examples:
1. CURRENT_TIME() -> 12:12:12
******************************************************
Function: to_date(<string> : string, [<date format> : string]) => date
Description: Converts a string to a date given a optional date format. If the date format is omitted, combinations of the following are accepted. [yyyy, yyyy-[m]m, yyyy-[m]m-[d]d, yyyy-[m]m-[d]d, yyyy-[m]m-[d]d, yyyy-[m]m-[d]dT*]
Examples:
1. TO_DATE('2012-8-8') -> 2012-8-8
2. TO_DATE('12/12/2012', 'mm/dd/yyyy') -> 2012-12-12
******************************************************
Function: month(<value1> : date) => integer
Description: Gets the month value of a date
Examples:
1. MONTH(TO_DATE('2012-8-8')) -> 8
******************************************************
Function: year(<value1> : date) => integer
Description: Gets the year value of a date
Examples:
1. YEAR(TO_DATE('2012-8-8')) -> 2012
******************************************************
Function: hour(<value1> : date) => integer
Description: Gets the hour value of a date
Examples:
1. HOUR(TO_DATE('2009-07-30T12:58:59')) -> 12
******************************************************
Function: minute(<value1> : date) => integer
Description: Gets the minute value of a date
Examples:
1. MINUTE(TO_DATE('2009-07-30T12:58:59')) -> 58
******************************************************
Function: second(<value1> : date) => integer
Description: Gets the second value of a date
Examples:
1. SECOND(TO_DATE('2009-07-30T12:58:59')) -> 59
******************************************************
Function: dayOfMonth(<value1> : date) => integer
Description: Gets the day of the month given a date
Examples:
1. DAY_OF_MONTH(TO_DATE('2018-06-08')) -> 08
******************************************************
Function: dayOfWeek(<value1> : date) => integer
Description: Gets the day of the week given a date. 1 - Sunday, 2 - Monday ..., 7 - Saturday
Examples:
1. DAY_OF_MONTH(TO_DATE('2018-06-08')) -> 7
******************************************************
Function: dayOfYear(<value1> : date) => integer
Description: Gets the day of the year given a date
Examples:
1. DAY_OF_YEAR(TO_DATE('2016-04-09')) -> 100
******************************************************
Function: weekOfYear(<value1> : date) => integer
Description: Gets the week of the year given a date
Examples:
1. WEEK_OF_YEAR(TO_DATE('2008-02-20')) -> 8
******************************************************
Function: lastDayOfMonth(<value1> : date) => date
Description: Gets the last date of the month given a date
Examples:
1. LAST_DAY_OF_MONTH(TO_DATE('2009-01-12')) -> 2009-01-31
******************************************************
Function: monthsBetween(<from date> : date, <to date> : date) => double
Description: Gets the number of months between two dates
Examples:
1. MONTHS_BETWEEN(TO_DATE('1997-02-28 10:30:00'), TO_DATE('1996-10-30')) -> 3.94959677
******************************************************
Function: addMonths(<date> : date, <months to add> : integral) => date
Description: Add months to a date
Examples:
1. ADD_MONTHS(TO_DATE('2016-08-31'), 1) -> 2016-09-30
******************************************************
Function: sum(<value1> : number) => number
Description: Gets the aggregate sum of a numeric column
Examples:
1. SUM(col) -> value
******************************************************
Function: sumDistinct(<value1> : number) => number
Description: Gets the aggregate sum of distinct values of a numeric column
Examples:
1. SUM_DISTINCT(col) -> value
******************************************************
Function: count([<value1> : any]) => long
Description: Gets the aggregate count of values. If the optional column(s) are specified, it ignores NULL values in the count
Examples:
1. COUNT(custId) -> 100
2. COUNT(custId, custName) -> 50
3. COUNT() -> 125
******************************************************
Function: countDistinct(<value1> : any, [<value2> : any], ...) => long
Description: Gets the aggregate count of distinct values of a set of columns
Examples:
1. COUNT_DISTINCT(custId, custName) -> 60
******************************************************
Function: avg(<value1> : number) => number
Description: Gets the average of values of a column
Examples:
1. AVG(sales) -> 7523420.234
******************************************************
Function: mean(<value1> : number) => number
Description: Gets the mean of values of a column. Same as AVG
Examples:
1. MEAN(sales) -> 7523420.234
******************************************************
Function: min(<value1> : number) => number
Description: Gets the minimum value of a column
Examples:
1. MIN(sales) -> 00.01
******************************************************
Function: max(<value1> : number) => number
Description: Gets the maximum value of a column
Examples:
1. MAX(sales) -> 12312131.12
******************************************************
Function: stddev(<value1> : number) => double
Description: Gets the standard deviation of a column
Examples:
1. STDDEV(sales) -> 122.12
******************************************************
Function: stddev_population(<value1> : number) => double
Description: Gets the population standard deviation of a column
Examples:
1. STDDEV_POPULATION(sales) -> 122.12
******************************************************
Function: stddev_sample(<value1> : number) => double
Description: Gets the sample standard deviation of a column
Examples:
1. STDDEV_SAMPLE(sales) -> 122.12
******************************************************
Function: variance(<value1> : number) => double
Description: Gets the variance of a column
Examples:
1. VARIANCE(sales) -> 122.12
******************************************************
Function: variance_population(<value1> : number) => double
Description: Gets the population variance of a column
Examples:
1. VARIANCE_POPULATION(sales) -> 122.12
******************************************************
Function: variance_sample(<value1> : number) => double
Description: Gets the unbiased variance of a column
Examples:
1. VARIANCE_SAMPLE(sales) -> 122.12
******************************************************
Function: covariance_population(<value1> : number, <value2> : number) => double
Description: Gets the population covariance of a column
Examples:
1. COVARIANCE_POPULATION(sales) -> 122.12
******************************************************
Function: covariance_sample(<value1> : number, <value2> : number) => double
Description: Gets the sample covariance of a column
Examples:
1. COVARIANCE_SAMPLE(sales) -> 122.12
******************************************************
Function: kurtosis(<value1> : number) => double
Description: Gets the kurtosis of a column
Examples:
1. KURTOSIS(sales) -> 122.12
******************************************************
Function: skewness(<value1> : number) => double
Description: Gets the skewness of a column
Examples:
1. SKEWNESS(sales) -> 122.12

