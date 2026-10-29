# Extracts the depth values from a \`download\` object

Using a `download` object, return the sample depths (if available).

Using a numeric value, `download`, `download_list`, `dataset` or
`dataset_list` object, open up a browser window in the users default
browser. Very large objects

## Usage

``` r
depths(obj, ...)

# Default S3 method
depths(obj, ...)

# S3 method for class 'download'
depths(obj, ...)

# S3 method for class 'download_list'
depths(obj, ...)
```

## Arguments

- obj:

  A `download` object.

- ...:

  arguments passed to other methods.

## Value

Returns a vector of depths.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/sites

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples
