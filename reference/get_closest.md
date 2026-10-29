# Find the closest dataset records to a site, dataset or long/lat pair in Neotoma

Passing in a download object the function outputs a Bacon or Clam
formatted file to a user defined destination for age modelling with
existing age-depth modeling software.

## Usage

``` r
get_closest(x, n, buffer, ...)
```

## Arguments

- x:

  A vector long/lat pair, or a dataset, site or download.

- n:

  The maximum number of records to return (in the case of ties the
  return may be larger)

- buffer:

  The size of the buffer for dataset search (in meters)

- ...:

  optional arguments to pass into `get_dataset`.

## Value

This command returns a `dataset` or `dataset_list`, or NULL if no
records exist within the bounding box.

## Details

The function uses the `sf` package to generate a circular buffer around
a point of interest. From there a square bounding box is sent to Neotoma
using the
[`get_dataset()`](https://docs.ropensci.org/neotoma/reference/get_dataset.md)
function. To use the buffering function we must convert from long/lat to
UTM coordinates, which we do by guessing the UTM zone of the point of
interest. Details can be found in the function's R code hosted on
GitHub:
<https://github.com/ropensci/neotoma/blob/master/R/get_closest.R>

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>, Andria Dawson
<andria.dawson@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
#  The point of pulling chronology tables is to re-build or examine the chronological
#  information that was used to build the age-depth model for the core.
# Find the closest records to Madison, WI:
get_closest(x = c(-89.4012, 43.0731), n = 10, buffer = 5000, datasettype = "pollen")
} # }
```
