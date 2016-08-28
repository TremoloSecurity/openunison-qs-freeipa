# OpenUnison FreeIPA Quickstart

This quickstart will deploy an OpenUnison integration with FreeIPA.  Once deployed,
a user will be able to:
1. Register
2. Request access to groups managed by FreeIPA
3. Update their own profile and upload an SSH key
4. Use a self service password reset if they forget their password

In addition to the keystore created in the instructions from https://hub.docker.com/r/tremolosecurity/openunisons2idocker/ the FreeIPA root certificate
should be added to the keystore.  

## Environment Variables

| Variable | Description | Example |
| -------- | ----------- | ------- |
| OU_HOST | The host name users will use to access the site | myapp.mycompany.lan |
| FREEIPA_BASE | The root DN of the FreeIPA Server | dc=rheldemo,dc=lan |
| FREEIPA_HOST | The host name of the FreeIPA Server | ipa.rheldemo.lan |
| FREEIPA_BIND_USER | A DN with read access to the 389 backing FreeIPA | uid=someuser,cn=users,cn=accounts,dc=rheldemo,dc=lan |
| FREEIPA_BIND_PASSWORD | The password for the read access service account | somesecret |
| JAVA_OPTS | List of Java system properties, MUST include unisonKeystorePassword | -Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom -DunisonKeystorePassword=start123 |

## Use

Once deployed, access this site by navigating to https://OU_HOST/ replacing
OU_HOST with the value of the OU_HOST environment variable.  For instance, if
OU_HOST is myapp.mycompany.lan use https://myapp.mycompany.lan/.  Once prompoted
for a username and password, use a uid and password from FreeIPA.  Once logged in, a page showing all headers,
request and session variables is shown.
