# Introduction
Assure Magic provides a set of APIs which help any external system(channel) to integrate with Assure Fulfillment Platform like:
- ERP
- E-commerce portal
## Setting Up
- Go through the documentation of Assure Magic 
- Mail to assure.support@increff.com for exchange of credentials 
- Implement required APIs at your end
- Test your APIs in staging environment
- Once APIs are developed and tested, please repeat the above process to go live in the production system

### Protocols
REST Synchronous calls 

### Format
JSON format

### API Invocation

Following headers need to be provided (unless otherwise stated). The credentials will be provided to you upon request.
- authUsername 
- authPassword 
- Content-Type: application/json

## Staging Environment Url
https://staging-oltp.increff.com/assure-magic2

### HTTP Status Codes and Bodies

Both end points must use only following HTTP Status Codes
- 200: In case of success 
- 400: In case of bad request data
- 401: In case of authentication / authorization failure
- 404: In case of URL does not exist
- 500: In case of an Internal Server Error

In case of a 400 or 500 error, following response body JSON should be used 

```javascript
{
   "errorMessage":"string"
}
```

# Inventory Interface API Reference 

## Update Inventory Count
Outbound | PUT | {Client’s URL}

### Summary
This API will push the inventory count to the channel.

### Description

This api will always send the inventory available for sale. The inventory will always be absolute.

Note : One batch will contain 200 skus .Frequency of this job is configurable in Assure.

### Request Body
```javascript
{
   "locationCode":"wd003",
   "inventories":[
      {
         "quantity":40,
         "channelSkuCode":"302"
      }
   ]
}
```
#### Request Desciption 

Parameter Name | Data Type | Description | Mandatory
---------------|-----------|-------------|---------
locationCode | String | Identifier for a warehouse in channel | Yes
inventories| Object[] | List of inventories to be updated | Yes
quantity | Integer | Absolute quantity available for sale sale in Assure | Yes
channelSkuCode | String | Code used by channel to identify an SKU | Yes


### Response Body
```json
{
   "failureList":[
      
   ],
   "successList":[
	"302"
   ]
}
```

`HttpStatus : 200`

