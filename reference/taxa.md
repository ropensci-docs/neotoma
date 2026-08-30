# Access proxy taxonomic data

Extracts taxa from `download` objects and returns them in a useful
format.

## Usage

``` r
taxa(obj, ...)

# S3 method for class 'download'
taxa(obj, ...)

# S3 method for class 'download_list'
taxa(obj, collapse = TRUE, hierarchy = FALSE, ...)
```

## Arguments

- obj:

  an R object from which counts are to be extracted.

- ...:

  arguments passed to other methods.

- collapse:

  should the results be returned as a list, one for each site (`FALSE`),
  or a single dataframe of all taxa? Default is `TRUE`

- hierarchy:

  Should the taxonomic hierarchy be included?

## Value

Either a data frame of taxa or a list of such objects.

## Details

Methods are available for "download" and "download_list" objects.

## Author

Simon Goring

## Examples

``` r
if (FALSE) { # \dontrun{
ostracodes <- get_dataset(datasettype = 'ostracode')

ostro.dl <- get_download(ostracodes)
ostro.taxa <- taxa(ostro.dl)
} # }
```
