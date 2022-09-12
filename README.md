BNI API SDK - PHP
===============
This is the Official PHP client / library for BNI API. 
Please visit [Digital Services](https://digitalservices.bni.co.id/en/) for more information about our product and visit our documentation page at [API Documentation](https://digitalservices.bni.co.id/documentation/public/en) for more technical details.

## 1. Installation

### 1.1 Using COMPOSER
download Composer [download](https://getcomposer.org/download/) and run command line

```
composer require bni/sdk --dev 
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

```php
{
private function init()
    {
        return new Bni(
            false,
            'Test Wawat', <!-- appName -->
            '',<!-- apiSecret -->
            '',<!-- apiKey -->
            '',<!--  clientSecret -->
            ''<!--  clientId -->
        );
    }

}
```

### 2.2.A One Gate Payment

Create `One Gate Payment` class object
```php
{
private function init()
    {
        return new Bni(
            false,
            'Test Wawat', <!-- appName -->
            'ff19bcb7-3a15-4d0b-97b1-f36f9cf9bdb2',<!-- apiSecret -->
            'd227997a-3525-442d-b80e-2ab2e7d908f0',<!-- apiKey -->
            '98c4277f-866d-46b0-ba83-d3e0e37e667e',<!--  clientSecret -->
            'b3b58219-8a88-401f-89c0-f2dc5bb7ce21'<!--  clientId -->
        );
    }

}
```

Available methods for `One Gate Payment` class
#### Get Balance
```php
dd($bni->getToken());
        $ogp = new OneGatePayment($bni);
        return $ogp->getBalance('115471119');
        return $ogp->getInHouseInquiry('115471119');
        return $ogp->doPayment(
            '20170227000000000020',
            '0',
            '113183203',
            '115471119',
            '20170227000000000',
            'IDR',
            100500,
            '?',
            '',
            'Mr.X',
            'Jakarta',
            '',
            'CENAIDJAXXX',
            'OUR'
        );
```

#### Get In House Inquiry
```php
{   
"clientId" : "IDBNI" + BASE64(clientName),
"signature" :"[SIGNATURE]",
"accountNo" : "115471119"
}
```

#### Do Payment
```php
{      
"clientId" : "IDBNI" + BASE64(clientName),
"signature" : "[SIGNATURE]",
"customerReferenceNumber" : "(customerReferenceNumber)",
"paymentMethod" : "0",
"debitAccountNo" : "(debitAccountNo)",
"creditAccountNo" : "(creditAccountNo)",
"valueDate" : "(valueDate)",
"valueCurrency" : "(valueCurrency)",
"valueAmount" : "(valueAmount)",
"remark" : "?",
"beneficiaryEmailAddress":"",
"beneficiaryName":"(beneficiaryName)",
"beneficiaryAddress1":"(Address1)",
"beneficiaryAddress2":"",
"destinationBankCode":"(destinationBankCode)",
"chargingModelId":"OUR" 
}
```

#### Get Payment Status
```php
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "[SIGNATURE]",
"customerReferenceNumber": "(customerReferenceNumber)"
}
```

#### Get Inter Bank Inquiry
```php
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "[SIGNATURE]",
"customerReferenceNumber": "(customerReferenceNumber)",
"accountNum": "(accountNum)",
"destinationBankCode": "(BankCode)",
"destinationAccountNum": "(destinationAccountNum)"
}
```

#### Get Inter Bank Payment
```php
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "[SIGNATURE]",
"customerReferenceNumber": "(customerReferenceNumber)",
"amount": "(amount)",
"destinationAccountNum": "(destinationAccountNum)",
"destinationAccountName": "(destinationAccountName)",
"destinationBankCode": "(bankcode)",
"destinationBankName": "(bankname)",
"accountNum": "(accountNum)",
"retrievalReffNum": "(retrievalReffNum)"
}
```

#### Hold Amount
```php
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "[SIGNATURE]",
"customerReferenceNumber": "(customerReferenceNumber)",
"amount": "(amount)",
"destinationAccountNum": "(destinationAccountNum)",
"destinationAccountName": "(destinationAccountName)",
"destinationBankCode": "(destinationBankCode)",
"destinationBankName": "(destinationBankName)",
"accountNum": "(accountNum)",
"retrievalReffNum": "(retrievalReffNum)"
}
```

#### Hold Amount Release
```php
{
{
"clientId": "IDBNI" + BASE64(clientName),
"signature": "M4+FEsYOQluwIldqTqRti6oK3EhtGcTtrQZVtNrNZHxGz71kzXBoRCVgGuT8rq/jSE7c/sUXnSl/lqOPSvechI6HX1RpatHudd5mmLe2kcX38a2jg3L46dDuKC92cVrRmuPdvpOIH24J/gsNjrHHsgN3eEq8tmwKxQhgTkoZ4+Y=",
"customerReferenceNumber": "(customerReferenceNumber)",
"amount": (amount),
"accountNo": "(accountNo)",
"bankReference": "(bankReference)",
"holdTransactionDate": "(holdTransactionDate)"
}
```

### 2.2.B Snap BI

Create `One Gate Payment` class object
```php
{
X-SIGNATURE: (your_signature)
X-TIMESTAMP: (timedate)
X-CLIENT-KEY: (your_clientkey)
{
 "grantType": "client_credentials",
 "additionalInfo": {}
}
}
```

Available methods for `Snap BI` class
#### Balance Inquiry
```php
 "partnerReferenceNo": "(partnerReferenceNo)",
 "accountNo": "(accountnumber)"
}
});
```

#### Bank Statement
```php
{
 "partnerReferenceNo": "(partnerReferenceNo)",
 "accountNo": "(accountNo)",
 "fromDateTime": "(datetime)",
 "toDateTime": "(dataetime)"
}
});
```

#### Internal Account Inquiry
```php
 "partnerReferenceNo": "(partnerReferenceNo)",
 "beneficiaryAccountNo": "(beneficiaryAccountNo)"
});
```

#### Transaction Status Inquiry
```php
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
```php
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
```php
{{
{
 "partnerReferenceNo": "(partnerReferenceNo)",
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
```php
{
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
```php
{
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
```php
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
