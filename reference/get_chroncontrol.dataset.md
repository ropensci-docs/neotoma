# Function to return chronological control tables from a `dataset`.

Using a `dataset`, return the default chron-control table.

## Usage

``` r
# S3 method for class 'dataset'
get_chroncontrol(x, chronology = 1, verbose = TRUE, add = FALSE)
```

## Arguments

- x:

  A `dataset`.

- chronology:

  When `download` objects have more than associated chronology, which
  chronology do you want? Default is `1`.

- verbose:

  logical; should messages on API call be printed?

- add:

  Should the `chroncontrol` be added to the download object (only
  accepts `FALSE`)
