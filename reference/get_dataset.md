# Obtain dataset information from the Neotoma Paleoecological Database or an existing object.

A function to access the Neotoma API and return datasets corresponding
to the parameters defined by the user.

## Usage

``` r
get_dataset(
  x,
  datasettype,
  piid,
  altmin,
  altmax,
  loc,
  gpid,
  taxonids,
  taxonname,
  ageold,
  ageyoung,
  ageof,
  subdate
)
```

## Arguments

- x:

  An optional value, either a `numeric` site ID or object of class
  `download`, `download_list` or `site`.

- datasettype:

  A character string corresponding to one of the allowed dataset types
  in the Neotoma Database. Allowed types include: `"geochronologic"`,
  `"loss-on-ignition"`, `"pollen"`, `"plant macrofossils"`,
  `"vertebrate fauna"`, `"mollusks"`, and `"pollen surface sample"`. See
  note in Details delow.

- piid:

  Numeric value for the Principle Investigator's ID number.

- altmin:

  Numeric value indicating the minimum altitude for the site (can be
  used alone or with `altmax`).

- altmax:

  Numeric value indicating the maximum altitude for the site (can be
  used alone or with `altmin`).

- loc:

  A numeric vector `c(lonW, latS, lonE, latN)` representing the bounding
  box within which to search for sites. The convention here is to use
  negative values for longitudes west of Greenwich or longitudes south
  of the equator

- gpid:

  A character string or numeric value, must correspond to a valid
  geopolitical identity in the Neotoma Database. Use
  get.tables('GeoPoliticalUnits') for a list of acceptable values, or
  link here: <http://wnapi.neotomadb.org/apdx/geopol.htm>

- taxonids:

  A numeric identifier for the taxon. See
  [`get_table`](https://docs.ropensci.org/neotoma/reference/get_table.md)
  and use `get_table('Taxa')` for a list of acceptable values.

- taxonname:

  A character string corresponding to a valid taxon identity in the
  Neotoma Database. See
  [`get_table`](https://docs.ropensci.org/neotoma/reference/get_table.md)
  and use `get_table('Taxa')` for a list of acceptable values.

- ageold:

  The oldest date acceptable for the search (in years before present).

- ageyoung:

  The youngest date acceptable for the search.

- ageof:

  If a taxon ID or taxon name is defined this parameter must be set to
  `"taxon"`, otherwise it may refer to `"sample"`, in which case the age
  bounds are for any samples within datasets or `"dataset"` if you want
  only datasets that are within the bounds of ageold and ageyoung.

- subdate:

  Date of dataset submission, either YYYY-MM-DD or MM-DD-YYYY.

## Value

More details on the use of these parameters can be obtained from
<http://wnapi.neotomadb.org/doc/resources/datasets>.

A list of class \`dataset_list\`, with each item corresponding to an
individual record. Searches that return no items will result in a NULL
value being returned. Otherwise each list item (each dataset record)
includes the following components:

- `dataset.id` :

  Unique database record identifier for the dataset.

- `dataset.name` :

  Name of the dataset; not commonly used.

- `CollUnitHandle` :

  Code name of the Collection Unit with which the dataset is associated.
  This code may be up to 10 characters. Data are frequently distributed
  by Collection Unit, and the Handle is used for file names.

- `CollUnitID` :

  Unique database record identifier for the collection unit.

- `CollType` :

  The collection type. Types include cores, sections, excavations, and
  animal middens.

- `DatasetType` :

  The dataset type, such as: geochronologic, loss-on-ignition, pollen,
  plant macrofossils, vertebrate fauna, etc.

- `AgeOldest` :

  The oldest of all sample ages (in calendar years before present) in
  the dataset.

- `AgeYoungest` :

  The youngest of all sample ages (in calendar years before present) in
  the dataset.

- `SubDates` :

  An array of objects that describe dataset submission events. If
  multiple submissions occurred then this is a table.

- `DatasetPIs` :

  An array of objects that describe Principal Investigators associated
  with a dataset.

- `Site` :

  An object describing the site where the dataset samples were taken.

## Details

With regards to `datasettypes`, because Neotoma is a "living" database,
and new dataset types are being added in an ongoing manner as new
research disciplines use the database, you can use
`get_table("datasettypes")` to see the full list of available dataset
types in the database.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
# Search for sites with "Thuja" pollen that are older than 8kyr BP and
# that are on the west coast of North America:
t8kyr.datasets <- get_dataset(taxonname='Thuja*', 
                              loc=c(-150, 20, -100, 60), 
                              ageyoung = 8000)

# Search for vertebrate fossils in Canada (gpid: 756) within the last 2kyr.
gpids <- get_table(table.name='GeoPoliticalUnits')
canID <- gpids[which(gpids$GeoPoliticalName == 'Canada'),1]

v2kyr.datasets <- get_dataset(datasettype='vertebrate fauna', 
                              gpid=canID, 
                              ageold = 2000)
} # }
```
