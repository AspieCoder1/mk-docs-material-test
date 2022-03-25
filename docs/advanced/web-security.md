# Web security

By default, authentication is not enabled for datapreparer.
However, you may want to ensure that only authenticated users can access the web interface.
Datapreparer gives you the ability to define a list of usernames and passwords for intended users of the application.
To do this, we edit the *datapreparer-users.properties*.
This file is expected to have the form `user.username = password`.
An example is:
```
user.user1 = pass1
user.user2 = pass2
```

## Enabling HTTPS
> To run this step, you need to have SSL certificates pre-installed on your server. 
> And you have generated the application JAR.

We can also enable HTTPS to run with datapreparer.
It takes the following steps:

### Get SSL certicicates
Get your SSL certificates from your chosen certificate provider.

### Adding certificate to the Keystore
You now need to import the certificate into a keystore. Java often comes with a tool called `keytool` to do this.
The command to do this is:
```bash
keytool -import -alias myAlias -file myCertificate.crt
    -keystore /path/to/keystore.p12 -storepass password
```

### Modifying server properties
First, Do the following two steps:

1. `vi datapreparer-${version}.jar`.
2. Choose the file `BOOT-INF/classes/application.properties`
Modify the file based on the following
```bash
# The format used for the Keystore. It could be set to JKS if it is a JKS file
server.SSL.key-store-type=PKCS12
# The path to the Keystore containing the certificate
server.SSL.key-store=/path/to/Keystore.p12
# The password used to generate the certificate
server.SSL.key-store-password=password
# The alias mapped to the certificate
server.SSL.key-alias=myAlias
```

### Restarting the service (if running)
You now restart datapreparer using `sudo systemctl restart datapreparer.service`

### Restarting the service (if running)
You now just restart data preparer using `sudo systemctl restart datapreparer.service`