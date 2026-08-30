# Leaflet plots for neotoma data.

A plotting function to provide interactive data investigation using the
leaflet tools. This package requires a connection to the internet for
proper functioning.

## Usage

``` r
plot_leaflet(x, providerTiles = "Stamen.TerrainBackground", ...)
```

## Arguments

- x:

  A neotoma data object

- providerTiles:

  Default "Stamen.TerrainBackground", a character string indicating the
  tile background to be used for plotting.

- ...:

  Other terms to be passed to the function.

## Value

A `leaflet` object
