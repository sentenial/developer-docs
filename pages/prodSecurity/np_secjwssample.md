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
MIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQC2YpptmMegwas4SP0uLAk1px8e+iwU/djJez75ozmDWH/Hg4jqNrfA8sqHtBsP/1NDuzfv5KMxb+J/fZi52L90qn0tQGLMX0sDCoKam1aDSo0f4bhkLvM3goIXaeamFs5Qc1AOI+gjbPa+mw2x4IYG0kjiRYzZMtrUdMf9RIGf66Sy5qQIRd43HvvGXURdQ7EVk+lXzNX8IPfZ4HuvZWKkpNJLWnGPsMeuj672kTEs4PvnRPfA6d6wIK4HetIgS7bRJnQ2JasbZPf5V2GNTiyn12/oO2x3HbLHZDOFDPRU2i6UtgZkpCEL9DLw/K6nNFU7gKkcJ97yuuZ9bQLtUj8/AgMBAAECggEAD8RZpVZEq794yQmssx+LcqzBiMpuO48jMDsMKEVvS2a//sRLdpphK4UE85/v8Jbm4KWziEGaLUPtSMHXpvld7WM8i+G53AEnWVpac0ZkJdiw3cWEGbHiKzWITMES93jK2gAEahrtW2KoHuifBNzShiekgisqqfw2sfc5v5aUivnAG5xN00YUN2kSJaBlSa7vEsPYew3vdoVKIRluXhXsrv73aw4gbAza1LOH+mO6G4V55fduKa6R/P8zPwS1t3pDArvQs8L46FmJD8ow/H737Oqg+KPPo9VtqHE+Y7iwOw7h6dh0tBQ2BcMpPSkvg9oTNBttkjSKdL8fNQVolhx7wQKBgQDx5fWv342zisyoU4IxvNjEyr8h357PIZAIxTlxR6jKVHZMIXNEzL/uqhjMZCiOPkdvstLSgwgwnDFRRVXJnQEqQvMtLNDu6Ps0FxFGAjXSiOs+fI5TDa4IcJoX7Qs+90AbtHIDNhdfLbPl6lnIePxjrHJfR0TkZOfvAhx9CVOkbQKBgQDBBHtobhd5zlnYv7xuo0NqTLk7e1wutFLf5iZgv5loA5mYAHGb7TZf7Ha+85+9WqD3ViXnTl45hStI4puHfgO7LXL1pnshVV3FxqeHCNHhbYmawLJvv9FXlYULrmNGJlXkEVHi8ydNq/O2WLovHc7Lr4GY0DyPR+o2Q6es6n0u2wKBgCc9PWB9LBhO0KoRedIlpygtF1ogUzuYXyv9Cjdk/21qzBHHb1JewFevwfwN10JTufTVljtNxBtWiu17CNJ+pHy9hYLzfST0KCOoBkZL/30adsaZH+E7G9sEoQp2ild5di3IVKJOuPXYjREjtdK+RXrJs3ffML6326O6vPJPfAD1AoGAEyZEsBmsDpOgalardTaRa6xs/C/C94dAaaJF0Hdx2tXwmRoCK3wfVuj45vz4riqdqaxMWmR2CLLjlnmVAJ5J9HoP27tGoAn+Ia8R093WJM1fR5Eyos+fD1dwObZ1dvI6t0PYofGJxrT2mvK2lhIZADBLZUPTnkt+Ox//NLKW9N0CgYAoMRha3MJHyls597o0XPBVFC0nj2rTSqLubokzAZId+I6t+HAOOJ3KPxZMy+UvBgWrRpAR+5AgRbybVcpEyOUKwpCfTzho6v6AdRlbjgi9VN31Bki/CDY12EsQxyMGRHsanRQb+nNy8Z3EhLqbvsQo1qnw9+pM2Lsk0Gek2ocgbw==
-----END PRIVATE KEY-----
````

## Sample Certificate

