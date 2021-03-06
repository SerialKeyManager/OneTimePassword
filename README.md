# One Time Password

A .NET core library that implements HOTP based on [rfc4226](https://tools.ietf.org/html/rfc4226) and TOTP based on [rfc6238](https://tools.ietf.org/html/rfc6238).

It's compatible with the Google Authenticator App.

## Example
First, we need to create a shared secret (stored on the server and by the client)
```
var secret = OneTimePassword.CreateSharedSecret();
```

### Time-based
For a time-based token, we use:
```
OneTimePassword.TimeBasedPassword(secret)
```

### Counter-based
For a counter-based token, we use:
```
OneTimePassword.CounterBasedPassword(secret, 1)
```
The counter here is 1.

### Google Authenticator App
To get a Google Authenticator friendly shared secret:
```
OneTimePassword.SharedSecretToString(secret);
```

## Referencing from .NET Framework, .NET Core and others
One Time Password targets the .NET Standard 1.6, which should be compatible with .NET Framework 4.6.1 and .NET Core 1.0. For other frameworks, please see [this](https://docs.microsoft.com/en-us/dotnet/standard/net-standard).

It's seems to be important to install [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) for everything to work, especially on the .NET Framework.
