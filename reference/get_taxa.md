# Get taxon information from Neotoma.

Get taxon information from Neotoma.

## Usage

``` r
get_taxa(taxonid, taxonname, status, taxagroup, ecolgroup)
```

## Arguments

- taxonid:

  Numeric taxon identifier used in Neotoma

- taxonname:

  A character string representing the full or partial name of taxa of
  interest.

- status:

  The current status of the taxon, one of 'extinct', 'extant', 'all'.

- taxagroup:

  The taxonomic grouping for the taxa. See
  <http://wnapi.neotomadb.org/doc/resources/taxa> for the list of
  approved groupings.

- ecolgroup:

  The ecological group of the taxa. More detailed than `taxagroup`, can
  be obtained using `get_table("EcolGroupTypes")`.

## Value

Returns a data frame with the following components:

- `TaxonID` :

  Unique database record identifier for a taxon

- `TaxonCode` :

  Shorthand notation for a taxon identification

- `TaxonName` :

  Name of the taxon

- `Author` :

  Author(s) of the name. Used almost exclusively with beetle taxa

- `Extinct` :

  True if extinct; false if extant

- `TaxaGroup` :

  Code for taxa group to which taxon belongs

- `EcolGroups` :

  Array of ecological group codes to which the taxon belongs

- `HigherTaxonID` :

  TaxonID of the next higher taxonomic rank

- `PublicationID` :

  Publication identification number

- `Notes` :

  Free-form notes or comments about the taxon

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
## Return all species taxa with "Abies" in name - note wildcard
taxa <- get_taxa(taxonname = "Abies*")
} # }
```
