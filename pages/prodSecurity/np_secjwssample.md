---
title: JWS Sample
keywords: JWS Sample
summary: "JSON Web Signature Sample"
sidebar: sec_sidebar
permalink: np_secjwssample.html
folder: prodSecurity
---

To illustrate how to set up the JWS please view the following samples, which include:

* A sample Private Key
* A sample Certificate
* A JOSE Header generated from the certificate
* An example JSON payload
* The JWS generated using the above data and RFC 7515 specification

## Sample Private Key

```
-----BEGIN PRIVATE KEY-----
MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQC4Nf52wssJnpdYba4tfWoMGmUDfzFsqLDDccUm2+bmn/93lKuTZq57WbBRAFzyrlmiOi43Be4fLra0z0wV9etIxvvfo6OMagdh2uSW5+U+GuUYxUI+Sd67QkFmACM+A4YWvEGaR7jyYXUyYSr5EBa9Eq2xrYcJYmG2l3u9jXJTrUe7GOobRsZf5w+djg4qaAWDdukc4dg+kog3CwoiA9vJqqgUAhrTkashDrvxaFksR6Ngx1Cib+RV9X1XC/He2AKdRDUP9O/d7hqgGVIpUThh9BsbR25M3LzRoKOZQCr6dF7CG9EgZoZxbxZm+AFlaoEI/Dxcv9fEkYPGKzBlvw+FAgMBAAECggEAAccfoBTMMdkSe9t/IVhDBD/i9rAtEW/lWNWJwhDAPzyPEh/gsgj9KRqZ/YYj34G4Qr0OAiDwBeQFBmSzxsh7T1YAS03Af9PsI1EiAKTXTQykZmNM+t3qpOMET5Azxt7w1dpWRb9odQpkv6o5aHLzzTpXa84RbhFBgSogGxm43z7aKd6WVRiqNfZ2hsfghjQb3zbk6W7EQDAGLxGdyGob2QKP57FufFLPLUZzSoltNDW32WNuNqR1PeGbdaWqu9tPOLAxe7EAL2EuWGZAi10g0LGpOaSY67Tek14jPpZdq61JjIudRB0NCh2+H4UhF5QVCPNik63VtTC56UirBvRdQQKBgQDxOmDkgueRM0gwTchknsdZexZtU3tKDb5GCLZqXR0EOS5NGK4R7YHBD5t4UWIN8QslFEUK1Zt1pbxIuLODkiCTXIVyLUH9om5lXBsbJ1MCXTXtsEzrenO2AW+Sdt/TfQsoEf8s9is/aE7s3KSg6L6QTwyQuwUukdCAyeQxLkuzZQKBgQDDfci8qsnvgb+pLgPeiL2UoQ9IDLfVpXx7Nk3NsewzMMzvA7ENpwFX6/XEVq2OxK2YXJXciZK1YY/ijhrBdv6jQ2kWtsp4p9JjEffDAIGuGMmK/iysYzDbAUgXhOL4J9MqNWibXuwWmejRZwLJotltk4SazxibbUQbd+TsWK75oQKBgQC+K/nK7HBGhhk5C3kZ6hrarjDmC1Q880y3xZKZk8KWW8XmvbgtJgKPAxDb77zPpOHWX352piOiwgAHjKTo6sCHq/8AHjHSFMXXXp937q6ARJ+JPN3HHoguSj99Rf36qq+q7VUwSvmZSVA/Z0raF+Jzvf3385iIOCgaAA/HvemsCQKBgQCn0Z81d1gLJ1MlJL9llfVJVkoMC/70hS+rhh6cahTejRIgTQb9NVTN6V39wnsTiHuNxE1SGTe8RZiDYIJPept2BDR+r0R493iAW7hZymGI1vaNP02SX0RdfWgp6IX/ihCYt2ipmH8Ll+xpdwjJl+cXTgAT9ZymMNK60d3PlwH+gQKBgGWUsKGPh/RbDadV0lyl07d977O01btYz0JLvFT3sqZXe+4IQ1eBN5EU9QU7AFgCzkZ6JcXJtALgP15+41UySS0U9TjxLUQy02tV5bXREM67XsOwAlkmqzkrwIEs8cDgEcvq6wiHaUB4diPY4Z0yivA5WL9Wc+Zcgt24yqf0kzIz
-----END PRIVATE KEY-----
````

## Sample Certificate

```
-----BEGIN CERTIFICATE-----
MIIEtDCCApygAwIBAgIFHyPzaocwDQYJKoZIhvcNAQELBQAwgZsxCzAJBgNVBAYTAklFMRAwDgYDVQQIDAdLSUxEQVJFMREwDwYDVQQHDAhNQVlOT09USDESMBAGA1UECgwJU0VOVEVOSUFMMREwDwYDVQQLDAhVTklUIDE2RjEXMBUGA1UEAwwOc2VudC11YXQtZ2twcjExJzAlBgkqhkiG9w0BCQEWGGFwcHN1cHBvcnRAc2VudGVuaWFsLmNvbTAeFw0yMTExMDkxNDI2MTJaFw0zMTExMDkxNDI2MTJaMFExTzAJBgNVBAYTAkdCMA0GA1UEBwwGTG9uZG9uMA0GA1UECgwGTnVhcGF5MBEGA1UEAwwKeWJvcXlheTkycTARBgNVBAsMCk51YXBheSBBUEkwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQC4Nf52wssJnpdYba4tfWoMGmUDfzFsqLDDccUm2+bmn/93lKuTZq57WbBRAFzyrlmiOi43Be4fLra0z0wV9etIxvvfo6OMagdh2uSW5+U+GuUYxUI+Sd67QkFmACM+A4YWvEGaR7jyYXUyYSr5EBa9Eq2xrYcJYmG2l3u9jXJTrUe7GOobRsZf5w+djg4qaAWDdukc4dg+kog3CwoiA9vJqqgUAhrTkashDrvxaFksR6Ngx1Cib+RV9X1XC/He2AKdRDUP9O/d7hqgGVIpUThh9BsbR25M3LzRoKOZQCr6dF7CG9EgZoZxbxZm+AFlaoEI/Dxcv9fEkYPGKzBlvw+FAgMBAAGjSDBGMA4GA1UdDwEB/wQEAwIF4DATBgNVHSUEDDAKBggrBgEFBQcDAjAfBgNVHSMEGDAWgBQJG1r5ajrSSNQhRAr6bgnfYsVxmDANBgkqhkiG9w0BAQsFAAOCAgEAGaVkyIh2LnVh8FPOIjKMQ064IrmcfGLVMW/z/P8B7OPSN6SjTBXpPkmt6pHeoEgH5EECS6g3WSJkAC+EZvcrAhvGs3PkgmtUfEfk1LX3badq2qAzCU1BN0aoWWf/ASmZoW/GLSQb7aT3iRk4FrtBDT0wWhn4WWiAN2a3Gv9N1xDSY59Wxi37bn4PYrIpmtXL/3eRycJzuedMmf3LpMY35cZwZIAg/EW62C/J9C/SqD8bWBrKECNvy9j6uroozSz4kJh2jXv+4soTItYlQo2atR6+nM/IGB0PaQPU4E048Ji84jbvBTc0bpYpfEVM+uUY+6b7BhVx9PpebBY31S+ghybrBIsKUjmJt/cQHJ0ptYQRZiG4xTsApTdA6slkk9rU5RQivs+sxkL96eE6D4oMuqbjT7diIn29EPdNZ8Yo3WCD2ZvQfxIiI9fnzet/Z9LPbzO1Q/JYUwve7bNCAlwpgTAZ7heW+IBt6VM8iLWTgTfQSIFe3hzrFPthraNCas1TLhaJ3ZdrIjGkGSxRF0tc8WlDwDcwU++K5e8W6wMNpZan2KzvA7I4GAK0l0gyKHL7KVuCaqaGIelo648KFmYIiXYK8jLkW/JaPUx/agP/llOXImZWdOHkuASp53vv1AW6QW6rmiZ0uwoGvnaV2c2UhFqIAo156r41Dnjng3qiZNc=
-----END CERTIFICATE-----
````

