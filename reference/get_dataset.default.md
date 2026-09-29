# Obtain dataset information from the Neotoma Paleoecological Database or an existing object.

A function to access the Neotoma API and return datasets corresponding
to the parameters defined by the user.

## Usage

``` r
# Default S3 method
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

  A numeric value corresponding to the site ID.

- datasettype:

  A character string corresponding to one of the allowed dataset types
  in the Neotoma Database. You can find the full list of allowed
  datasettypes using: `get_table("datasettypes")`.

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
