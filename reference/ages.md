# Access proxy age data

Extracts age information from objects and returns them in a useful
format.

## Usage

``` r
ages(obj, ...)

# S3 method for class 'download'
ages(obj, ...)

# S3 method for class 'download_list'
ages(obj, ...)
```

## Arguments

- obj:

  an R object from which counts are to be extracted.

- ...:

  arguments passed to other methods.

## Value

Either a data frame of ages or a list of such objects.

## Details

Methods are available for "download" and "download_list" objects.

## Author

Simon Goring

## Examples

``` r
if (FALSE) { # \dontrun{
ostracodes <- get_dataset(datasettype = 'ostracode')

ostro.dl <- get_download(ostracodes)
ostro.ages <- ages(ostro.dl)
} # }
```
