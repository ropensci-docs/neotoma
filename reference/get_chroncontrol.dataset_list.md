# Function to return chronological control tables from a `dataset_list`.

Using a `dataset_list`, return the default chron-control table.

## Usage

``` r
# S3 method for class 'dataset_list'
get_chroncontrol(x, chronology = 1, verbose = TRUE, add = FALSE)
```

## Arguments

- x:

  A `dataset_list` object.

- chronology:

  When `download` objects have more than associated chronology, which
  chronology do you want? Default is `1`.

- verbose:

  logical; should messages on API call be printed?

- add:

  Should the `chroncontrol` be added to the download object (only
  accepts `FALSE`)
