---
layout: post
title: Curl basics
tags:
  - curl
  - REST
---
## Requests

```
curl https://example.com                               #GET request

curl -X POST https://example.com -d '{"key":"value"}'  #POST request

curl -X PATCH https://example.com -d '{"key":"value"}' #PATCH request
```

## Other ways to send data using -d flag

```
-d key="value"    #json format

-d @file.json     #file as input
```

## Options

```
-k               #for insecure requests/self signed certs
-o <file>        #store output in a file
-v               #verbose
-vv              #extra verbose
-s               #silent
-u user:pass     #authentication 
                 (use '\' to escape special characters in user or password)
-H               #header (example, -H 'Content-type: Application/json')
```

## Other useful things

```
curl https://example.com | json_pp  #pretty print json type response from curl.
                                     For this to work the response should be in json format.
```