# Instructions

Debemos enviar (por post) una orden de compra

1. Cambiar el campo `orderId` de [Purchase Order Example](#Purchase-Order-Example) y mandamos la peticion por post a un [servicio](#Service-to-add-purchase-orders) del `svl-backend-for-frontend` que se encarga de guardar la order.
2. Vamos a la base de datos y cambiamos el estado de la order a "readyForPacking".
   1. `Ir a robo3t`.
   2. `test`->`collections`->`orders`->`document` where (externalId:orderId)
   3. Cambiar el campo "deliveryState" que deberia estar en "awaitingRequest" y lo cambiamos por readyForPacking.
3. Ir al front y accedemos a la order.
   1. `Logistica`->`Gestion de pedidos`.
   2. Filtramos la order de compra filtrando por numero de solicitud (orderId que enviamos por postman.
   3. Deberiamos ver la order correspondiente.
   4. Click en `imprimir etiquetas`.
4. Ahora en la nueva vista, tenemos una seccion que dice detalle de pedido.
   - Example:
   ```bash
   Unidades: 10
   SKU Seller: 9727605092
   SKU Sodimac: 222
   ```
5. Ingresar un numero en el campo N° Guía de Despacho o Factura Electrónica.
6. Luego agregamos un producto. La cantidad debe ser la misma que figura en el campo unidades de la seccion detalle del pedido.
7. Ya podriamos dar en continuar y si esta todo correcto la orden deberia ser ingresada y preparada correctamente. En caso de hacerlo, cuando volvamos a la gestion de ordenes de compra y buscamos la orden anterior la accion deberia decir "lista para entregar"

## JSON Response - Postman

```js
{
    "message": {
        "errno": "ENOTFOUND",
        "code": "ENOTFOUND",
        "syscall": "getaddrinfo",
        "hostname": "logistics-topic-event-grid-endpoint.com",
        "host": "logistics-topic-event-grid-endpoint.com",
        "port": 443
    }
}
```

## Service to add purchase orders

`{{bff}}/api/v1/sodimac/purchase_orders`

## Purchase Order Example

```js
{
   "header" : {
      "channel" : "ODBMS",
      "commerce" : "Sodimac",
      "country" : "CL",
      "datetime" : "2019-01-14T15:40:14.202",
      "entityType" : "purchaseOrder",
      "messageId" : "6596a137-932e-4559-b480-da92402bbd8f",
      "mimeType" : "application/json",
      "timestamp" : "1547491214202",
      "version" : "1.0"
   },
   "metadata" : {
      "products" : [ {
         "actualCost" : "NO DATA",
         "commodityCode" : "6521903861627",
         "diameter" : "NO DATA",
         "height" : "NO DATA",
         "length" : "NO DATA",
         "originalBudgetedCost" : "NO DATA",
         "quantity" : {
            "orderQty" : "10"
         },
         "sku" : "222",
         "totalMonetaryValue" : "669240",
         "unNumber" : "9727605092",
         "unitMonetaryValue" : "66924",
         "unitTaxAmount" : "NO DATA",
         "width" : "NO DATA"
      } ],
      "budgetedCost" : "0",
      "businessPartnerCode" : "0",
      "businessUnit" : "1",
      "companyId" : "1",
      "declaredValue" : "956355",
      "destinationAddress" : "Eduado Frei Montalva  # 3092",
      "destinationAddress2" : "Santiago",
      "destinationAddress3" : "",
      "destinationCity" : "Santiago",
      "destinationCountry" : "CL",
      "destinationFacilityAliasId" : "20",
      "destinationFacilityName" : "NO ESTA",
      "destinationStateProv" : "",
      "dispatchType" : "cross_docking_to_delivery_center",
      "isCancelled" : "False",
      "isClosed" : "False",
      "monetaryValue" : "803660",
      "mvCurrencyCode" : "CLP",
      "orderCancelDate" : "04/03/2019 00:00",
      "orderCreatedDate" : "13/02/2019 00:00",
      "orderExpectedDate" : "27/02/2019 00:00",
      "orderId" : "3333999",
      "orderStatus" : "4",
      "sellType": "POVEV",
      "originFacilityAliasId" : "214",
      "originFacilityName" : "NO ESTA",
      "referenceField3" : "MarketPlace DESP Sodimac",
      "returnMiscellaneousNumber" : "152695"
   }
}
```
