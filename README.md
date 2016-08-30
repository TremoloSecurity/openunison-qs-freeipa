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
| FREEIPA_ADMIN_USER | Administrative user used to update IPA | admin |
| FREEIPA_ADMIN_PASSWORD | Admin user's password | ***** |
| OU_HIBERNATE_DIALECT | The hibernate dialect for your database (https://docs.jboss.org/hibernate/orm/4.2/javadocs/org/hibernate/dialect/package-summary.html) | org.hibernate.dialect.MySQL5Dialect |
| OU_JDBC_DRIVER | The JDBC driver used to talk to the database | JDBC driver for your database, make sure that the driver is a dependency in your POM file | com.mysql.jdbc.Driver |
| OU_JDBC_URL | The connection URL for the OpenUnison audit database | jdbc:mysql://mariadb:3306/unison?useSSL=true |
| OU_JDBC_USER | User used to connect to the audit database | root |
| OU_JDBC_PASSWORD | Password used to connect to the audit database | ***** |
| OU_JDBC_VALIDATION | A query for validating connections on checkout | SELECT 1 |
| SMTP_HOST | Host for the SMTP server | smtp.gmail.com |
| SMTP_PORT | Port for the SMTP Server | 587 |
| SMTP_FROM | The "From" subject of emails to approvers | You have approvals waiting |
| SMTP_USER | User name for accessing the email server | user@domain.com |
| SMTP_PASSWORD | Password for the user for the email server | ***** |
| SMTP_TLS | true/false if the SMTP server uses TLS | true |
| OU_AUDITOR_GROUP | The name (cn) of a group in FreeIPA that provides access for auditors | system-auditors |
| JAVA_OPTS | List of Java system properties, MUST include unisonKeystorePassword | -Djava.awt.headless=true -Djava.security.egd=file:/dev/./urandom -DunisonKeystorePassword=start123 |
| OU_JDBC_PWD_URL | The JDBC URL for the password reset database | jdbc:mysql://mariadb:3306/passwordReset?useSSL=true |
| GOOGLE_CAPTCHA_SITE_KEY | Site Key from https://www.google.com/recaptcha |  XXXXXX |
| GOOGLE_CAPTCHA_SECRET | Secret from google recaptcha | XXXXXX |
| OU_SELF_REG_APPROVER_GROUP | The name (cn) of the group for approving user self registrations |


## Use

Once deployed, access this site by navigating to https://OU_HOST/ replacing
OU_HOST with the value of the OU_HOST environment variable.  For instance, if
OU_HOST is myapp.mycompany.lan use https://myapp.mycompany.lan/.  Once prompted
for a username and password, use a uid and password from FreeIPA.  Once logged in, a page showing all headers,
request and session variables is shown.
