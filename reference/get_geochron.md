# Function to return geochronological data from records.

Using the dataset ID, return all geochronological data associated with
the dataID. At present, only returns the dataset in an unparsed format,
not as a data table. This function will only download one dataset at a
time.

## Usage

``` r
get_geochron(x, verbose = TRUE)
```

## Arguments

- x:

  A numeric dataset ID or a vector of numeric dataset IDs, or an object
  of class of class `site`, `dataset`, `dataset_list`, `download` or
  `download_list` for which geochrons are required.

- verbose:

  logical; should messages on API call be printed?

## Value

This command returns either an object of class `"try-error"`' (see
[`try`](https://rdrr.io/r/base/try.html)) defined by the error returned
from the Neotoma API call, or a `geochronologic` object, which is a list
with two components, a `dataset` and a geochronology table, a
`data.frame` with the following components:

- `sample.id` :

  A unique identifier for the geochronological unit.

- `age.type` :

  String. The age type, one of calendar years, radiocarbon years, etc.

- `age` :

  Dated age of the material.

- `e.older` :

  The older error limit of the age value. Commonly 1 standard deviation.

- `e.young` :

  The younger error limit of the age value.

- `delta13C` :

  The measured or assumed delta13C value for radiocarbon dates, if
  provided.

- `material.dated` :

  A table describing the collection, including dataset information, PI
  data compatible with
  [`get_contact`](https://docs.ropensci.org/neotoma/reference/get_contact.md)
  and site data compatable with
  [`get_site`](https://docs.ropensci.org/neotoma/reference/get_site.md).

- `geo.chron.type` :

  Text string, type of geochronological analysis, i.e., Radiocarbon
  dating, luminesence.

- `notes` :

  Text string

- `infinite` :

  Boolean, does the dated material return an "infinite" date?

A full data object containing all the relevant geochronological data
available for a dataset.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
#  Search for the sites around Marion Lake, BC.  I want to find sites within 
#  about 1km.

marion <- get_site(sitename = "Marion Lake*")

marion_close <- get_closest(marion, n = 10, buffer = 1)

#  Returns 116 records (as of 13/07/2015).  These are the pollen records though, 
#  we want the sites:
geochron.records <- get_geochron(marion_close)

#  We want to extract all the radiocarbon ages from the records:

get_ages <- function(x){
  any.ages <- try(x[[2]]$age[x[[2]]$age.type == 'Radiocarbon years BP'])
  if(is(any.ages, 'try-error')) output <- NA
  if(!is(any.ages, 'try-error')) output <- unlist(any.ages)
  output
}

radio.chron <- unlist(sapply(geochron.records, get_ages))

hist(radio.chron[radio.chron<40000], breaks=seq(0, 25000, by = 1000),
     main = 'Radiocarbon dates for Pseudotsuga records',
     xlab = 'Radiocarbon date (14C years before 1950)')
} # }
```
