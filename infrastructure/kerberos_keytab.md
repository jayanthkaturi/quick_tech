
[Source](https://ssimo.org/blog/id_016.html "Permalink to About Kerberos Principals and Keys")

# About Kerberos Principals and Keys

### About Kerberos Principals and Keys

Thu, 20 Jun 2013 - 16:00

I find time and again people find the concept of principals is a confusing unless they are very familiar with Kerberos.

I see the same issues when discussing about keys and keytabs.

So what is a Kerberos Principal ?

The simplest, initial, answer can be that a principal is the analogous of a user name in a multiuser OS. So why do we call it principal ? And why do you hear variations like 'User Principal' or 'Service Principal' ?

The reason why the term principal is used is because 'user' is indeed insufficient, too generic and misleading. In Kerberos there are many actors that need keys, any actor that need a key needs to be represented by an identifier. These identifiers are compounded strings called 'principals'.

#### Anatomy of a principal

A principal is a set of components represented by strings. One very important component is the realm name, each principal is always fully qualified with the name of the realm, The realm is represented by the last component in the string form. It is placed after an @ sign and is conventionally all upper case. The first part of the principal, instead, represents a specific identity within the realm. The first part can be split in multiple components joined by a / character.

Example: 
    
    
    component1 / component2 @ REALM

The simplest principals are actually what we think of users, generally actual people. The simplest identifier to represent users uses just one component and the realm. For example, the principal simo@EXAMPLE.COM represents a user named 'simo' that belongs to a realm named EXAMPLE.COM

The component is what we think of a user name, pretty simple so far. The realm as you can see resembles a domain name. That is on purpose as normally Kerberos realms are tied to DNS domain names, although not strictly required by the protocol specifications. Some implementations of Kerberos like Active Directory makes this a requirement. In AD the realm name is always the (DNS) domain name.

Another set of extremely important principals are the so called Service Principals. These principals represent actual programs or computers. Their form normally comprises two components, a service part and a fully qualified hostname.

Example: 
    
    
    nfs/server.example.com@EXAMPLE.COM

Let's analyze this principal name. The first component represents the service being used, in this case 'nfs' is used to represent a NFS server. Other well know service types are 'HTTP', 'DNS', 'host', 'cifs', etc... The second component is a DNS name. This is the server's own name. The realm specifies that this service is bound to the EXAMPLE.COM realm.

Why this specific convention was chosen to represent a specific NFS Server ?

The reason is that the Kerberos protocol does not offer a name resolution service. So a convention was devised to make it easy for a client to automatically compute what is the principal name of a target service they want to contact based on 2 easy to know names: the service type, and the name of the host that is offering it. This is necessary because this name is used by the client to contact the KDC and ask for a ticket for that specific service. If the client doesn't know the specific name of the target service, it cannot ask for a ticket.

The service type is easy to know, an NFS client is used to connect to an NFS server and the type can simply be hard coded to 'nfs', or can be set into a configuration file quite easily, it will be the same for all services of that type across the network.

The host name is also generally a well known name. When a user wants to connect to a specific server it has to identify it somehow to the NFS client, and that usually means giving the mount utility a server 'name'. Same for HTTP, you have to give the browser a server name to contact as part of a URL and so on. The only limitation, in case of Kerberos is that you need the canonical form upfront (although there is work to relax this requirement). DNS is often used to find out the canonical form from a shorter name or sometimes even an IP address (but see [this post][1] about reverse resolution).

The question at this point is why do we need principals to represent services or whole hosts ? The answer is that each service you want to contact needs keys in order to decrypt the tickets you present them to authenticate yourself.

#### Keys and Keytabs

Each principal is associated to a specific key in the KDC and this key is used to encrypt the tickets given to the clients. A service needs the same key in order to decrypt tickets; this is why Kerberos is called a shared key system. Any actor in a Kerberos system has a key that is also known to the KDC and is used to authenticate messages sent to the KDC or received from the KDC (a ticket can be considered a message received indirectly from the KDC where the KDC asserts the identity of the client.)

For user principals the key is the user's password. The KDC stores a copy of the password (generally transformed from the clear text into a more cryptographically useful secret through a key derivation process, but nonetheless perfectly equivalent to the user password).

For service principals, generally, instead of using a password a random key is generated and stored both in the KDC and in a file called a 'Keytab'.

A keytab file contains keys for a specific service, it is completely equivalent to a password file and needs to be treated as a highly sensitive secret.

Possession of the keytab means ability to fully impersonate the principal whose keys are stored in the keytab file. This means a keytab file should never be transmitted over a network in the clear (no emailing of keytabs please) and should be protected by appropriate access control (file permissions) at all times; a common mistake is to create a file in /tmp that is readable by anyone and only then move it somewhere else more secure.

Users can also use keytabs, a password can always be transformed into a keytab (using the same key derivation process that the KDC uses to store its copy), but that is less common because any password change will require to create a new keytab with the new keys.

#### Using and mapping principals

One of the things that people seem not to realize when they are first shown principals is that any principal can be used as a client to contact any service (this is not always true in AD as sometimes Service Principals are not allowed to request a TGT, but this is a configuration decision and is not always true).

This means that when accepting connections authenticated via Kerberos, applications need to pay a little bit of attention to who the client is. And need to perform some basic access control on the client principal before allowing access.

A common mistake is to take the principal name in string form and simply cut anything after the @ sign (the realm name) and use the remaining part as a 'user name' on the system, then perform calls like getpwnam() with this user name and grant the client the same access this user has on the system. Another even worse mistake is to allow ANY client that could properly authenticate to access data as if it were 'trusted' somehow. 

On the one hand this may not be sufficient, and on the other this may be dangerously broad and an actual security issue.

First of all, as we said above, any principal may try contact a service, not just users that have a 1-1 corresponding name in the system. A NFS Server may act as a client and use it's key to contact another service. For example a web application needs to decide whether it wants to grant access to a client named nfs/nfsserver.example.com@EXAMPLE.COM just like it gives access to joe@EXAMPLE.COM or not.

There are also more exotic principals that may contact a service though, not just principals that are somehow directly trusted by our own KDC. For example anonymous principals and principals coming from a trusted realm.

[Anonymous principals][2] are quite an obscure and little used feature, often it is not possible to get tickets anonymously in a Kerberos realm, but they are allowed by some implementation, and if the KDC is configured to allow anonymous principals then applications need to be careful not to give these clients the same access they give to fully identified clients.

The anonymous principal is: 
    
    
    WELLKNOWN/ANONYMOUS@WELLKNOWN:ANONYMOUS

As can be seen the realm is actually a specially named realm and this is to avoid legacy apps that match the REALM before allowing access to be fooled in to thinking this is a fully trusted user. This is one reason why simply blindly chopping off anything after the @ character is a grave mistake.

Another reason why the realm part must be validated are Kerberos cross-realm trusts. A Kerberos realm can be configured to 'trust' another Kerberos realm. Meaning the principals of Realm A are allowed to get tickets for services in Realm B if there is a trust relationship between B and A.

For our application this means that it may be contacted by both the user joe@REALM.A and a different user joe@REALM.B that has nothing to do with the previous one. If our application simply cuts off the realm part, without checking that the realm matches something it understand, it may give access to data of a user in one realm to an homonym in another realm. 

In general applications that do not want to deal with multiple realms should define one realm as allowed and refuse access to any principal that comes from a different realm. If multiple realms need to be supported (and that is a good idea) then appropriate mapping from the principal to an application identifier should be performed, by either using the full principal name as identifier, or by asking the system to map the principal for us including telling whether the principal is acceptable. This can be done in GSSAPI by using the gss_localname() function, which respects the auth_to_local configuration documented in the krb5.conf(5) manpage.

Using the system provided configuration allows admins to configure rules only once for the whole machine/network and avoid the need to implement mapping in every different application, so I highly recommend it where possible.

Additional warning: Principal names are considered case sensitive by the reference implementation (MIT Kerberos) but some implementation treat them in a case-insensitive way (Active Directory for example). It is safer to always treat principal names in a case sensitive way. (Active Directory will generally always provide the canonicalized form in tickets although it may accept mismatching cases when requesting tickets).

Hopefully this brief explanation will be useful to understand how to deal with principals and key tabs to the casual programmer that cares more about the practical implications rather than the abstract semantics and technicalities of the Kerberos protocol.

[1]: https://ssimo.org/id_015.html
[2]: http://k5wiki.kerberos.org/wiki/Anonymous_kerberos
