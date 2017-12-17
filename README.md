EasyHexcoin-PHP
===============

A simple class for making calls to HexCoins's API using PHP.

Getting Started
---------------
1. Include easyhexcoin.php into your PHP script:

    ```php
    require_once('easyhexcoin.php');
    ```
2. Initialize Bitcoin connection/object:

    ```php
    $hexcoin = new Hexcoin('username','password');
    ```

    Optionally, you can specify a host, port. Default is HTTP on localhost port 8332.

    ```php
    $hexcoin = new Hexcoin('username','password','localhost','8332');
    ```

    If you wish to make an SSL connection you can set an optional CA certificate or leave blank
    ```php
    $hexcoin->setSSL('/full/path/to/mycertificate.cert');
    ````

3. Make calls to hexcoind as methods for your object. Examples:

    ```php
    $hexcoin->getinfo();
    
    $hexcoin->getrawtransaction('0e3e2357e806b6cdb1f70b54c3a3a17b6714ee1f0e68bebb44a74b1efd512098',1);
    
    $hexcoin->getblock('000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f');
    ```

Additional Info
---------------
* When a call fails for any reason, it will return false and put the error message in `$hexcoin->error`

* The HTTP status code can be found in $hexcoin->status and will either be a valid HTTP status code or will be 0 if cURL was unable to connect.

* The full response (not usually needed) is stored in `$hexcoin->response` while the raw JSON is stored in `$hexcoin->raw_response`
