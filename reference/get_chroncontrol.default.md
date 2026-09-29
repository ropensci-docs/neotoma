# Function to return chronological control tables from a chronologic ID.

Using the chronology ID, return the chron control table as a
`data.frame`.

## Usage

``` r
# Default S3 method
get_chroncontrol(x, chronology = 1, verbose = TRUE, add = FALSE)
```

## Arguments

- x:

  A single numeric chronology ID or a vector of numeric chronology IDs
  as returned by `get_datasets`.

- chronology:

  For `download` methods, which chronology controls should be used?

- verbose:

  logical; should messages on API call be printed?

- add:

  logical, should this chron control be added to the download object?
