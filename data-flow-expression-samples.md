## Shortcuts

Ctrl-K Ctrl-C: Comment entire line
Ctrl-K Ctrl-U: Uncomment


## Convert Date to String format

toString(toDate('28/03/2010', 'dd/MM/yyyy'), 'ddMMMyyyy')
= 28Mar2010


## Concat Strings Shortcut

'This is my string.' + ' This is my new string.'
= This is my string. This is my new string


## Regexp

https://kromerbigdata.com/2019/01/02/azure-data-factory-data-flow-transform-data-with-regular-expressions/

* regexReplace(Address1,`[ ]{2}|\.`,' ')
* regex_extract(Address1, `^(\d+)`, 1)
* rlike(City,'^[A-G]')
