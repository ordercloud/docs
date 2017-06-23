# Global Products

Global products also known as library products are the product definitions for a franchise or group of stores that all have the same inventory or menu.
For example a restaurant chain that has the same menu in every store can simply import this menu from the dead office's global products.

## Creating global products
The API call to create a new product can be found [here](https://docs.ordercloud.com/#!/productlibraryproducts/createProductLibraryItem).

Note that products are unique by name and organisation so trying to create a product with the same name will result in a conflict.

## Viewing global products
Global products can be viewed either as a list of all products or a single product can be retreived by id.

The API call to view the list of products are [here](https://docs.ordercloud.com/#!/productlibraryproducts/findAllForOrganisation) and to view a single global product is [here](https://docs.ordercloud.com/#!/productlibraryproducts/findProductLibraryItem).

## Updating global products
The API call to update product can be found [here](https://docs.ordercloud.com/#!/productlibraryproducts/updateProductLibraryItem).

## Disabling a global product
Global products can be disabled. Disabled products are not searched for by default and will not be imported to another orgnisations list of products.
The API call to disable a global product can be found [here](https://docs.ordercloud.com/#!/productlibraryproducts/disableProductLibraryItem).

## Enabling a global product
Once a global product is disabled it can be re-enabled. This means it will once again function as before.
The API call to enable a global product can be found [here](https://docs.ordercloud.com/#!/productlibraryproducts/enableProductLibraryItem).