|**Attribute**|**Value**|
|Serial Number|1f23f36a87|
|Subject (OU)|Nuapay API|
|Subject (CN)|yboqyay92q|
|Subject (O)|Nuapay|
|Subject (L)| London|
|Subject (C)|GB|

## Sample JOSE Header

The JOSE Header is generated from the certificate attributes above, note that:
* The 'Serial Number' is first decoded from hexadecimal to decimal before use in the JOSE header as the kid.
* In this example the Serial Number from the certificate (`1f23f36a87`) is decoded to `133747141255` (and used as the kid value).

```json
{
  "alg": "RS256",
  "kid": "133747141255",
  "iat": 0,
  "iss": "C=GB, L=London, OU=Nuapay API, O=Nuapay, CN=yboqyay92q",
  "b64": false,
  "crit": [
    "iat",
    "iss",
    "b64"
  ]
}
````

## Sample HTTP Request Body

The request body that needs to be signed must be provided to generate the JWS. In this example, an empty request body is provided: `{}`


{% include tip.html content="The formatting of your request body is important here. If you have pretty-printed your request body but the request is reformatted later, for example if all CR and LF characters are stripped prior to being processed in Nuapay, for example, then the JWS Signature will be invalid." %}

## Sample JWS Signature

The JWS Signature generated, to RFC 7515 specification, which uses the above certificate, private key, JOSE Header and payload is provided below:

```
ewogICJhbGciOiAiUlMyNTYiLAogICJraWQiOiAiMTMzNzQ3MTQxMjU1IiwKICAiaWF0IjogMCwKICAiaXNzIjogIkM9R0IsIEw9TG9uZG9uLCBPVT1OdWFwYXkgQVBJLCBPPU51YXBheSwgQ049eWJvcXlheTkycSIsCiAgImI2NCI6IGZhbHNlLAogICJjcml0IjogWwogICAgImlhdCIsCiAgICAiaXNzIiwKICAgICJiNjQiCiAgXQp9..d_cZ46lwNiaFHAu_saC-Zz4rSzNbevWirO94EmBlbOwkB1L78vGbAnNjUsmFSU7t_HhL-cyMiQUDyRWswsEnlDljJsRi8s8ft48ipy2SMuZrjPpyYYMgink8nZZK7l-eFJcTiS9ZWezAAXF_IJFXSTO5ax9z6xty3zTNPNMV9W7aH8fEAvbUIiueOhH5xNHcsuqlOGygKdFz2rbjTGffoE_6zS4Dry-uX5mts2duLorobUimGsdlUcSM6P6vZEtcXaJCdjrT9tuFMh4CkX9nqk19Bq2z3i-SX4JCPvhD2r3ghRmX0gG08UcvyFVbrnVZJnpl4MU8V4Nr3-2M5URZOg
````

