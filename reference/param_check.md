# Internal function to check passed parameters.

Functions
[`get_site`](https://docs.ropensci.org/neotoma/reference/get_site.md),
[`get_dataset`](https://docs.ropensci.org/neotoma/reference/get_dataset.md)
and others pass parameters to `param_check`, which tells them if there's
a problem.

## Usage

``` r
param_check(cl)
```

## Arguments

- cl:

  Contact ID is a numerical value associated with the Neotoma Contact
  table's numerical Contact ID.

## Value

A list with two components:

- flag:

  Returns a 0 if everything's fine, a 1 if there's a problem.

- message:

  A list of error messages.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>
