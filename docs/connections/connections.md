# Connections

## What are connections?

A connection is a relationship between two organisations defining how they interact with each other. This allows the sharing of information, price modification and management of certain responsibilities for the orther organisation.

## Connection Types

* **Delivery Service** (DS) - Allows provider to do delivery of orders
* **Marketplace** (M) - Allows connections to order products
* **Franchise** (F) - Allows franchisees to import product catalogue
* **POS (POS)** - Allows POS to manage online orders
* **Payment Gateway** (PG) - Allows the provider to process payments
* **Communication Provider** (CM) - Allows provider to send notifications
* **Courier Service** (CS) - Allows provider to courier orders
* **Child** (CH) - Allows to import product catalogue
* **Chain Store** (C) - Allows oversight of orders
* **Reseller** (R) - Allows to resell product catalogue
* **Inventory Manager** (IM) - Allows to manage product catalogue
* **Order Manager** (OM) - Allows to manage orders
* **Call Centre** (CC) - Allows callcentre to manage and place orders

Connection Types can be viewed through the API [here](https://docs.ordercloud.com/#!/connections/findConnectionTypes).

## Connecting to another organisation

Before two organisation can work with each other they need to connect and define their relationship with connection types.

### Requesting a organisation to connect

When a connection is required between two organisation a request can be made with [this](https://docs.ordercloud.com/#!/organisations/createOrganisationConnection) call.

A connection can only be made once for a organisaiton pair per connection type. A new connection needs to be created for every additional connnection type.

One thing to note is that the connectionType paramter takes the connection type:

```
    "typeCode": "M" //marketplace
    "toOrganisationId" : xx // target organisation id
```

### Creating an connecting an organisation

When creating a new organisation connections can be passed to be made when it is created. The create organisation [call](https://docs.ordercloud.com/#!/organisations/createOrganisation) is used.

The connection needed is passed through with create organisation call:

```
"connectionTypeCode": [
   "M", //marketplace
   "OM" //Order Manager
 ],

```

?> Connections created this way do not need to be accepted by other party


### Allowed connections

To view which organisation can be connectected to use this [call](https://docs.ordercloud.com/#!/connections/listPossibleConnectionsToMake)


### Viewing pending connections

Pending connections for an organisaiton can be viewed by making a call to [view connections](https://docs.ordercloud.com/#!/organisations/findConnectionByOrganisation) and passing in the status filter in.

```
GET /organisations/{organisationId}/connections?status=PENDING

```

?> Pending connections can also be filtered by type by appending a connection type filter

!> Do note that pending connections uses paging

### Accepting a Connection

A connection can be accepted by using [this](https://docs.ordercloud.com/#!/connections/organisationAcceptConnection) call wiht the organisation and connection ID

?> Once a connection is accepted it will appear under the connected organisations.

!> The requesting party cannot accept a connection they requested

### Declining a Connection

A connection can be accepted by using [this](https://docs.ordercloud.com/#!/connections/organisationDeclineConnection) call wiht the organisation and connection ID

!> The requesting party cannot decline a connection they requested


### Viewing connected organisations

Connections for an organisaiton can be viewed by making a call to [view connections](https://docs.ordercloud.com/#!/organisations/findConnectionByOrganisation) and passing the connected status.

```
GET /organisations/{organisationId}/connections?status=CONNECTED

```

?> Connection can be viewed by radius from a point by passing radius, lat and long or by filtered by industry by passing the correct parametes [see](https://docs.ordercloud.com/#!/organisations/findConnectionByOrganisation) for more details


### Disable a connection

A connection can be disabled with this [call](https://docs.ordercloud.com/#!/connections/disableConnection)

Disabled Connections for an organisaiton can be viewed by making a call to [view connections](https://docs.ordercloud.com/#!/organisations/findConnectionByOrganisation) and the showDisabled parameter.

```
GET /organisations/{organisationId}/connections?status=CONNECTED&showDisabled=true
```

### Enable a connection

A connection can be enabel with this [call](https://docs.ordercloud.com/#!/connections/enableConnection)

Enabled Connections for an organisaiton can be viewed by making a call to [view connections](https://docs.ordercloud.com/#!/organisations/findConnectionByOrganisation) and the showDisabled parameter.

```
GET /organisations/{organisationId}/connections?status=CONNECTED&showDisabled=false
```

https://docs.ordercloud.com/#!/connections/enableConnection
## Setting
