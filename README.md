BNI API SDK - Node.js
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
const { BNIClient } = require('bni-nodejs');
// Create Core API instance
const client = new BNIClient({
  prod: false,
  clientId: '{your-client-id}',
  clientSecret: '{your-client-secret}',
  apiKey: '{your-api-key}',
  apiSecret: '{your-api-secret}',
  appName: '{your-app-name}'
});
```

### 2.2.A One Gate Payment

Create `One Gate Payment` class object
```javascript

const { BNIClient, OneGatePayment } = require('bni-nodejs');

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

const { BNIClient, SnapBI } = require('bni-nodejs');

// Create Client instance
const client = new BNIClient({
  prod: false,
  clientId: '{your-client-id}',
  clientSecret: '{your-client-secret}',
  apiKey: '{your-api-key}',
  apiSecret: '{your-api-secret}',
  appName: '{your-app-name}'
});

const snap = new SnapBI(client, { 
  privateKeyPath: '{your-rsa-private-key-path}', 
  channelId: '{your-channel-id}' 
});
```

Available methods for `Snap BI` class
#### Balance Inquiry
```javascript
// return as Promise of Object
const balanceInquiry = await snap.balanceInquiry({
  partnerReferenceNo: '202010290000000000002', // optional
  accountNo: '0115476117'
});
```

#### Bank Statement
```javascript
// return as Promise of Object
const bankStatement = await snap.bankStatement({
  partnerReferenceNo: '202010290000000000002', // optional
  accountNo: '0115476117',
  fromDateTime: '2010-01-01T12:08:56+07:00', // optional
  toDateTime: '2011-01-01T12:08:56+07:00' // optional
});
```

#### Internal Account Inquiry
```javascript
// return as Promise of Object
const internalAccountInquiry = await snap.internalAccountInquiry({
  partnerReferenceNo: '2020102900000000000001', // optional
  beneficiaryAccountNo: '0115476151'
});
```

#### Transaction Status Inquiry
```javascript
// return as Promise of Object
const transactionStatusInquiry = await snap.transactionStatusInquiry({
  originalPartnerReferenceNo: '20211213100434', // optional
  originalReferenceNo: '20211220141520', // transaction reference number
  originalExternalId: '20211220141520', // optional
  serviceCode: '36', // SNAP BI service code
  transactionDate: '2021-12-20',
  amount: {
    value: '12500',
    currency: 'IDR'
  },
  additionalInfo: {
    deviceId: '123456', // optinal
    channel: 'mobilephone' // optinal
  }
});
```

#### Transfer Intra Bank
```javascript
// return as Promise of Object
const transferIntraBank = await snap.transferIntraBank({
  partnerReferenceNo: '202201911020300006', // transaction reference number
  amount: {
    value: '12500',
    currency: 'IDR'
  },
  beneficiaryAccountNo: '0115476117',
  beneficiaryEmail: 'mail@example.com', // optional
  currency: 'IDR', // optional
  customerReference: '14045', // optional
  feeType: 'OUR', // OUR: fee will be paid by sender (default), BEN: fee will be paid by beneficary, SHA: fee divided
  remark: '', // optional
  sourceAccountNo: '0115476151',
  transactionDate: '2021-12-13',
  additionalInfo: {
    deviceId: '123456', // optinal
    channel: 'mobilephone' // optinal
  }
});
```

#### Transfer RTGS
```javascript
// return as Promise of Object
const transferRTGS = await snap.transferRTGS({
  partnerReferenceNo: '202201911020300011', // transaction reference number
  amount: {
    value: '150005001',
    currency: 'IDR'
  },
  beneficiaryAccountName: 'SAN',
  beneficiaryAccountNo: '"3333333333',
  beneficiaryAccountAddress: 'Jakarta Barat', // optional
  beneficiaryBankCode: 'CENAIDJA',
  beneficiaryBankName: 'PT. BANK CENTRAL ASIA Tbk.', // optional
  beneficiaryCustomerResidence: '1',
  beneficiaryCustomerType: '1',
  beneficiaryEmail: 'mail@example.com', // optional
  currency: 'IDR', // optional
  customerReference: '202201911020300006',
  feeType: 'OUR', // OUR: fee will be paid by sender (default), BEN: fee will be paid by beneficary, SHA: fee divided
  kodePos: '12550', // optional
  recieverPhone: '08123456789', // optional
  remark: '', // optional
  senderCustomerResidence: '1', // optional
  senderCustomerType: '1', // optional
  senderPhone: '08123456789', // optional
  sourceAccountNo: '0115476151',
  transactionDate: '2022-01-25',
  additionalInfo: {
    deviceId: '123456', // optinal
    channel: 'mobilephone' // optinal
  }
});
```

#### Transfer SKNBI
```javascript
// return as Promise of Object
const transferSKNBI = await snap.transferSKNBI({
  partnerReferenceNo: '202201911020300012', // transaction reference number
  amount: {
    value: '150005001',
    currency: 'IDR'
  },
  beneficiaryAccountName: 'SAN',
  beneficiaryAccountNo: '3333333333',
  beneficiaryAddress: 'Jakarta Barat', // optional
  beneficiaryBankCode: '0140397',
  beneficiaryBankName: 'PT. BANK CENTRAL ASIA Tbk.', // optional
  beneficiaryCustomerResidence: '1',
  beneficiaryCustomerType: '1',
  beneficiaryEmail: 'mail@example.com', // optional
  currency: 'IDR', // optional
  customerReference: '202201911020300006',
  feeType: 'OUR', // OUR: fee will be paid by sender (default), BEN: fee will be paid by beneficary, SHA: fee divided
  kodePos: '12550', // optional
  recieverPhone: '08123456789', // optional
  remark: '', // optional
  senderCustomerResidence: '1', // optional
  senderCustomerType: '1', // optional
  senderPhone: '08123456789', // optional
  sourceAccountNo: '0115476151',
  transactionDate: '2022-01-25',
  additionalInfo: {
    deviceId: '123456', // optinal
    channel: 'mobilephone' // optinal
  }
});
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
const transferInterBank = await snap.transferInterBank({
  partnerReferenceNo: '2020102900000000000001', // transaction reference number
  amount: {
    value: '12345678',
    currency: 'IDR'
  },
  beneficiaryAccountName: 'Yories Yolanda',
  beneficiaryAccountNo: '888801000003301',
  beneficiaryAddress: 'Palembang', // optional
  beneficiaryBankCode: '002',
  beneficiaryBankName: 'Bank BRI', // optional
  beneficiaryEmail: 'mail@example.com', // optional
  currency: 'IDR', // optional
  customerReference: '10052019', // optional
  sourceAccountNo: '888801000157508',
  transactionDate: '2019-07-03T12:08:56+07:00',
  feeType: 'OUR', // OUR: fee will be paid by sender (default), BEN: fee will be paid by beneficary, SHA: fee divided
  additionalInfo: {
    deviceId: '123456', // optinal
    channel: 'mobilephone' // optinal
  }
});

```

## Get help

* [Digital Services](https://digitalservices.bni.co.id/en/)
* [API documentation](https://digitalservices.bni.co.id/documentation/public/en)
* [Stackoverflow](https://stackoverflow.com/users/19817167/bni-api-management)
* Can't find answer you looking for? email to [apisupport@bni.co.id](mailto:apisupport@bni.co.id)
