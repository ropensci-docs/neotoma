# A function to get publications for sites or datasets in the Neotoma Database using the API.

The function takes the parameters, defined by the user, and returns a
table with publication information from the Neotoma Paleoecological
Database.

## Usage

``` r
# Default S3 method
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
