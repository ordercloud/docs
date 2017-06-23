# Delivery

## Delivery Types

### Self Pickup

```
    "deliveryType": "SELFPICKUP",
```

When a customer places an order and collects it themselves. Sometimes referred to as "Click and Collect".

<aside class="info">
No user address(Geo) is required when placing he order.
</aside>

The deliveryType can be set  when creating the [order](https://docs.ordercloud.com/#!/orders/CreateOrders)


### Instore

```
    "deliveryType": "INSTORE",
```

When a customer places an order and it is fullfilled within the store. Examples are ordering digitally from the table.

<aside class="info">
No user address(Geo) is required when placing he order.
</aside>

The deliveryType can be set  when creating the [order](https://docs.ordercloud.com/#!/orders/CreateOrders)



### Inhouse Delivery

```
    "deliveryType": "DELIVERY",
    "userGeo": {
      "id": 123456789
    },
    "delivery": {
      "external": false,
    },
    "deliveryCost": 50,
```


When a customer places an order and would like it delivered to a location.

<aside class="warning">
    A user address(Geo) that is allready in the system is required.
</aside>

The deliveryType can be set  when creating the [order](https://docs.ordercloud.com/#!/orders/CreateOrders)

To configure the system to allow this type of deliveries, it needs to be set in the console or by using the following api [call](### Enable Inhouse Deliveries)



### Outsourced Delivery

```
    "deliveryType": "DELIVERY",
    "userGeo": {
      "id": 123456789
    },
    "delivery": {
      "external": true,
      "organisation" : {
          "id" : 12345621 // delivery provider organisation id
      }
    },
    "deliveryCost": 33,
```

This is used when a customer want the order delivery to a specific address. And the marketplace uses third party delivery services.

<aside class="warning">
    A user address(Geo) that is allready in the system needs to be sent along .
</aside>

The deliveryType can be set  when creating the [order](https://docs.ordercloud.com/#!/orders/CreateOrders)

## Inhouse Delivery

### Enable Inhouse Deliveries

```
{
  "value": "true",
  "key": {
    "name": "org_self_deliver"
  }
}

```

To set that a organisation does its own deliveries a call to [update settings]() can be made.

Current setting can be [viewed](https://docs.ordercloud.com/#!/organisations/getOrganisationSettingsForTag_0) with the following body.

### Delivery Costs

```
[
  {
    "value": "5",
    "key": {
      "name": "delivery_fee_flat"
    }
  },
  {
    "value": "1.5",
    "key": {
      "name": "delivery_fee_per_km"
    }
  }
]
```

Delivery cost for Internal Deliveries can be set by [calling](https://docs.ordercloud.com/#!/organisations/addOrganisationSettingInBulk_0)

If just a flat fee is charged the delivery_fee_per_km can be left out. The same goes for if just a per KM fee is charged the delivery_fee_flat can be left out.

The delivery fee is calculated like the following: delivery_fee_flat + delivery_fee_per_km x distance of delivery.



### Assign a Delivery Agent

A delivery agent can be assigned to the order with the [assign delivery agent call](https://docs.ordercloud.com/#!/orders/assignDeliveryAgentToOrder).

### Delivery Range

Delivery range can be [viewed](https://docs.ordercloud.com/#!/organisations/getDeliveryAreas) , [added](https://docs.ordercloud.com/#!/organisations/createDeliveryArea) , [updated](https://docs.ordercloud.com/#!/organisations/updateDeliveryArea) or [removed](https://docs.ordercloud.com/#!/organisations/deleteDeliveryArea) for an organisation. The range is calculated based on a circle with a radius from the latitude and longitude specified. Multiple ranges can be added to an organisation.

<aside class="warning">
    If a user address(Geo) is specified that falls outside the range for an order. A error will return that delivery is not available.
</aside>


## Outsourced Deliveries

### Configure

### Enable Outsourced Deliveries

```
{
  "value": "false",
  "key": {
    "name": "org_self_deliver"
  },
}

```
To set that a organisation does not use its own deliveries a call to [update settings](https://docs.ordercloud.com/#!/organisations/addOrganisationSetting_0) can be made.

Current setting can be [viewed](https://docs.ordercloud.com/#!/organisations/getOrganisationSettingsForTag_0) with the following body.

<aside class="info">
    A delivery connection needs to be made in Ordercloud to the delivery company before external deliveries can be made.
</aside>


## Un-manged deliveries

```
{
  "value": "true",
  "key": {
    "name": "org_uses_external_delivery"
  }
}

```

If deliveries are done. But does not leverage Ordercloud for delivery functionality this can be used.

To set that a organisation does not use its own deliveries a call to [update settings](https://docs.ordercloud.com/#!/organisations/addOrganisationSetting_0) can be made.

Current setting can be [viewed](https://docs.ordercloud.com/#!/organisations/getOrganisationSettingsForTag_0) with the following body.


##Delivery Area


The delivery area defines the area in which the organisation can deliver orders too. More than one delivery area can be defined and are allowed to overlap. A organisation address is still required for the product owner to do deliveries , a delivery area does not overwrite this.


### Is delivery available

To check if delivery is available for a location make a call to [check delivery availability](https://docs.ordercloud.com/#!/organisations/getIsDeliveryAvailable)

<aside class="info">
    The organisation delivery area is determined from the X-Ordercloud-Ordercloud header
</aside>

### Creating a delivery area

```
{
    "latitude": "-34.090347",
    "longitude": "18.805951",
    "radius": 100 //'in meters
}
```

Before deliveries price estimates are allowed to be retrieved from the API. Available delivery areas need to be specified.

To create a  delivery area a call to [add delivery area](https://docs.ordercloud.com/#!/organisations/createDeliveryArea)

<aside class="info">
    More than one delivery area can be added
</aside>

### Viewing delivery areas

Currently configured delivery areas can be viewed by calling [view delivery areas](https://docs.ordercloud.com/#!/organisations/getDeliveryAreas)

### Updating a delivery area

```
{
    "latitude": "-34.090347",
    "longitude": "18.805951",
    "radius": 100 //'in meters
}
```

To update a  delivery area a call to [update delivery area](https://docs.ordercloud.com/#!/organisations/createDeliveryArea)


<aside class="info">
    Delivery areas can overlap
</aside>


### Remove a delivery area

To remove a  delivery area a call to [remove delivery area](https://docs.ordercloud.com/#!/organisations/deleteDeliveryArea)


##Estimating the delivery cost

```
[
  {
	"id": 1233432523145, //organisation for pickup
  }, {
	  "id": 98765432, //organisation for pickup
  }
]
```

<aside class="warning">
    Delivery areas need to be set for the delivery organisation.
</aside>

The delivery cost for an order can be [estimated by passing](https://docs.ordercloud.com/#!/orders/estimateDeliveryCost) the delivery location (geo) along with all the locations of pickup points for the order.

If a organisation does [un-manged deliveries](orders/delivery.md#un-manged-deliveries) . It still has to set available [delivery area](orders/delivery.md#delivery-area) to use the estimate functionality.

### Common Error messages
 Code       | Error           | Message | Reason
-------     |     ---------   |    -----|----
400| no_waypoint_address | No organisations with valid addresses found for calculation | One of the organisation that was passed in the body does not have a address specified. The address is required to be used as a start point or waypoint on route to the users address.
400| delivery_not_available |Delivery not available for user location | Users location falls outside all delivery areas for the delivery organisation passed in the url

##Delivery Time

###Default delivery time

```
{
  "value": "10", //in minutes
  "key": {
    "name": "estimated_delivery_time"
  }
}

```
To set that a organisation does not use its own deliveries a call to [update settings](https://docs.ordercloud.com/#!/organisations/addOrganisationSetting_0) can be made.

Current setting can be [viewed](https://docs.ordercloud.com/#!/organisations/getOrganisationSettingsForTag_0) with the following body.



###Estimated delivery time

The estimated delivery time can be found by passing the order to the [delivery estimate call](https://docs.ordercloud.com/#!/orders/getOrderDeliveryEstimateTime)
