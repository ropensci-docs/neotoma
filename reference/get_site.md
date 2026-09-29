# Return Site Information.

Return site information from the Neotoma Paleoecological Database.

`get_site` returns site information from the Neotoma Paleoecological
Database based on parameters defined by the user.

## Usage

``` r
get_site(sitename, altmin, altmax, loc, gpid, ...)
```

## Arguments

- sitename:

  character string representing the full or partial site name, or an
  object of class `dataset`, `dataset_list`, `download` or
  `download_list`

- altmin:

  Minimum site altitude (in m).

- altmax:

  Maximum site altitude (in m).

- loc:

  A numeric vector c(lonW, latS, lonE, latN) representing the bounding
  box within which to search for sites. The convention here is to use
  negative values for longitudes west of Grewnwich or longitudes south
  of the equator.

- gpid:

  A character string or numeric value, must correspond to a valid
  geopolitical identity in the Neotoma Database. Use
  get.tables('GeoPoliticalUnits') for a list of acceptable values, or
  link here: http://wnapi.neotomadb.org/apdx/geopol.htm

- ...:

  Optional additional arguments

## Value

A data frame:

- `siteid`:

  Unique database record identifier for the site.

- `sitename`:

  Name of the site.

- `long`:

  Mean longitude, in decimal degrees, for a site (-180 to 180).

- `lat`:

  Mean latitude, in decimal degrees, for a site (-90 to 90).

- `elev`:

  Elevation in meters.

- `description`:

  Free form description of a site, including such information as
  physiography and vegetation around the site.

- `long_acc`:

  If the site is described by a bounding box this is the box width.

- `lat_acc`:

  If the site is described by a bounding box this is the box height.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/sites

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
#  What is the distribution of site elevations in Neotoma?
all.sites <- get_site()  #takes a bit of time.

plot(density(all.sites$elev, from = 0, na.rm=TRUE),
main = 'Altitudinal Distribution of Neotoma Sites', xlab = 'Altitude (m)', log='x')

#  Get site information from a dataset:
nw.datasets <- get_dataset(loc = c(-140, 50, -110, 65), 
                           datasettype='pollen',
                           taxonname='Pinus*')
                           
nw.sites <- get_site(nw.datasets)

} # }
```