```
-----BEGIN CERTIFICATE-----
MIIEbTCCAlWgAwIBAgIFAJTPRnEwDQYJKoZIhvcNAQELBQAwVTELMAkGA1UEBhMCR0IxDzANBgNVBAcMBkxvbmRvbjEPMA0GA1UECgwGTnVhcGF5MRMwEQYDVQQLDApOdWFwYXkgQVBJMQ8wDQYDVQQDDAZOdWFwYXkwHhcNMTcwOTEyMTE1NzIzWhcNMjcwOTEyMTE1NzIzWjBRMU8wCQYDVQQGEwJHQjANBgNVBAcMBkxvbmRvbjANBgNVBAoMBk51YXBheTARBgNVBAMMCmEyYXYzcHk4MncwEQYDVQQLDApOdWFwYXkgQVBJMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAtmKabZjHoMGrOEj9LiwJNacfHvosFP3YyXs++aM5g1h/x4OI6ja3wPLKh7QbD/9TQ7s37+SjMW/if32Yudi/dKp9LUBizF9LAwqCmptWg0qNH+G4ZC7zN4KCF2nmphbOUHNQDiPoI2z2vpsNseCGBtJI4kWM2TLa1HTH/USBn+uksuakCEXeNx77xl1EXUOxFZPpV8zV/CD32eB7r2VipKTSS1pxj7DHro+u9pExLOD750T3wOnesCCuB3rSIEu20SZ0NiWrG2T3+VdhjU4sp9dv6Dtsdx2yx2QzhQz0VNoulLYGZKQhC/Qy8PyupzRVO4CpHCfe8rrmfW0C7VI/PwIDAQABo0gwRjAOBgNVHQ8BAf8EBAMCBeAwEwYDVR0lBAwwCgYIKwYBBQUHAwIwHwYDVR0jBBgwFoAUIzFc1F8e8ejiFwGt2rB+x1G6EwowDQYJKoZIhvcNAQELBQADggIBAFPRL7amnWqp0gsvDFlhizt1RHmCK/eS4xPeNF0ME8/SJA9r+/rTbAqsLrwxolz+3NozloTjvIxlaVN9b0g/mDBnwu4ihSKwLvs08F//zEXMKboRizIV1s2liaYacMRWiaIi5zQ5YDup6RcxhzejlHCMnPboOjE8adWMmSvlr+WyPLxJyhDyVSnsCk2JztYN9+W+r4UQ8wzAl6RrfCSsbDVaaAP9FGIZblFwf50FcbiP9Y3wXdai522hc9OiXmZtBokDMxWzKCgAsN3JJClB8EbtRMTQdOc6S0g8gnHVzn9K/tQoD+m6afOX3RZyekNm0CxNnDEvweheo/gzpduX95na3dK2suWQRTEngwx6xqeEIlOGD4IErWbeVgePV4mnPqJ0J/Wbsz8XqDmpl73UsmNgdbwA6UhiGZ8UwOiJhUOS72K0lQzG/eHprPqoWmwJaSHsp436TqKtNm8NvvuaYhRH5HU4u9m4IHWN2twQHbesIHPQ3JqFnM8bndX9WQhkwiMCn6XHiZH2mGTnIPo3CAuYazEzNwaXc8E0eSq7b3ChCCRIe3G7JB7L4elMMzRUpiLt0F80BGZ59AuPZqrDl9XnySYMYk9iNYo+ifecVG3nPqMQEVN4sAvkkOjvYUFT3+Jq8kav36UvMaU3pqqfSM/GmMaZmTk1RlCAv0/91Jhk
-----END CERTIFICATE-----
````

|**Attribute**|**Value**|
|Serial Number|00 94 cf 46 71|
|Subject (OU)|Nuapay API|
|Subject (CN)|a2av3py82w|
|Subject (O)|Nuapay|
|Subject (L)| London|
|Subject (C)|GB|

## Sample JOSE Header

The JOSE Header is generated from the certificate attributes above, note that the 'Serial Number' is first decoded from hexadecimal to decimal before use in the JOSE header as the kid.

```json
{
     "alg": "RS256",
     "kid": "2496611953",
     "iat": 0,
     "iss": "C=GB, L=London, OU=Nuapay API, O=Nuapay, CN=a2av3py82w",
     "b64": false,
     "crit": ["b64","iat","iss"]
}
````

## Sample HTTP Request Body

When generating the JWS this would be used as the payload. Typically this would be the body of the REST request you wish to have signed.

For this example we will use the following payload:


```json
{
     "originatorIban":"GB42TURU00999992266193",
     "requestedExecutionDate":"2017-09-19",
     "paymentAmount":12.34,
     "paymentCurrency":"EUR",
     "endToEndId":"1234567890abcdef",
     "remittanceInformation":"Remittance info"
}
````

## Sample JWS

This JWS was generated using the above certificate, private key, JOSE Header and payload to RFC 7515 specification.

```
ewogICAgICJhbGciOiAiUlMyNTYiLAogICAgICJraWQiOiAiMjQ5NjYxMTk1MyIsCiAgICAgImlhdCI6IDAsCiAgICAgImlzcyI6ICJDPUdCLCBMPUxvbmRvbiwgT1U9TnVhcGF5IEFQSSwgTz1OdWFwYXksIENOPWEyYXYzcHk4MnciLAogICAgICJiNjQiOiBmYWxzZSwKICAgICAiY3JpdCI6IFsiYjY0IiwiaWF0IiwiaXNzIl0KfQ..cI1J4sFocsXlYcbD4vvTZFEZXZtieR4HJJ-3BJOr9uFTv5tsChPLlc6bIDMJssm_B598yURFTixsWHOcF6QsR3NkOtUauFHJZdkbQcxPWrbHzQApgQoglV5CBlUTiv3GkBaNhNuyNAoE10D6ToqyTB2NYSo3kYU4JWRtly-33UXutG1Z-4ZKS-nGWSpVGkP45RjcrPzyOXdkX_Gg3hr3pYwX5M8pZDS3SfkCDnlV7fGBp0Iz8aSTq8cNVKc5-zBjAQG8Q4xcWeEKTW_TXAA9mhHtTHD_tVs6dVdsc2-cXNfReaaKvHzHaR3af_oQImJcGRepZfL1gtFr2tAbkoS3ow
````

{% include links.html %}
	