## Testing

To test your settings, use the JWS Generator tool below.

{% include note.html content="This tool will allow you to generate a JWS Signature and should be used for testing." %}

<p>To use the Generator tool below:</p>
 <ol>
 <li value="1">Edit the JWS Header section and update the following: <ol><li value="1">"kid" </li><li value="2">"iss" (COMMON NAME - CN)</li></ol></li>
 <li value="2">Paste the HTTP request body into the JWS Payload section (JSON). Note that in the sample above an empty payload is used i.e. {}.</li>
 <li value="3">Paste the Private Key into the Signing Private Key area.</li>
 <li value="4">Click the <b>Generate JWS Signature</b> button.</li>
 <li value="5">Use the generated string as a JWS-Signature header value when making your call (passed in the Payload) to the Nuapay Endpoint you referenced in step 2 above.</li>
 </ol>

## Generator Tool

Paste the required information as indicated below:
* Your certificate serial number (kid)
* Your Commone Name (CN)
* Your JSON Payload
* Your Private Key

Click **Generate JWS Signature** when you're done:

{% include jws-signature-generator.html %}

Note:
* State is not required when [creating your CSR](np_secjwsrest.html#creating-a-certificate-signing-request-csr).
* If you have provided a value for this when generating your CSR, ensure that you add `ST` to the `iss` value in the JWS Header.
* So for example: "iss": "C=GB, L=London, `ST = Your State`, OU=Nuapay API, O=Nuapay, CN= abcdefg123"

## Automating the JWS
The Generator Tool allows you to create a JWS signature value based on your certificate details and private key and is intended for your initial testing.

1. Use the tool above to generate a JWS for a specific payload (e.g. for a [Create Beneficiary](np_createbeneficiary.html) request).
1. Copy the generated JWS and paste that as a header value in your `Create Beneficiary` call.
1. Generate your request and confirm that it is successful. Once your JWS is working as expected, you will need to code a solution that takes your certificate and private key to automatically generate a JWS and dynamically add it as a header to any requests that require it.

## Troubleshooting
If you are unsuccessful in creating a request with the generated JWS signature, please try the following:
* When generating the [CSR](np_secjwsrest.html#tag/Certificates) (If you are using REST to generate your certificate), if you have provided a value for `State`, ensure that you add `ST` as an attribute in the `iss` of the JWS Header.
* Ensure that you are using the decoded Serial Number for the `kid` value (and not the raw hexadecimal value).
* The Unix Epoch passed in the `iat` should be set to the current timestamp. Ensure that this date is not a future timestamp; a valid JWS Signature can be  generated if the date is in the past but not if a future timestamp has been applied. (In the Generator above this has been set to zero).  
* Try to pass your request with an empty payload e.g. `{}` and check the error code returned. If you receive a HTTP 400 then you will know that your JWS is correct (the 400 is because of the empty payload; you will typically receive a `7085: Beneficiary object is required`).
* If you have pretty-printed your request body when generating a JWS Signature, try removing any `CR` or `LF` characters and retry.
* Similarly if your payload was not pretty-printed when generating the JWS Signature, ensure that it is not pretty-printed when calling the endpoint with the JWS Signature header.
* Ensure that there is no extra spaces or formatting changes applied to the JWS Header when generating the JWS Signature. (Any superfluous formatting will result in an incorrect JWS being generated).
* Use the example private key, certificate, JOSE Header and Sample request above and try passing the values into the Generator tool to confirm that that JWS is generated as expected. Once you have confirmed that the Generator tool is creating the same JWS Signature as described in the sample, replace the `kid`, `CN`, payload and Private Key with your own values.

## Java Example

For an example of how signatures may be generated in Java, see the following sample on Github:

<a href = "https://github.com/sentenial/jws-sample-java" target= "new">https://github.com/sentenial/jws-sample-java</a>



<!--
Use the sample details provided here in the [JWS Signature Generator](np_secjwsgenerator.html) and confirm that the generated JWS matches the sample above.

{% include note.html content="We recommend that you use the sample details presented here in the [JWS Signature Generator](np_secjwsgenerator.html), confirming that the generated JWS matches the sample above. Once you have confirmed this, replace the sample values with your own private key, payload and certificate values in order to generate your unique JWS signature." %}

-->


{% include links.html %}
