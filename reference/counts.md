# Access proxy count data

Extract pollen or other proxy counts from data objects and returns them
in a useful format.

## Usage

``` r
counts(obj, ...)

# S3 method for class 'download'
counts(obj, ...)

# S3 method for class 'download_list'
counts(obj, ...)
```

## Arguments

- obj:

  an R object from which counts are to be extracted.

- ...:

  arguments passed to other methods.

## Value

Either a data frame of counts or a list of such objects.

## Details

Methods are available for "download" and "download_list" objects.

## Author

Gavin Simpson

## Examples

``` r
if (FALSE) { # \dontrun{
marion <- get_site('Marion Lake%')
louise <- get_site('Louise Pond%')
western.sites <- rbind(marion, louise)
western.data  <- get_dataset(western.sites)

western.dl <- get_download(western.data)
western.cnt <- counts(western.dl)
sapply(western.cnt, dim)
marion.cnt<- counts(western.dl[[1]])
dim(marion.cnt)
} # }
```
