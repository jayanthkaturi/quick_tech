
[Source](https://medium.com/@robert.broeckelmann/authentication-vs-federation-vs-sso-9586b06b1380 "Permalink to Authentication vs. Federation vs. SSO - Robert Broeckelmann")

# Authentication vs. Federation vs. SSO - Robert Broeckelmann

![Robert Broeckelmann][1]

Subway of Life 8/52** /** [Dennis Skley][2]

Authentication. Federation. Single Sign On (SSO). I've mentioned these concepts many times. I haven't actually formally defined what each of these terms mean even though I've used these many times throughout my writing — these concepts are closely related.

**Authentication: **process of an entity (the Principal) proving its identity to another entity (the System).

**Single Sign On (SSO): **characteristic of an authentication mechanism that relates to the user's identity being used to provide access across multiple Service Providers.

**Federation: **common standards and protocols to manage and map user identities between Identity Providers across organizations (and security domains) via trust relationships (usually established via digital signatures, encryption, and PKI).

First, Identity and Access Management (IAM) is the management of identity concerns within an information technology organization. The term, IAM, can refer to the team or the responsibilities of the team. Ideally, IAM is a centralized team, but due to history, politics, or organizational structure that isn't always possible. The next best option is to have a central team dedicated to each of Business-to-Business (B2B), Business-to-Consumer (B2C), and Business-to-Employee (B2E) concerns. All too often, every individual group handles their own IAM responsibilities — this creates additional hurdles to adopting Federation and SSO across an organization. IAM can include authentication of users and system, authorization of those users and systems, user provisioning, audit of identity systems, user repository management (think LDAP or Active Directory), password policies, and other concerns.

Providing authentication services is a core responsibility of IAM. Authentication is the most generic of the three concepts mentioned in the post title. From an earlier post on[ thinkmiddleware.com][3], I gave the following as a definition of authentication. Authentication is the process of an entity (the Principal) proving its identity to another entity (the System). The Principal could be a computer program (a batch job, for example, running in the background), an end user (human), a computer system, a piece of hardware, mobile device, or other exotic things. The System, for our purposes, is any computer system that requires the caller to be identified before access is granted — often this system will be on server, sometimes it is on a device (cellphone, desktop, laptop, tablet), sometimes it will be in a browser. The Principal provides Credentials to the System that must be authenticated by the System using some type of identity system (including User Repository, Federation Server, or other). Credentials are sensitive information that positively identify the client and could come in many forms:

* Userid and password
* Digital Signature
* X509v3 client certificate
* pin # + random number from a[ FOB][4], Google Authenticate, or similar technology.

For completeness, a User Repository contains information about Users (Principals), their Credentials, Groups, group membership, and other user attributes. An LDAP Server or Active Directory is a typical example of a User Repository. More detailed descriptions of these concepts can be found[ here][5]. I previously defined Federation Server and Identity Provider in a previous [post][6].

Single Sign On (SSO) is a characteristic of an authentication mechanism that relates to the user's identity being used to provide access across multiple Service Provider. SSO allows a single authentication process (managed by a single Identity Provider, Directory Server, or other authentication mechanism) to be used across multiple systems (Service Providers) within a single organization or across multiple organizations. That single authentication mechanism could be:

* an LDAP server, Active Directory, database, or similar directory server
* a system that generates and passes a trusted token around to applications for the purposes of authentication.
* Sometimes, the term SSO is used to describe signing into applications with a password manager.
* Before 2005, SSO might have been used to mean a common set of credentials were used across multiple systems (probably with some type of asynchronous password synchronization system), but those credentials had to be provided by the user to log into each separate system — in some contexts, this is probably still the case.
* Federation as described below.

Single Sign On (SSO) deals with authentication and the technical interoperability of the actors involved to provide the common login credentials across systems.

A Directory Server-based SSO solution for multiple applications looks something like the following diagram.

SSO thru a common directory server

Another SSO example is N Service Providers (SPs) within an organization trusting a single Identity Provider (IdP) looks something like the following (this is actually identity federation, see next section).

N SPs trusting a single IdP

Federated Identity Management is a sub-discipline of IAM, but typically the same team(s) is involved in supporting it. Federation is a type of SSO where the actors span multiple organizations and security domains.

From the WS-Federation spec (one of numerous SSO protocols that enable federation) we have, "The goal of federation is to allow security principal identities and attributes to be shared across trust boundaries according to established policies." This is a good description of federation in general; it involves having common standards and protocols to manage and map user identities between Identity Providers across organizations (and security domains) via trust relationships (usually established via digital signatures, encryption, and PKI). Federation is the trust relationship that exists between these organizations; it is concerned with where the user's credentials are actually stored and how trusted third-parties can authenticate against those credentials without actually seeing them.

The federation relationship can be accomplished through one of several different protocols including (but, not limited to):

* SAML1.1
* SAML2
* WS-Federation
* OAuth2
* OpenID Connect
* WS-Trust
* Various proprietary protocols

Federation can take many forms. Within an organization (departments, business units), the patterns could look like:

* N Service Providers (SPs) within an organization trusting a single Identity Provider (IdP) — see diagram in the last section.
* N SPs across multiple organizations trusting a single third-party IdP
N SPs across multiple organizations trusting a single third-party IdP

* N IdPs within an organization trusted by one SP.
N IdPs within an organization trusted by one SP

* N IdPs within an organization trusting a single IdP
N IdPs within an organization trusting a single IdP

* N SPs (let's call them API Providers) across multiple organizations trusting a single IdP, which is then trusted by a common system (such as an API Gateway)

[1]: https://miro.medium.com/fit/c/96/96/1*yXVvmCCxXnGwQvFzw6q2bw.jpeg
[2]: https://www.flickr.com/photos/dskley/
[3]: http://thinkmiddleware.com/blog01
[4]: http://searchsecurity.techtarget.com/definition/key-fob
[5]: http://thinkmiddleware.com/blog01/2009/06/14/using-openldap-as-a-user-repository-with-jboss-43x/
[6]: https://medium.com/%40robert.broeckelmann/keeping-your-apis-secure-for-multiple-user-types-d5c627793c4c

  
