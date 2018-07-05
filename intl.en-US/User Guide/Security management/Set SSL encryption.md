# Set SSL encryption {#concept_ack_rv4_ydb .concept}

To increase link security, you can enable SSL encryption and install SSL certificates on the necessary application services. SSL \(Secure Sockets Layer\) is used on the transport layer to encrypt network connections. It increases the security and integrity of communication data, but also increases the network connection time.

**Note:** 

-   Due to the inherent drawbacks of SSL encryption, activating this function significantly increases your CPU usage. We recommend that you only enable SSL encryption for Internet connections requiring encryption. Intranet connections are relatively secure, and generally do not require link encryption.

-   In addition, SSL encryption cannot be disabled once it is enabled. Do this operation with caution.


## Enable SSL encryption {#section_hjf_z54_ydb .section}

1.  Log on to the [RDS Console](https://rds.console.aliyun.com/).
2.  Select the region where the target instance is located.
3.  Click the ID of the target instance to enter the Basic Information page.
4.  In the left-side navigation pane, select **Security** to go to the Security page.
5.  Select the **SSL** tab.
6.  Click the button next to **Disabled**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/4147_en-US.png)

7.  In the SSL Setting dialog box, select the link for which to activate SSL encryption and click **OK** to activate SSL encryption, as shown in the following figure.

    **Note:** You can choose to encrypt both Internet and intranet links as needed, but only one link can be encrypted.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/4148_en-US.png)

8.  Click **Download CA Certificate** to download the SSL certificate, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/4149_en-US.png)

    The downloaded SSL certificate is a package including the following files:

    -   p7b file: Used to import the CA certificate on Windows OS

    -   PEM file: Used to import the CA certificate on other systems or for other applications

    -   JKS file: A java truststore certificate file used for importing CA certificate chains in Java programs. The password is apsaradb.

        **Note:** When using JKS certificate files in Java, you need to modify default jdk security configurations of jdk7 and jdk8 as follows: In the `jre/lib/security/java.security` file of the machine that runs the database to be accessed through SSL, modify the following configurations:

        ```
        jdk.tls.disabledAlgorithms=SSLv3, RC4, DH keySize < 224
        jdk.certpath.disabledAlgorithms=MD2, RSA keySize < 1024
        ```

        If you do not modify the JDK security configuration, the following error will be reported. Other similar errors are generally caused by Java security configurations.

        ```
        javax.net.ssl.SSLHandshakeException: DHPublicKey does not comply to algorithm
                    constraints
        ```


## Configure the SSL CA certificate {#section_mdn_nv4_ydb .section}

After SSL encryption is enabled, you need to configure the SSL CA certificate for applications or clients that access RDS. The following uses MySQL Workbench as an example to describe how to install the SSL CA certificate. For other applications or clients, see their usage instructions.

1.  Open MySQL Workbench.
2.  Choose **Database** \> **Manage Connections** .
3.  Enable **Use SSL** and import the SSL CA certificate, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/7949/4150_en-US.png)


