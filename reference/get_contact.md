# Get contact information.

A function to obtain contact information for data contributors from the
Neotoma Paleoecological Database.

## Usage

``` r
get_contact(contactid, contactname, contactstatus, familyname)
```

## Arguments

- contactid:

  Contact ID is a numerical value associated with the Neotoma Contact
  table's numerical Contact ID.

- contactname:

  A character string indicating the data contributors' project,
  organization or personal name. May be a partial string and can include
  wildcards.

- contactstatus:

  The current status of the contact. Possible values include: active,
  deceased, defunct, extant, inactive, retired, unknown.

- familyname:

  A character string. Full or partial string indicating the contact's
  last name.

## Value

The function takes parameters defined by the user and returns a list of
contact information supplied by the Neotoma Paleoecological Database.
The user may define all or none of the possible fields. The function
contains data checks for each defined parameter.

The function returns either a single item of class `"try-error"`
describing the reason for failure (either mis-defined parameters or an
error from the Neotoma API), or a table of contacts, with rows
corresponding to the number of individual contacts returned by the
Neotoma API. Each row entry includes the following parameters:

- `contact.name` :

  Full name of the person, last name first (e.g.
  `"Simpson, George Gaylord"`) or name of organization or project (e.g.
  `"Great Plains Flora Association"`).

- `contact.status` :

  Current status of the person, organization, or project. Field links to
  the ContactStatuses lookup table.

- `family.name` :

  Family or surname name of a person.

- `leading.initials` :

  Leading initials for given or forenames without spaces (e.g.
  `"G.G."`).

- `given.names` :

  Given or forenames of a person (e.g. `"George Gaylord"`). Initials
  with spaces are used if full given names are not known (e.g.
  `"G. G")`.

- `suffix` :

  Suffix of a person's name (e.g. `"Jr."`, `"III"`).

- `title` :

  A person's title (e.g. `"Dr."`, `"Prof."`, `"Prof. Dr"`).

- `phone` :

  Telephone number.

- `fax` :

  Fax number.

- `email` :

  Email address.

- `url` :

  Universal Resource Locator, an Internet World Wide Web address.

- `address` :

  Full mailing address.

- `notes` :

  Free form notes or comments about the person, organization, or
  project.

- `contact.id` :

  Unique database record identifier for the contact.

- `alias.id` :

  The ContactID of a person's current name. If the AliasID is different
  from the ContactID, the ContactID refers to the person's former name.

## References

Neotoma Project Website: http://www.neotomadb.org API Reference:
http://wnapi.neotomadb.org/doc/resources/contacts

## Author

Simon J. Goring <simon.j.goring@gmail.com>

## Examples

``` r
if (FALSE) { # \dontrun{
#  To find all data contributors who are active:
active.cont <- get_contact(contactstatus = 'active')

# To find all data contributors who have the last name "Smith"
smith.cont <- get_contact(familyname = 'Smith')
} # }
```
