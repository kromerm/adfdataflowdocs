## Shortcuts

Ctrl-K Ctrl-C: Comment entire line
Ctrl-K Ctrl-U: Uncomment


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

true() in your alter row filter will allow all rows to match that condition. Good for Upsert

## Use byName() to access "hidden fields"

When you are working in the ADF Data Flow UI, you can see the metadata as you construct your transformations. The metadata is based on the projection of the source plus the columns defined in transformations. However, in some instances you do not get the metadata due to schema drift, column patterns, or dynamic transfomrations like Pivot that create column names on the fly. In that case, you byName():

`toString(byName('mynewcol'))`
