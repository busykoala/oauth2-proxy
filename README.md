# OAuth2 Proxy with Nginx Rev-Proxy

This is a brief proof of concept installation to protect a
web-server (e.g. backend/frontend microservice) using a oauth2-proxy.

```bash
user --- nginx rev-proxy ---(auth request)--- oauth2-proxy --- IdP
                 |
          (if auth success)
                 |
            web-server
```

The rev-proxy does an auth request to the oauth2-proxy. If there is
a valid cookie the oauth2-proxy will allow the request and the
call is reversed to web-server (including the auth token incl. e.g. roles).
If there is not yet a cookie the oauth2-proxy will redirect to the
IdP (e.g. Keycloak) initiating a OIDC flow.
