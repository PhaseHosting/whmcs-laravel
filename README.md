Laravel WHMCS API
=================
# Important Notes
For Laravel 4, please refer to this notes. [Click Here](https://github.com/mgufrone/whmcs-api/tree/v1.0.1)

Laravel 5 - Simple package for WHMCS external API.

#### Setting you API URL

go to config/whmcs.php and set the parameters


	return array(

		'username'		=>	'api-username',
		'password'		=>	'api-password', // fill these if you want to use username password
		'auth_type'		=> 	'password', // password or api_key
		'url'			=>	'http://www.site.com/whmcs/includes/api.php', // API url
		'response'	=> 'object', // you can fill with either object or array
	);


Usage
=====

#### Basic usage

Logging a user to WHMCS

	$username = 'client';	// Client Username
	$password = 'password'; // Client Password

	$login = Whmcs::execute('validatelogin', array(
		'email' => $username,
		'password2' => $password
	));

	// or

	$login = Whmcs::validatelogin(array(
		'email' => $username,
		'password2' => $password
	));

	if($login->result == 'success') {
		echo 'User Logged In';
	} elseif($login->result == 'error') {
		echo $login->message;
	}

For reference on WHMCS API please follow [http://docs.whmcs.com/API](http://docs.whmcs.com/API "WHMCS API Documentation")


### Dynamic Configuration

If your site has multiple whmcs configuration, you sure will do override configuration like this

	\Config::set('whmcs.url','http://whmcs.site.com/includes/api.php');
	\Config::set('whmcs.password','your_password');
	\Config::set('whmcs.username','your_username');
