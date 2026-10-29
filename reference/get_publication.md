# A function to get publications for sites or datasets in the Neotoma Database using the API.

The function takes the parameters, defined by the user, and returns a
table with publication information from the Neotoma Paleoecological
Database.

## Usage

``` r
get_publication(x, contactid, datasetid, author, pubtype, year, search)
```

## Arguments

- x:

  Numeric Publication ID value, either from
  [`get_dataset`](https://docs.ropensci.org/neotoma/reference/get_dataset.md)
  or known.

- contactid:

  Numeric Contact ID value, either from
  [`get_dataset`](https://docs.ropensci.org/neotoma/reference/get_dataset.md)
  or
  [`get_contact`](https://docs.ropensci.org/neotoma/reference/get_contact.md)

- datasetid:

  Numeric Dataset ID, known or from
  [`get_dataset`](https://docs.ropensci.org/neotoma/reference/get_dataset.md)

- author:

  Character string for full or partial author's name. Can include
  wildcards such as 'Smit\*' for all names beginning with 'Smit'.

- pubtype:

  Character string, one of eleven allowable types, see
  [`get_table`](https://docs.ropensci.org/neotoma/reference/get_table.md).
  For a list of allowed types run `get_table("PublicationTypes")`.

- year:

  Numeric publication year.

- search:

  A character string to search for within the article citation.

## Value

A list is returned with two data frame components:

- `meta` :

  A single row with Publication ID, type, year of publication and full
  citation.

- `Authors` :

  `data.frame` of author names, order and IDs, can be of variable
  length.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
#  To find all publications from 1998:
year.cont <- get_publication(year = 1998)

# To find all data contributors who have the last name "Smith"
smith.cont <- get_publication(author = 'Smith')
} # }
```
