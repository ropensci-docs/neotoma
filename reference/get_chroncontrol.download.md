# Function to return chronological control tables from a `download` object.

Using a `download`, return the default chron-control table as a
`data.frame`.

## Usage

``` r
# S3 method for class 'download'
get_chroncontrol(x, chronology = 1, verbose = TRUE, add = FALSE)
```

## Arguments

- x:

  A single `download` object.

- chronology:

  For `download` methods, which chronology controls should be used?

- verbose:

  logical; should messages on API call be printed?

- add:

  Should the `chroncontrol` be added to the download object (default
  `FALSE`)
