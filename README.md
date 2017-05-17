function pushpainel($title, $message, $url) {
    $apiToken = 'YOUR TOKEN HERE, SEU TOKEN AQUI';
    $curlUrl = 'https://pushcrew.com/api/v1/send/all';
    //set POST variables
    $fields = array(
        'title' => $title,
        'message' => $message,
        'url' => $url
    );
    $httpHeadersArray = Array();
    $httpHeadersArray[] = 'Authorization: key=' . $apiToken;
    //open connection
    $ch = curl_init();
    //set the url, number of POST vars, POST data
    curl_setopt($ch, CURLOPT_URL, $curlUrl);
    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($fields));
    curl_setopt($ch, CURLOPT_HTTPHEADER, $httpHeadersArray);
    //execute post
    $result = curl_exec($ch);
    $resultArray = json_decode($result, true);
    if ($resultArray['status'] == 'success') {
        //success
        //echo $resultArray['request_id']; //ID of Notification Request
    } else if ($resultArray['status'] == 'failure') {
        //failure
    } else {
        //failure
    }
}
