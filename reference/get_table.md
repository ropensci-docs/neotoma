# Get Neotoma value tables.

Get Neotoma value tables.

## Usage

``` r
get_table(table.name = NULL)
```

## Arguments

- table.name:

  Call one of the available tables in the Neotoma Database. A full
  listing of tables can be found here:
  <http://wnapi.neotomadb.org/doc/resources/dbtables>. By default it
  returns all objects in the table.

## Details

A table of values corresponding to the parameter of interest.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
taxon.table <- get_table('Taxa')

#  Get the frequency of a random taxon in Neotoma.
tax_sample <- sample(nrow(taxon.table), 1)
cat("The taxon", 
    taxon.table$TaxonName[tax_sample], 
    "occurs in Neotoma", 
    length(get_dataset(taxonname = taxon.table$TaxonName[tax_sample])), 
    "times.")
} # }
```
