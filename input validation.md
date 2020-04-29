# input validation PHP

# white list with values
$only_allowed_ips = array('127.0.0.1');
if (!in_array($_SERVER['REMOTE_ADDRESS'], $only_allowed_ips))
{
  die('Unauthorized Access');
}

# white list with characters


# black list with values or characters

# type casting
```
* @param int $num_packets
```

# Dev Enviornment
```
define('IS_DEV_ENVIORNMENT', false);
if (IS_DEV_ENVIRONMENT && isset($_GET['wsdl']))
{
  //Provide WSDL declaration for this SOAP Web Service
}
```

# Is Authenticated via Sessions
```
session_start();
if (!isset($_SESSION['logged_in']) || !$_SESSION['logged_in'])) {
  die('Unauthorized access');
}

# regex statements


# regex statement only looking for properly formatted input


# functions (santize input)


# functions (encode output)


# Custom user created fudunctions 


