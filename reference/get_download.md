# Function to return full download records using `site`s, `dataset`s, or dataset IDs.

Using the dataset ID, site object or dataset object, return all records
associated with the data as a `download_list`.

## Usage

``` r
get_download(x, verbose = TRUE)
```

## Arguments

- x:

  A single numeric dataset ID or a vector of numeric dataset IDs as
  returned by `get_datasets`, or a `site`, `dataset`, or `dataset_list`.

- verbose:

  logical; should messages on API call be printed?

## Value

This command returns either object of class `"try-error"`' (see
[`try`](https://rdrr.io/r/base/try.html)) defined by the error returned
from the Neotoma API call, or an object of class `download_list`,
containing a set of `download` objects, each with relevant assemblage
information and metadata: The `download` object is a list of lists and
data frames that describe an assemblage, the constituent taxa, the
chronology, site and PIs who contributed the data. The following are
important components:

- `dataset` :

  A table describing the collection, including dataset information, PI
  data compatible with
  [`get_contact`](https://docs.ropensci.org/neotoma/reference/get_contact.md)
  and site data compatable with
  [`get_site`](https://docs.ropensci.org/neotoma/reference/get_site.md).

- `sample.meta` :

  Dataset information for the core, primarily the age-depth model and
  chronology. In cases where multiple age models exist for a single
  record the most recent chronology is provided here.

- `taxon.list` :

  The list of taxa contained within the dataset, unordered, including
  information that can be used in
  [`get_taxa`](https://docs.ropensci.org/neotoma/reference/get_taxa.md)

- `counts` :

  The assemblage data for the dataset, arranged with each successive
  depth in rows and the taxa as columns. All taxa are described in
  `taxon.list`, the chronology is in `sample.data`

- `lab.data` :

  A data frame of laboratory data, such as exotic pollen spike, amount
  of sample counted, charcoal counts, etc.

- `chronologies` :

  A list of existing chronologies. If only a single chronology exists
  for a record then this is the same as the age-model in `sample.meta`.

## Note

The function returns a warning in cases where single taxa are defined by
multiple taphonomic characteristics, for example grains that are
identified separately as crumpled and torn in the same sample and sums
these values within a sample. In the case that a geochronology dataset
is passed to `get_download` the function returns a message and a NULL
object (that is later excised). Use `get_geochron` for these objects.
The chronologies can be augmented using the function `get_chroncontrol`,
where the individual chronology objects in `chronologies` will consist
of a table equivalent to `sample.meta` and a `chroncontrol` object.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
#  Search for sites with "Pseudotsuga" pollen that are older than 8kyr BP and
#  that are roughly within western British Columbia:
t8kyr.datasets <- get_dataset(taxonname='*Picea*', loc=c(-90, 41, -89, 44),
                              ageold = 20000, ageyoung=10000)

#  Returns 20 records (as of 04/04/2013), get the dataset for all records:
pollen.records <- get_download(t8kyr.datasets)

#  Standardize the taxonomies for the different records using the WS64 taxonomy.
compiled.sites <- compile_taxa(pollen.records, list.name='WS64')

#  Extract the Pseudotsuga curves for the sites:
get.curve <- function(x, taxa) {
               if (taxa %in% colnames(x$counts)) {
                 count <- x$counts[,taxa]/rowSums(x$counts, na.rm=TRUE)
               } else {
                 count <- rep(0, nrow(x$count))
               }
               data.frame(site = x$dataset$site.data$site.name,
               age = x$sample.meta$age,
               count = count)
             }

curves <- do.call(rbind.data.frame,
                  lapply(compiled.sites, get.curve, taxa = 'Larix/Pseudotsuga'))

#  For illustration, remove the sites with no Pseudotsuga occurance:
curves <- curves[curves$count > 0, ]

smooth.curve <- predict(loess(sqrt(count)~age, data=curves),
                        data.frame(age=seq(20000, 0, by = -100)))

plot(sqrt(count) ~ age, data = curves,
     ylab = '% Pseudotsuga/Larix', xlab='Calibrated Years BP', pch=19,
     col=rgb(0.1, 0.1, 0.1, 0.1), xlim=c(0, 20000))
lines(seq(20000, 0, by = -100), smooth.curve, lwd=2, lty=2, col=2)

#  This figure shows us an apparent peak in Larix/Pseudotsuga pollen in the
#  early-Holocene that lends support to a warmer, drier early-Holocene in
#  western North America.
} # }
```
