# how to download the ssl certificate from a website

In order to download the certificate, you need to use the client built into openssl like so:

```bash
echo -n | openssl s_client -connect HOST:PORTNUMBER \
    | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > /tmp/$SERVERNAME.cert
```

That will save the certificate to `/tmp/$SERVERNAME.cert`.

You can use `-showcerts` if you want to download all the certificates in the chain. But if you just want to download the server certificate, there is no need to specify `-showcerts`

`echo -n` gives a response to the server, so that the connection is released

`sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p'` removes information about the certificate chain and connection details. This is the preferred format to import the certificate into other keystores.

!!! ref
    [https://serverfault.com/how-to-download-the-ssl-certificate-from-a-website](https://serverfault.com/questions/139728/how-to-download-the-ssl-certificate-from-a-website)
