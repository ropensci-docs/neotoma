# Function to read in defined Bacon outputs.

Reads in Bacon output and formats it for inclusion in a download object.

## Usage

``` r
read_bacon(
  x,
  path = ".",
  add = FALSE,
  chron_name = "Bacon",
  as_default = TRUE,
  download = NULL,
  sections = NULL,
  age_field = "median",
  interp = TRUE
)
```

## Arguments

- x:

  A folder path that contains a Bacon `age` file.

- path:

  The location of the `Cores` folder.

- add:

  Should the results be added to an existing `download`? Defaults to
  `FALSE`.

- chron_name:

  The name for the chronology if the Bacon file is being added to a
  `download`.

- as_default:

  Should the chronology become the default?

- download:

  The target `download` if `add` is `TRUE`.

- sections:

  If there are multiple Bacon runs in a folder, identify the file by the
  number of sections in the run.

- age_field:

  Should the age be assigned to the `"median"` or the `"wmean"`?

- interp:

  If the depths don't match up, should we interpolate from the Bacon
  output? (default `TRUE`)

## Details

The function expects that you are in a working directory containing a
"Cores" which would then contain output files from Bacon runs. The
output can either be added to an existing record (for example, replacing
the default age model returned by Neotoma), or it can be loaded on its
own. If the depths for the loaded file do not match with the depths in
the \`download\`'s \`sample.meta\` then the user can use the \`interp\`
parameter to interpolate between depths. This method uses linear
interpolation.

## Examples

``` r
if (FALSE) { # \dontrun{
# Download the record for Lake O' Pines:
lake_o_dl <- get_download(15925)

# This assumes that you have Bacon installed in a folder and have
# set it to your working directory.

write_agefile(lake_o_dl[[1]], path = ".", chronology = 1, 
              corename = "LAKEPINES", cal.prog = 'Bacon') 

source("Bacon.R") 

# These defaults just help the core run quickly, they're not 
# neccesarily good parameters.

Bacon("LAKEPINES", acc.mean = 10, 
      thick = 50, depths.file = TRUE, 
      suggest = FALSE, ask = FALSE)

lake_o_dl <- read_bacon("LAKEPINES", add = TRUE, 
                        download = download, sections = 17)

} # }
```
