//mangopay-v2-php-simple
//======================

//SIMPLE  CREATE USER (WITH SIMPLE Authorization) - in MANGOPAY

// TO BEGIN create a post to https://api.sandbox.mangopay.com/v2/clients/ with fields names on form:
// ClientId
// Name
// Email

// You will receive the password, then you search and replace the ClientId and PASSPHRASE in the next code :

$postData = array(
    'FirstName' => 'TESTE',
    'LastName' => 'TESTE',
    'Email' => 'teste@teste.com',
'Nationality' => 'PT',
    'Birthday' => strtotime('12/12/1990'),
    'CountryOfResidence' => 'PT');

$ch = curl_init('https://api.sandbox.mangopay.com/v2/ClientId/users/natural');
curl_setopt_array($ch, array(
    CURLOPT_POST => TRUE,
    CURLOPT_RETURNTRANSFER => TRUE,
    CURLOPT_HTTPHEADER => array('Content-Type: application/json',
        'Authorization: Basic '.base64_encode("ClientId:PASSPHRASE")
        
    ),
    CURLOPT_POSTFIELDS => json_encode($postData)
));

// Send the request
$response = curl_exec($ch);

// Check for errors
if($response === FALSE){
    die(curl_error($ch));
}else{print $response; }

