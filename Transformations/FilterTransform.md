# Azure Data Factory Data Flow Transformations

## Filter

The Filter transforms is a row filter takes an expression as its parameter. Click in the text box to launch the Expression Builder. This is where you can build a filter expression which allows you to control which rows from the current data stream are allowed to pass through (filter) to the next transformation.

I.e. filter on loan_status column:

```
in([‘Default’, ‘Charged Off’, ‘Fully Paid’], loan_status).
```

Filter on the year column in the Movies demo:

```
year > 1980
```
