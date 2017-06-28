# Product Sorting

Sorting products works by adding query parametes to the get calls for the products.


For example . Sorting the products by name Alphabetically looks like the following.

```
?sortProduct=name+
```

?> The + (Assending) or - (Descending) after the sort parameter defines which direction the sort is done.

## Position

If a custom sorting order is required a position can be set on the Products or Tags through a update.

The field is called position and takes an integer value and duplicates are allowed.

!> If not position is not set. Records will appear below the positioned ones in random order.

### Product

The product postion can be updated [here](https://docs.ordercloud.com/#!/product/updateProduct).

Example of field

```
...
 "position" : 1
...
```

Example of sorting
```
?sortProduct=position+
```

?> The + (Assending) or - (Descending) after the sort parameter defines which direction the sort is done.

### Tag

The product postion can be updated [here](https://docs.ordercloud.com/#!/producttag/updateTag).

Example of field

```
...
 "position" : 1
...
```

Example of sorting
```
?sortTag=position+
```

?> The + (Assending) or - (Descending) after the sort parameter defines which direction the sort is done.


## By Tag and Product

 Products can be sorted when using  [this](https://docs.ordercloud.com/#!/product/findByOrganisationGroupByTag) call. Product tags will be first sorted then products belonging to the tag.

 Example

 ```
 ?sortTag=name+&sortProduct=position+
 ```
