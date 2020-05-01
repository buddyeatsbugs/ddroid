# input validation PHP

# white list with values (prefered)
```
$only_allowed_ips = array('127.0.0.1');
if (!in_array($_SERVER['REMOTE_ADDRESS'], $only_allowed_ips))
{
  die('Unauthorized Access');
}

public function Ping($host, $num_packets) {
  if(!in_array($host, array('127.0.0.1', 'www.google.com')) || !in_array($num_packets, array(1,2,3,4))) {
    return 'host or number of packets not allowed, sorry eh';
  }
}

```

# white list with characters (still good but not as great as values)

```
public function Ping($host, $num_packets) {
  if (strlen($host) > 15 || strlen($num_packets) > 1 || !preg_match('|^[a-z\.]+$|', $host) || !preg_match('|^[1-9][0-9]*$|', $num_packets)) {
    return 'host or number of packets have an invalid format, sorry eh';
  }
}

```
# black list with values or characters

```

```

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
```

# regex statements
```
if(preg_match("/<!DOCTYPE/i", preg_replace("/\s/", '',
$xml_string))) {//DOCTYPE found
 die('Unsupported XML file, sorry'); //This is an attack,
abort processing ASAP
 }
 
 
 if (!preg_match('|^[a-z0-9\.]+$|i',
$filename)) {
 return 'Sorry, only letters and numbers allowed
in the filename!';
 }
 ```


# regex statement only looking for properly formatted input


# Native functions (santize input)
```
return shell_exec("ping -c" . escapeshellarg($number_packets) . " " . escapeshellarg($host));
```

# Native functions (canonicalize filepath names)
```
file_put_contents('/home/www/uploads' . basename(realname($filename), base64_decode($file_contents));
```

# Native functions (encode output)

```
echo htmlspecialchars($unencoded_output_string, ENT_QUOTES, 'UTF-8');
```


# Custom user created fudunctions 


# HTTP VERB/METHOD Tampering + REST ACTION SPOOFING
```
if ($_SERVER['REQUEST_METHOD'] === 'POST') {//This can only be done
using POST!
 if (isset($_POST['user']) && !preg_match('/^[a-z]+$/i',
$_POST['user'])) {
 die('Invalid user!'); //Abort
 }
if (isset($_POST['pass']) && !preg_match('/^[a-z]+$/i', $_POST['pass']))
{
 die('Invalid password!'); //Abort
 }
 add_user($_REQUEST['user'], $_REQUEST['pass']);//$_GET is not
validated!
} 
```
