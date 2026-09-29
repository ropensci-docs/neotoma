# Function to return chronological control tables from a `download_list` object.

Using a `download_list`, return the default chron-control table as a
`data.frame`.

## Usage

``` r
# S3 method for class 'download_list'
get_chroncontrol(x, chronology = 1, verbose = TRUE, add = FALSE)
```

## Arguments

- x:

  A `download_list` object.

- chronology:

  When `download` objects have more than associated chronology, which
  chronology do you want? Default is `1`.

- verbose:

  logical; should messages on API call be printed?

- add:

  Should the `chroncontrol` be added to the download object (default
  `FALSE`)
