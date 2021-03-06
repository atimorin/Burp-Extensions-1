Content-Type Converter
=========

Burp extension to convert XML to JSON, JSON to XML, x-www-form-urlencoded to XML, and x-www-form-urlencoded to JSON.

Requirements: Java 8 (Due to issues with one of the libraries it only works on Java 8. I have not had any problems with Burp using Java 8.)

Right-click on a request in an editable message window such as Repeater, Intruder, and the Proxy interceptor

The following convertions are supported:

* XML to JSON
* JSON to XML
* Body Parameter to XML
* Body Parameter to JSON
* GET Request Parameter to POST Request XML
* GET Request Parameter to POST Request JSON

![alt tag](https://blog.netspi.com/wp-content/uploads/2015/06/1433537211-4d9354b031b81daa10a7247d882d20da.jpg)

###Body Parameter###

```
POST /test HTTP/1.1
Host: www.example.com
Proxy-Connection: keep-alive
Content-Length: 32

parameter1=1&parameters2="test"

```

#####To XML#####
```
POST /test HTTP/1.1
Host: www.example.com
Proxy-Connection: keep-alive
Content-Length: 136
Content-Type: application/xml;charset=UTF-8

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<root>
<parameters2>"test"</parameters2>
<parameter1>1</parameter1>
</root>
```
#####To JSON#####
```
POST /test HTTP/1.1
Host: www.example.com
Proxy-Connection: keep-alive
Content-Length: 43
Content-Type: application/json;charset=UTF-8

{"parameter1":"1","parameters2":"\"test\""}
```

###JSON to XML###

```
POST /test HTTP/1.1
Host: www.example.com
Proxy-Connection: keep-alive
Content-Length: 43
Content-Type: application/json;charset=UTF-8

{"parameter1":"1","parameters2":"\"test\""}
```
#####To XML#####
```
POST /test HTTP/1.1
Host: www.example.com
Proxy-Connection: keep-alive
Content-Length: 136
Content-Type: application/xml;charset=UTF-8

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<root>
<parameters2>"test"</parameters2>
<parameter1>1</parameter1>
</root>
```

###XML to JSON###

```
POST /test HTTP/1.1
Host: www.example.com
Proxy-Connection: keep-alive
Content-Length: 136
Content-Type: application/xml;charset=UTF-8

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<root>
<parameters2>"test"</parameters2>
<parameter1>1</parameter1>
</root>
```
#####To JSON#####
```
POST /text HTTP/1.1
Host: www.example.com
Proxy-Connection: keep-alive
Content-Length: 60
Content-Type: application/json;charset=UTF-8

{"root": {
  "parameters2": "\"test\"",
  "parameter1": 1
}}
```
