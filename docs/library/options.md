# Global Options
Global options also known as library options, are options that are available on a global product. Global options grouped together in sets and then mapped to a global product. Only one option of a set can be selected out of an options set.
E.g. the colour of a product will be a set and the available colours will be the options contained within the set.

Sets are unique per organisation and name. Options in a set are unique by name within that set.

## Creating a global option set
Details on the API call to create an global option set can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/createLibraryOptionSet).

Please note sets are uniqe per name for an organisation.

## Viewing a global option set
Global option sets can be viewed either as a list of all sets or a single set can be retreived by id.

The API call to view the list of option sets are [here](https://docs.ordercloud.com/#!/productlibraryoptions/findAllLibraryOptionSet) and to view a single global option set is [here](https://docs.ordercloud.com/#!/productlibraryoptions/findLibraryOptionSet).

## Updating a global option set
Details on the API call to update a global option set can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/updateLibraryOptionSet).

Uniqueness on name and organisation will still be enforced when trying to update the set name.

## Disabling a global option set
An global option set can be disabled. Disabled sets will not be retreived by default and will not be imported to another orgnisations products.
Details on the API call to disable a global option set can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/disableLibraryOptionSet).

## Enabling a global option set
Once a global option set is disabled it can be re-enabled. This means it will once again function as before.
The API call to enable a global option set can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/enableLibraryOptionSet).

## Copying a global option set
It is possible to copy a global option set and all it's linked options. This is usefull when creating an option set that has almost the exact same, but some options will be added, removed or updated, including different prices.
The API call to copy and global option set can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/copyLibraryOptionSet).

## Creating a global option
Details on the API call to create a new global option can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/createProductLibraryOption).

Upon creation the global option is linked to an global option set. Uniqueness of options are enforced upon the name of the option and the set whithin which it is contained.

## Viewing a global option
Global option can be viewed either as a list of all sets or a single option can be retreived by id.

The API call to view the list of options are [here](https://docs.ordercloud.com/#!/productlibraryoptions/findAllForOrganisation) and to view a single global option is [here](https://docs.ordercloud.com/#!/productlibraryoptions/findProductLibraryOption).

## Updating a global option
Details on the API call to update a global option set can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/updateProductLibraryOption).

Uniqueness of options are still enforced upon the name of the option and the set whithin which it is contained.

## Disabling a global option
An global option can be disabled. Disabled options will not be retreived by default when viewing an options set and will not be imported to another orgnisations products.
Details on the API call to disable a global option can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/disableProductLibraryOption).

## Enabling a global option
Once a global option is disabled it can be re-enabled. This means it will once again function as before.
The API call to enable a global option can be found [here](https://docs.ordercloud.com/#!/productlibraryoptions/enableProductLibraryOption).
