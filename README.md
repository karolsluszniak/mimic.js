# Mimic

> This is a fork of [original Mimic](http://mimic-xmlrpc.sourceforge.net/) created by Carlos Eduardo Gonçalves. I've created it in order to extend it with async support and make the library available in bower.

Mimic is an open source XML-RPC client implemented in JavaScript. It was classified as client, because it is only able to produce requests and parse responses, so you cannot use it to parse requests and produce responses as required for a server implementation.

It is intended to be embedded inside web pages and enable them to access web services based on XML-RPC through the W3C XMLHttpRequest interface.

It is compliant with the major browsers (IE, Firefox, Opera, Safari and Chrome).

## How to Use

It is very simple to use Mimic, you only have to produce a request and then process the response. To do it you only have to use two small objects **XmlRpcRequest** and **XmlRpcResponse**.

Synchronous request example:

```js
function callCalculator() {
  var method = document.getElementById("operation").value;
  var request = new XmlRpcRequest("demos/calc.php", method);

  request.addParam(document.getElementById("n1").value);
  request.addParam(document.getElementById("n2").value);

  var response = request.send();

  alert(response.parseXML());
}
```

Asynchronous request example:

```js
function callCalculator() {
  var method = document.getElementById("operation").value;
  var request = new XmlRpcRequest("demos/calc.php", method);

  request.addParam(document.getElementById("n1").value);
  request.addParam(document.getElementById("n2").value);

  request.send(function (response, status) {
    if (status === 200) {
      alert(response.parseXML());
    }
  });
}
```
