# Function to return full download records using `numeric` dataset IDs.

Using the dataset ID, return all records associated with the data as a
`download_list`.

## Usage

``` r
# Default S3 method
get_download(x, verbose = TRUE)
```

## Arguments

- x:

  A single numeric dataset ID or a vector of numeric dataset IDs as
  returned by `get_datasets`.

- verbose:

  logical; should messages on API call be printed?
