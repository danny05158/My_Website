---
title: cURL API calls
author: Daniel
date: '2019-05-01'
slug: curl API calls
categories: []
tags: []
header:
  caption: ''
  image: ''
bibliography:
---

As I mentioned in my third post, I have been working with PHP. And one of the tasks I was tasked to do was to integrate an external API using HTTP cURL request. It was not my first time doing it but for the purposes of this post I wanted to show how I tackled this problem (GET, POST, PUT). The first iteration of approching this problem.

```php
function call_external_API($method, $posting_url, $data = [], $headers = []){


   $curl = curl_init();

   switch ($method){
      case "POST":
         curl_setopt($curl, CURLOPT_POST, TRUE);
         if ($data)
            curl_setopt($curl, CURLOPT_POSTFIELDS, $data);
         break;
      case "PUT":
          curl_setopt($curl, CURLOPT_CUSTOMREQUEST, "PUT");
         if ($data)
            curl_setopt($curl, CURLOPT_POSTFIELDS, $data);
         break;
      default:
         if ($data)
            $posting_url = sprintf("%s?%s", $posting_url, http_build_query($data));
   }

   // curl - options
   curl_setopt($curl, CURLOPT_URL, $posting_url);
   curl_setopt($curl, CURLOPT_HTTPHEADER, array(
      'APIKEY: 00000000000000000',
      'Content-Type: application/json',
   ));
   curl_setopt($curl, CURLOPT_RETURNTRANSFER, TRUE);
   curl_setopt($curl, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);

   // execute curl
   $result = curl_exec($curl);

   if(!$result){
      die("Error: No result");
    }

   curl_close($curl);
   return $result;
}
```

The above is a basic setup for creating a POST and PUT request. Ofcourse it will also depend on documentation and if the api requires headers and special tokens.

```php
$headers = array(
    'Authorization: Bearer 0110-1-1-1-1-1--1-1',
    'Content-Type: application/json'
);

$response = call_external_API('GET', 'https://yourendpoint.com/get_info/', $data, $headers);
$result = json_decode($response, true);

```
The  ``` $response``` variable will contain what we are looking for and for testing you can decode the response.

### Cheers!
