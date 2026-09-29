# Function to bind objects together into a longer object.

From multiple `download*`s, `dataset*`s or `site`s, join them together
into a single object.

## Usage

``` r
bind(x, ...)
```

## Arguments

- x:

  An object returned by one of the `get_*` commands for download, site
  or dataset.

- ...:

  other objects of the same class.

## Value

This command returns a larger list.

## Details

To support further synthesis and analysis `compile_download` works to
transform a list returned by
[`get_download`](https://docs.ropensci.org/neotoma/reference/get_download.md)
into a large data frame with columns for site and sample attributes and
also with the associated assemblage data at each sample depth. This
function also does the same for single sites.

## References

Neotoma Project Website: http://www.neotomadb.org

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
#  Search for sites with "Thuja" pollen that are older than 8kyr BP and
#  that are on the west coast of North America:
t8kyr.poa <- get_dataset(taxonname="Thuja*", 
                         loc=c(-150, 20, -100, 60), ageyoung = 8000)
t8kyr.canis <- get_dataset(taxonname="Canis*", 
                           loc=c(-150, 20, -100, 60), ageyoung = 8000)

t8kyr.co_site <- bind(t8kyr.poa, t8kyr.canis)
plot(t8kyr.co_site)

####
# We want to look at four different dataset types across a forest-prairie 
# boundary:
dataset_types <- c("ostracode surface sample",
                   "water chemistry",
                   "diatom surface sample",
                   "pollen surface sample")

# Run the `get_dataset` function for each of the different dataset types 
dataset_lists <- lapply(dataset_types, 
                          function(x) { 
                            get_dataset(datasettype=x, 
                                        loc = c(-100,43,-92,48))
                                        })

# Using do.call here to make sure that I don't have to split the list out.
new_datasets <- do.call(bind, dataset_lists)

# And voila!
plot(new_datasets)

} # }
```
