# Palaeoecological stratigraphic diagrams

Draws paleoecological diagrams from a `download` object. Allows control
of variable type (using the `tran` function from the `analogue`
package), and taxonomic grouping.

## Usage

``` r
# S3 method for class 'download'
Stratiplot(x, yaxis = "age", method = "none", group = NULL, ...)
```

## Arguments

- x:

  A `download` object.

- yaxis:

  One of the columns in `sample.meta`, including `depth`, `age`,
  `age.younger`, or `age.older`, default `age`.

- method:

  An option for axis transformation using `tran` from the `analogue`
  package. `"none"` by default.

- group:

  An ecological group from the taxon table.

- ...:

  variables to be passed to `Stratiplot`.

## Value

A `trellis` object.

## Details

A wrapper for the `analogue` package's `Stratiplot` function. Allowing
the user to plot a stratigraphic diagram directly from a `download`
object.

## Examples

``` r
if (FALSE) { # \dontrun{
lake_o_dl <- get_download(15925)
Stratiplot(lake_o_dl[[1]])
} # }
```
