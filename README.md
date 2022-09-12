BNI API SDK - PHP
===============
This is the Official PHP client / library for BNI API. 
Please visit [Digital Services](https://digitalservices.bni.co.id/en/) for more information about our product and visit our documentation page at [API Documentation](https://digitalservices.bni.co.id/documentation/public/en) for more technical details.

## 1. Installation

### 1.1 Using COMPOSER

```
composer require bni/sdk --dev //contoh
```

### 1.2 Manual Installation

If you are not using GIT, you can clone or [download](https://github.com/bni-api/bni-php.git) this repository.


## 2. Usage
  
### 2.1 Choose an API Product

We have 2 API products you can use:
- [One Gate Payment](#22A-snap) - A solution for a company to integrate its application / system with banking transaction services. [documentation](https://digitalservices.bni.co.id/en/api-one-gate-payment)
- [Snap BI](https://apidevportal.bi.go.id/snap/info) - Integrate with SNAP BI [documentation](https://apidevportal.bi.go.id/snap/api-services)


### 2.2 Client Initialization and Configuration

Get your client key and server key from [Menu - Applications](https://digitalservices.bni.co.id/en/profile-menu/apps)
Create API client object

```javascript
  // Create Core API instance
  public $prod;
    public $appName;
    public $clientId;
    public $clientSecret;
    public $apiKey;
    public $apiSecret;});
```

### 2.2.A One Gate Payment

Create `One Gate Payment` class object
```javascript



// Create Client instance
const client = new BNIClient({
  prod: false,
  clientId: '{your-client-id}',
  clientSecret: '{your-client-secret}',
  apiKey: '{your-api-key}',
  apiSecret: '{your-api-secret}',
  appName: '{your-app-name}'
});

const ogp = new OneGatePayment(client);
```

Available methods for `One Gate Payment` class
#### Get Balance
```javascript
// return as Promise of Object
https://{BNIServer}:{port}/H2H/v2/getbalance?access_token=(Your_token)
{	
"clientId" : "IDBNI" + BASE64(clientName),
"signature" :"[SIGNATURE]",
"accountNo" : "115471119"
}
```

#### Get In House Inquiry
```javascript
// return as Promise of Object
https://{BNIServer}:{port}/H2H/v2/getinhouseinquiry?access_token=(Your_token)
{   
"clientId" : "IDBNI" + BASE64(clientName),
"signature" :"[SIGNATURE]",
"accountNo" : "115471119"
}
```

#### Do Payment
```javascript
// return as Promise of Object
https://{BNIServer}:{port}/H2H/v2/dopayment?access_token=(your_token)
{      
"clientId" : "IDBNI" + BASE64(clientName),
"signature" : "[SIGNATURE]",
"customerReferenceNumber" : "20170227000000000020",
"paymentMethod" : "0",
"debitAccountNo" : "113183203",
"creditAccountNo" : "115471119",
"valueDate" : "20170227000000000",
"valueCurrency" : "IDR",
"valueAmount" : "100500",
"remark" : "?",
"beneficiaryEmailAddress":"",
"beneficiaryName":"Mr.X",
"beneficiaryAddress1":"Jakarta",
"beneficiaryAddress2":"",
"destinationBankCode":"CENAIDJAXXX",
"chargingModelId":"OUR" 
}
```

#### Get Payment Status
```javascript
// return as Promise of Object
https://{BNIServer}:{port}/H2H/v2/getpaymentstatus?access_token=(Your_token)
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "[SIGNATURE]",
"customerReferenceNumber": "20170227000000000020"
}
```

#### Get Inter Bank Inquiry
```javascript
https://{BNIServer}:{port}/H2H/v2/getinterbankinquiry?access_token=(your_token)
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "[SIGNATURE]",
"customerReferenceNumber": "20170227000000000021",
"accountNum": "113183203",
"destinationBankCode": "014",
"destinationAccountNum": "3333333333"
}
```

#### Get Inter Bank Payment
```javascript
https://{BNIServer}:{port}/H2H/v2/getinterbankpayment?access_token=(your_token)
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "[SIGNATURE]",
"customerReferenceNumber": "20170227000000000021",
"amount": "10000",
"destinationAccountNum": "3333333333",
"destinationAccountName": "BENEFICIARY NAME 1 UNTIL HERE1BENEFICIARY NAME 2(OPT) UNTIL HERE2",
"destinationBankCode": "014",
"destinationBankName": "BCA",
"accountNum": "115471119",
"retrievalReffNum": "100000000024"
}
```

#### Hold Amount
```javascript
// return as Promise of Object
https://{BNIServer}:{port}/H2H/v2/holdamount?access_token=(your_token)
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "[SIGNATURE]",
"customerReferenceNumber": "20170227000000000021",
"amount": "10000",
"destinationAccountNum": "3333333333",
"destinationAccountName": "BENEFICIARY NAME 1 UNTIL HERE1BENEFICIARY NAME 2(OPT) UNTIL HERE2",
"destinationBankCode": "014",
"destinationBankName": "BCA",
"accountNum": "115471119",
"retrievalReffNum": "100000000024"
}
```

#### Hold Amount Release
```javascript
https://{BNIServer}:{port}/H2H/v2/holdamountrelease?access_token=(your_token)
{
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "M4+FEsYOQluwIldqTqRti6oK3EhtGcTtrQZVtNrNZHxGz71kzXBoRCVgGuT8rq/jSE7c/sUXnSl/lqOPSvechI6HX1RpatHudd5mmLe2kcX38a2jg3L46dDuKC92cVrRmuPdvpOIH24J/gsNjrHHsgN3eEq8tmwKxQhgTkoZ4+Y=",
"customerReferenceNumber": "20170504153218298",
"amount": 12007,
"accountNo": "0115476151",
"bankReference": "513668",
"holdTransactionDate": "31052010"
}
```

### 2.2.B Snap BI

Create `One Gate Payment` class object
```javascript
// Create Client instance
{
X-SIGNATURE: (your_signature)
X-TIMESTAMP: (timedate_
X-CLIENT-KEY: (your_clientkey)
{
 "grantType": "client_credentials",
 "additionalInfo": {}
}
}
```

Available methods for `Snap BI` class
#### Balance Inquiry
```javascript
// return as Promise of Object
 "partnerReferenceNo": "(partnerReferenceNo)",
 "accountNo": "(accountnumber)"
}
});
```

#### Bank Statement
```javascript
// return as Promise of Object
{
 "partnerReferenceNo": "(partnerReferenceNo)",
 "accountNo": "(accountNo)",
 "fromDateTime": "(datetime)",
 "toDateTime": "(dataetime)"
}
});
```

#### Internal Account Inquiry
```javascript
// return as Promise of Object
 "partnerReferenceNo": "(partnerReferenceNo)",
 "beneficiaryAccountNo": "(beneficiaryAccountNo)"
});
```

#### Transaction Status Inquiry
```javascript
// return as Promise of Object
{
{
"originalPartnerReferenceNo": "(originalPartnerReferenceNo)",
 "originalReferenceNo": "(originalReferenceNo)",
 "originalExternalId": "(originalExternalId)",
 "serviceCode": "(serviceCode)",
 "transactionDate": "",
 "amount": {
 "value": "(value)",
 "currency": "IDR",
 },
 "additionalInfo": {
 "deviceId": "(iddevice",
 "channel": "mobilephone"
 }
}
```

#### Transfer Intra Bank
```javascript
// return as Promise of Object
{
 "partnerReferenceNo": "(partnerReferenceNo)",
 "amount": {
 "value": "(value)",
 "currency": "IDR"
 },
 "beneficiaryAccountNo": "(beneficiaryAccountNo)",
 "beneficiaryEmail": "",
 "currency": "IDR",
 "customerReference": "14045",
 "feeType": "",
 "remark": "Already One Year",
 "sourceAccountNo": "(sourceAccountNo)",
 "transactionDate": "(date)",
 "additionalInfo": {
 "deviceId": "(iddevice)",
 "channel": "mobilephone"
 }
}

```

#### Transfer RTGS
```javascript
// return as Promise of Object
const transferRTGS = await snap.transferRTGS{
 "partnerReferenceNo": "202201911020300011",
 "amount": {
 "value": "150005001",
 "currency": "IDR"
 },
 "beneficiaryAccountName": "(accountname)",
 "beneficiaryAccountNo": "(accountno)",
 "beneficiaryAddress": "(Andress)",
 "beneficiaryBankCode": "(bankcode)",
 "beneficiaryBankName": "(bankname)",
 "beneficiaryCustomerResidence": "1",
 "beneficiaryCustomerType": "1",
 "beneficiaryEmail": "",
 "currency": "IDR",
 "customerReference": "(customerReference)",
 "feeType": "OUR",
 "kodepos": "(poscode)",
 "recieverPhone": "",
 "remark": "Already One Year",
 "senderCustomerResidence": "1",
 "senderCustomerType": "1",
 "senderPhone": "",
 "sourceAccountNo": "(sourceAccountNo)",
 "transactionDate": "(transactionDate)",
 "additionalInfo": {
 "deviceId": "(iddevice)",
 "channel": "mobilephone"
 }
}

```

#### Transfer SKNBI
```javascript
// return as Promise of Object
const transferSKNBI = await snap.transferSKNBI{
 "partnerReferenceNo": "(partnerReferenceNo)",
 "amount": {
 "value": "(value)",
 "currency": "IDR"
 },
 "beneficiaryAccountName": "(accountname",
 "beneficiaryAccountNo": "(acccountno)",
 "beneficiaryAddress": "(address)",
 "beneficiaryBankCode": "(bankcode)",
 "beneficiaryBankName": "(bankname)",
 "beneficiaryCustomerResidence": "1",
 "beneficiaryCustomerType": "1",
 "beneficiaryEmail": "",
 "currency": "IDR",
 "customerReference": "(customerReference)",
 "feeType": "OUR",
 "kodepos": "(poscode)",
 "recieverPhone": "",
 "remark": "Already One Year",
 "senderCustomerResidence": "1",
 "senderCustomerType": "1",
 "senderPhone": "",
 "sourceAccountNo": "(sourceAccountNo)"
 "transactionDate": "(transactionDate)",
 "additionalInfo": {
 "deviceId": "(iddevice)",
 "channel": "mobilephone"
 }
}
```

#### External Account Inquiry
```javascript
// return as Promise of Object
const externalAccountInquiry = await snap.externalAccountInquiry({
  beneficiaryBankCode: '002',
  beneficiaryAccountNo: '888801000157508',
  partnerReferenceNo: '2020102900000000000001', // optional
  additionalInfo: {
    deviceId: '123456', // optinal
    channel: 'mobilephone' // optinal
  }
});
```

#### Transfer Inter Bank
```javascript
// return as Promise of Object
{
 "partnerReferenceNo": "(partnerReferenceNo)",
 "amount": {
 "value": "(value)",
 "currency": "IDR"
 },
 "beneficiaryAccountName": "(AccountName)",
 "beneficiaryAccountNo": "(AccountNo)",
 "beneficiaryAddress": "(Address)",
 "beneficiaryBankCode": "(bankcode)",
 "beneficiaryBankName": "(bankname)",
 "beneficiaryEmail": "(email)",
 "currency": "IDR",
 "customerReference": "(customerReference)",
 "sourceAccountNo": "(sourceAccountNo)",
 "transactionDate": "(transactionDate)",
 "feeType": "OUR",
 "additionalInfo": {
 "deviceId": "(iddevice)
 "channel": "mobilephone"
 }
}

```

## Get help

* [Digital Services](https://digitalservices.bni.co.id/en/)
* [API documentation](https://digitalservices.bni.co.id/documentation/public/en)
* [Stackoverflow](https://stackoverflow.com/users/19817167/bni-api-management)
* Can't find answer you looking for? email to [apisupport@bni.co.id](mailto:apisupport@bni.co.id)
