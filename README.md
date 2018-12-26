PSTPagoFacil Transactional API PHP
============================================================

## Installation

Use composer package manager

```bash
composer require saulmoralespa/pstpagofacil
```

#### Bootstrapping autoloader and instantiating

```php
// ... please, add composer autoloader first
include_once __DIR__ . DIRECTORY_SEPARATOR . 'vendor' . DIRECTORY_SEPARATOR . 'autoload.php';

// import client class
use PSTPagoFacil\PSTPagoFacil

// create token in panel  menu "API Tokens" 
$token_user = 'YOUR_TOKEN_USER';

// instantiate the class
$pagoFacil = new PSTPagoFacil($token_user);
$pagoFacil->sandbox_mode(true); // sandbox true o production false
```

### Create pay transaction

```php
$transaction = array(
       'x_url_callback' => 'http://127.0.0.1/notify',
       'x_url_cancel' => 'http://127.0.0.1/cancel',
       'x_url_complete' => 'http://127.0.0.1/complete',
       'x_customer_email' => 'da545@gmail.com',
       'x_reference' => time(),
       'x_account_id' => '262', // Id service
       'x_amount' => 500,
       'x_currency' => 'CLP',
       'x_shop_country' => 'CL'
       );
//return object       
$data = $pagoFacil->createPayTransaction($transaction);
```

### Get status order

```php
$idOrder = '34524'; //id order
//return object
$statusOrder = $pagoFacil->statusOrder($idOrder);
```