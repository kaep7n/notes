---
description: >-
  this page describes how to set up a asp.net core application using kestrel and
  windows authentication (kerbereos) on Windows as well as Linux
---

# kerberos

## Getting Started

Create asp.net core project using at least version 3.0. 

Add package [Microsoft.AspNetCore.Authentication.Negotiate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Negotiate) to the project. This package provides the necessary tools to use Kerberos with the platform independent Kestrel web server.

```aspnet
Install-Package Microsoft.AspNetCore.Authentication.Negotiate -Version 3.0.0
```

Add to ConfigureServices method in Startup

```aspnet
services.AddAuthentication(NegotiateDefaults.AuthenticationScheme)
                .AddNegotiate();
```

Add to Configure method in Startup

```aspnet
app.UseAuthentication();
```

After the authentication is configured correctly add an \[Authorize\] Attribute wherever it is required.

#### Debugging

When using IISExpress you might see this Exception

> InvalidOperationException: The Negotiate Authentication handler cannot be used on a server that directly supports Windows Authentication. Enable Windows Authentication for the server and the Negotiate Authentication handler will defer to it.

Make sure that the IIS settings launchsettings.json are configured properly and windows authentication is enabled

```text
"iisSettings": {
    "windowsAuthentication": true, 
    "anonymousAuthentication": true, 
    "iisExpress": {
      "applicationUrl": "http://localhost:49645",
      "sslPort": 0
    }
  }
```

## Windows

A prerequisite of using this approach on Windows is to add a SPN \(Service Principal Name\) to the User that is running the Service \(not the Machine Account\)

```
setspn -S HTTP/app-server-01.intern.test.com myuser
```



