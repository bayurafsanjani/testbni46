BNI API SDK - PHP
===============
This is the Official PHP client / library for BNI API. 
Please visit [Digital Services](https://digitalservices.bni.co.id/en/) for more information about our product and visit our documentation page at [API Documentation](https://digitalservices.bni.co.id/documentation/public/en) for more technical details.

## 1. Installation

### 1.1 Using COMPOSER
[download](https://getcomposer.org/download/)  Composer and run command line

```
composer require composer require bni-api/bni-php-client
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
$bni = new Bni(
  false,
'{your-app-name}',
'{your-api-secret}',
'{your-api-key}',
'{your-client-secret}',
'{your-client-id}'
);
```

### 2.2.A One Gate Payment

Create `One Gate Payment` class object
```php
$bni = new Bni(
  false,
'{your-app-name}',
'{your-api-secret}',
'{your-api-key}',
'{your-client-secret}',
'{your-client-id}'
);
dd($bni->getToken());
        $ogp = new OneGatePayment($bni);
```

Available methods for `One Gate Payment` class
#### Get Balance
```php
$ogp = new OneGatePayment($bni);
return $ogp->getBalance('115471119');
```

#### Get In House Inquiry
```php
$ogp = new OneGatePayment($bni);
return $ogp->getInHouseInquiry('115471119');
```

#### Do Payment
```php
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

#### Get Payment Status
```php
return $ogp->getPaymentStatus('20170227000000000020');
```

#### Get Inter Bank Inquiry
```php
return $ogp->getInterBankInquiry(
'20180930112233003',
'0115476117',
'014',
'01400000'
);
```

#### Get Inter Bank Payment
```php
return $ogp->getInterBankPayment(
'20180930112233005',
12007,
'01400000',
'Bpk HANS',
'014',
'BCA',
'0316031099',
'100000000097'
);
```

#### Hold Amount
```php
return $ogp->holdAmount(
'20181001112233009',
12007,
'0115476151',
'testHold'
        );
```

#### Hold Amount Release
```php
return $ogp->holdAmountRelease(
 '20181001112233010',
 12007,
 '0115476151',
 '657364',
 '31052010'
 );
```

### 2.2.B Snap BI

Create `One Gate Payment` class object
```php
//snap
$bni = new Bni(
  false,
  '{your-app-name}',
  '{your-api-secret}',
  '{your-api-key}',
  '{your-client-secret}',
  '{your-client-id}'
        );
//snap 
bi$snap = new SnapBI(
  $bni = '{instance-of-bn-class}',
  $pathPrivateKey = '{your-path-private-key}',
  $chanel = '{your-chanel}'
        );         
```

Available methods for `Snap BI` class
#### Balance Inquiry
```php
$token = $snap->balanceInquiry(
'202010290000000000002',
'0115476117'
 );
```

#### Bank Statement
```php
$token = $snap->bankStatement(
'202010290000000000002',
'0115476117',
'2010-01-01T12:08:56+07:00',
'2011-01-01T12:08:56+07:00'
);
```

#### Internal Account Inquiry
```php
$token = $snap->internalaccountinquiry(
 '2020102900000000000001',
 '0115476151'
);
```

#### Transaction Status Inquiry
```php
$token = $snap->transactionstatusinquiry(
 '20211213100434',
 '20211220141520',
 '0211220141520',
 '36',
 '2021-12-20',
 '12500.00',
 'IDR',
);
```

#### Transfer Intra Bank
```php
$token = $snap->transactionstatusinquiry(
 '202201911020300006',
 '12500',
 'IDR',
 '0115476117',
 '',
 'IDR',
 '14045',
 '',
 'Already One Year',
 '0115476151'
);
```

#### Transfer RTGS
```php
$token = $snap->transferrtgs(
'202201911020300011',
 '150005001',
 'IDR',
 'SAN',
 '3333333333',
 'CENAIDJA',
 '1',
 '1',
 '202201911020300006',
 '0115476151',
 '2022-01-25'
);
```

#### Transfer SKNBI
```php
$token = $snap->transfersknbi(
'202201911020300011',
 '150005001',
 'IDR',
 'SAN',
 '3333333333',
 'CENAIDJA',
 '1',
 '1',
 '202201911020300006',
 '0115476151',
 '2022-01-25'
);
```

#### External Account Inquiry
```php
$token = $snap->externalaccountinquiry(
'002',
'888801000157508'
);
```

#### Transfer Inter Bank
```php
$token = $snap->transferinterbank(
'2020102900000000000001',
'12345678.00',
'IDR',
'Yories Yolanda',
'888801000003301',
'002',
'888801000157508',
'2019-07-03T12:08:56-07:00'
);
```

## Get help

* [Digital Services](https://digitalservices.bni.co.id/en/)
* [API documentation](https://digitalservices.bni.co.id/documentation/public/en)
* [Stackoverflow](https://stackoverflow.com/users/19817167/bni-api-management)
* Can't find answer you looking for? email to [apisupport@bni.co.id](mailto:apisupport@bni.co.id)
