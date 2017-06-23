# Orders

## Create Order

To create a order the items of the order

Totals sent need to match the expected total.

To create a [order](https://docs.ordercloud.com/#!/orders/CreateOrders)


See [Available Delivery Methods](orders/delivery.md#delivery-types)

### Order for pickup by client

See [Pickup](delivery.md#self-pickup)

### Order for delivery

See [Inhouse Delivery](orders/delivery.md#inhouse-delivery)
See [External Delivery](orders/delivery.md#external-delivery)

### Order for in-store customer

See [In-store](orders/delivery.md##instore)

## Payments

### Unpaid Orders

A order is first made before a payment is attached. This allows a payment to be reprocessed or a different payment method to be tried without having to replace the order. A order without a payment will remain in new status and only progess to pending once a payment is attached. To create a order that is paid externall use [Paid Order](## Create Paid Order)

To create a [unpaid order](https://docs.ordercloud.com/#!/orders/CreateOrders)

### Payment Types

* [Cash On Delivery (COD)](https://docs.ordercloud.com/#!/orders/payViaCOD)

* [Credit Card (CC)](https://docs.ordercloud.com/#!/orders/payViaCreditCard)

* [Stored Credit Card (CC)](https://docs.ordercloud.com/#!/orders/payViaCreditCard)

* [Loyalty](https://docs.ordercloud.com/#!/orders/payViaExternalMethod)

* [External Payment](https://docs.ordercloud.com/#!/orders/payViaExternalMethod)
    An external payment is one that does not pass through Ordercloud. It is used to keep track of the payment.
    * External Credit Card
    * External COD
    * External Payment

### Paying An Order

To pay a order use one of the [payment types](#payment-types) and the order ID.


## Create Paid Order

To create a [paid order](https://docs.ordercloud.com/#!/orders/CreateOrders)



## Discounts

Discounts can be sent through along with the order at creation to change the order item total or order item price that is expected by the api.

To enable an organisation to allow discounts on order creation it needs to be activated in the settings.

#### Order Discount Setting

```
{
  "value": "true",
  "key": {
    "name": "org_allow_dsicounts"
  }
}

```

To set that a organisation does its own deliveries a call to [update settings]() can be made.

Current setting can be [viewed](https://docs.ordercloud.com/#!/organisations/getOrganisationSettingsForTag_0) with the following body.


### Order Discounts

```
{
  "orderDiscount": {
    "amount": 20,
    "description": "description for the discount",
  }
}

```

Order discount is passed as the amount of the order total to discount. This is a value and not a percentage. The order total passed should also reflect the discount amount.




### Order Item

```
{
"items"{
   ....
  "itemDiscount": {
      "amount": 20, //ammount of discount on the order total. This is nog a percentage
      "description": "description for the discount",
  }
  ....
  }
}
```


Order Item discount is passed as the ammount of the order item total to discount. This is a value and not a percentage. The order total passed should have the  each order item discount subtracted from it.

## View Order

## View Orders

## Modify Order



* Add Order Item Option; View Order Item Option
