# Importing the signed certificate to the store

You will find the default trust store delivered with your JVM in:

```
$JAVA_HOME/lib/security/cacerts
```

For instance in Mac OS, it is in:

```
/System/Library/Frameworks/JavaVM.framework/Home/lib/security/cacerts
```

Launch the following command line to import the certificate to the default trust store.

```
keytool -import -file /path/to/your/certificate.pem -alias NameYouWantToGiveOfYourCertificate -keystore /path/to/the/copy/of/the/default/truststore.jks -storepass changeit
```

To set the trust store and key store statically, you just have to add the following parameter into the environment variable:

What for | Parameter name
--- | ---
Trust Store Path | javax.net.ssl.trustStore
Trust Store Password | javax.net.ssl.trustStorePassword
Trust Store Type | javax.net.ssl.keyStoreType

So if you want to set them at start time, you can add the following parameter either:

* into your JAVA_OPTS:

```
-Djavax.net.ssl.trustStore=/the/path/to/your/trust/store.jks -Djavax.net.ssl.keyStoreType=jks ... etc ...
```

* or into your Java code:

```java
System.setProperty(
        "javax.net.ssl.trustStore",
        "/the/path/to/your/trust/store.jks");
System.setProperty(
        "javax.net.ssl.keyStore",
        "/the/path/to/your/key/store.jks");
System.setProperty("javax.net.ssl.keyStorePassword", "myPassword");
...etc...
```
