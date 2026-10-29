# Open a browser window to display a Neotoma dataset within the Neotoma Explorer

Using a `download` or `dataset` object, open up a browser window in the
users default browser. Passing a `download_list` or `dataset_list` will
open Neotoma Explorer with the first object and return a warning.

Using a numeric value, `download`, `download_list`, `dataset` or
`dataset_list` object, open up a browser window in the users default
browser. Very large objects

## Usage

``` r
browse(x)
```

## Arguments

- x:

  A numeric value, `download`, `download_list`, `dataset` or
  `dataset_list` object.

## Value

Returns a NULL value, opens a browser.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/sites

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# Where are the XRF data?

xrf.data <- get_dataset(datasettype='X-ray fluorescence (XRF)')
browse(xrf.data)

} # }
```
