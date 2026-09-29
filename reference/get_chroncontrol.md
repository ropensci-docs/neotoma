# Function to return chronological control tables used to build age models.

Using the dataset ID, return all records associated with the data. At
present, only returns the dataset in an unparsed format, not as a data
table. This function will only download one dataset at a time.

## Usage

``` r
get_chroncontrol(x, chronology = 1, verbose = TRUE, add = FALSE)
```

## Arguments

- x:

  A single numeric chronology ID, a vector of numeric dataset IDs as
  returned by
  [`get_dataset`](https://docs.ropensci.org/neotoma/reference/get_dataset.md)
  or a `download` or `download_list` object.

- chronology:

  When `download` objects have more than associated chronology, which
  chronology do you want? Default is `1`.

- verbose:

  logical, should messages on API call be printed?

- add:

  logical, should this chron control be added to the download object?

## Value

This command returns either an object of class `"try-error"` containing
the error returned from the Neotoma API call, or a full data object
containing all the relevant information required to build either the
default or prior chronology for a core. When `download` or
`download_list` objects are passes, the user can `add` the chroncontrol
to the `download` object explicitly, in which case the function will
return a download with `chroncontrol` embedded.

This is a list comprising the following items:

- `chron.control` :

  A table describing the collection, including dataset information, PI
  data compatable with
  [`get_contact`](https://docs.ropensci.org/neotoma/reference/get_contact.md)
  and site data compatable with
  [`get_site`](https://docs.ropensci.org/neotoma/reference/get_site.md).

- `meta` :

  Dataset information for the core, primarily the age-depth model and
  chronology. In cases where multiple age models exist for a single
  record the most recent chronology is provided here.

If Neotoma returns empty content, either the control table or the
associated metadata (which happens in approximately 25

## References

\+ Neotoma Project Website: http://www.neotomadb.org + API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
#  The point of pulling chronology tables is to re-build or examine the 
#  chronological information that was used to build the age-depth model for 
#  the core.  You can do this by hand, but the `write_agefile` function works 
#  with `download` objects directly.

three_pines <- get_download(get_dataset(get_site("Three Pines Bog"), 
                                        datasettype = "pollen"))
pines_chron <- get_chroncontrol(three_pines)

# Spline interpolation:
model <- smooth.spline(x = pines_chron[[1]]$chron.control$depth,
                       y = pines_chron[[1]]$chron.control$age)
                       
new_ages <- predict(model, x = three_pines[[1]]$sample.meta$depth)

} # }
```
