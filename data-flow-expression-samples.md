## Shortcuts

Ctrl-K Ctrl-C: Comment entire line
Ctrl-K Ctrl-U: Uncomment

## Manual Comments

/* This is my comment */

TIP: If you put a comment at the top of your expression, it will appear in the transformation text box to document your transformation expressions:

![Comments](media/data-flow/comments2.png "Comments")

## Convert Date to String format

`toString(toDate('28/03/2010', 'dd/MM/yyyy'), 'ddMMMyyyy')`
= 28Mar2010


## Concat Strings Shortcut

'This is my string.' + ' This is my new string.'
= This is my string. This is my new string


## Regexp

https://kromerbigdata.com/2019/01/02/azure-data-factory-data-flow-transform-data-with-regular-expressions/

* regexReplace(Address1,`[ ]{2}|\.`,' ')
* regex_extract(Address1, `^(\d+)`, 1)
* rlike(City,'^[A-G]')

## Good for Alter Row:

`true()`

Use it in your alter row filter will allow all rows to match that condition. Good for Upsert. No need to use 1==1.

Or, if you want inequality (1==0):

`false()`

## Use byName() to access "hidden fields"

When you are working in the ADF Data Flow UI, you can see the metadata as you construct your transformations. The metadata is based on the projection of the source plus the columns defined in transformations. However, in some instances you do not get the metadata due to schema drift, column patterns, or dynamic transfomrations like Pivot that create column names on the fly. In that case, you byName():

`toString(byName('mynewcol'))`

## Fuzzy matching

`Soundex(columnname)`

## isNull / coalesce

`isNull (col1, 'somevalue')`

or

`coalesce(expression)`

## Lookup Match / No match

After your Lookup transformation, you can use subsequent transformations to inspect the results of each match row by using the expression function `isMatch()` to make further choices in your logic based on whether or not the Lookup resulted in a row match or not.

## Regex to remove non-alphanumeric chars

```
regexReplace(mystring,`^a-zA-Z\d\s:`,'')
```

## Convert to Timestamp

`toTimestamp('10/20/2018T08:11:22Z','MM/dd/yyyy\'T\'hh:mm:ss\'Z\'')`

