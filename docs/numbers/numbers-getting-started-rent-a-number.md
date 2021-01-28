---
title: Rent a virtual number
excerpt: 'Learn how to rent, search and configure a virtual number using the Sinch Numbers API.'
hidden: false
---


## Rent a virtual number in the US

To rent a virtual number you first need to find a number that suites the needs for your application.

### Search for a virtual number

Search for virtual numbers that are available for you to rent. In this example you will search for any virtual US number.

```shell
curl --request GET \
 --url 'https://numbers.api.sinch.com/v1alpha1/projects/{projectId}/availableNumbers?regionCode=US' \
 --header 'Accept: application/json' \
 -u {clientId}:{clientSecret}
```
Replace {projectId}, {clientId} and {clientSecret} with your values. 

You can filter by any property on the available virtual number resource. Learn more about it in the [API specification](https://developers.sinch.com/reference#numberservice_listavailablenumbers).  


#### Response

```json
{
  "availableNumbers": [
    {
      "phoneNumber": "+12089087284",
      "regionCode": "US",
      "type": "LOCAL",
      "capability": ["SMS"],
      "setupPrice": {
        "currencyCode": "USD",
        "amount": "0.00"
      },
      "monthlyPrice": {
        "currencyCode": "USD",
        "amount": "2.00"
      },
      "paymentIntervalMonths": 1
    }
  ]
}
```
Take a note of the phoneNumber you will need it in the next step. 

### Rent the virtual number

Rent a virtual number to use with SMS or Voice products

```shell
curl --request POST \
 --url https://numbers.api.sinch.com/v1alpha1/projects/projectId/availableNumbers/+12089087284:rent \
 --header 'Accept: application/json' \
 --u {clientId}:{clientSecret} 
```
Replace {projectId}, {clientId} and {clientSecret} with your values. 

#### Response

```json
{
  "phoneNumber": "+12092224786"
}
```

### Rent the virtual number and configure it for SMS

Rent a virtual number to use with SMS or Voice products

```shell
curl --request POST \
 --url https://numbers.api.sinch.com/v1alpha1/projects/projectId/availableNumbers/+12089087284:rent \
 --header 'Accept: application/json' \
 --u {clientId}:{clientSecret} 
 --d '{"smsConfiguration":{"servicePlanId":"sdfewe383408d"}}'
```
Replace {projectId}, {clientId} and {clientSecret}, and [servicePlanId](https://dashboard.sinch.com/sms/api) with your values.  

## Search for a virtual Toll free number.

As above, but add the virtual number type you are interested in.
```shell
curl --request GET \
 --url 'https://numbers.api.sinch.com/v1alpha1/projects/{projectId}/availableNumbers?regionCode=US&type=TOLL_FREE' \
 --header 'Accept: application/json' \
 -u {clientId}:{clientSecret}
```
