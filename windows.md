# windows

## Generate self signed certificate

Generate a self signed certificate with powershell with the name "LocalCert" under LocalMachine\My

```
New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "localhost" -FriendlyName "LocalCert" -NotAfter (Get-Date).AddYears(10)
```

{% hint style="info" %}
Powershell must be run under elevated privileges
{% endhint %}

### Allow HttpListener to Url without Admin privileges

```text
netsh http add urlacl url=https://+:9000/ user=Everyone
```

### Bind certificate to Port

```text
netsh http add sslcert ipport=0.0.0.0:9000 certhash=5edf6324bf9935827b84fbc56abb901861f20037 appid={3D0947C1-26DA-4B60-BDEA-70424EE847B2}
```

