### SPF (Sender Policy Framework)

```
"v=" defines the version of SPF used.

Publish a policy: Domains and hosts identify the machines authorized to send email on their behalf. They do this by adding additional records to their existing DNS information: every domain name or host that has an A record or MX record should have an SPF record specifying the policy if it is used either in an email address or as HELO/EHLO argument. Hosts which do not send mail should have an SPF record published which indicate such ("v=spf1 -all"). It is highly recommended to validate the SPF record using record testing tools such as those provided on the SPF Project webpage.
Check and use SPF information: Receivers use ordinary DNS queries, which are typically cached to enhance performance. Receivers then interpret the SPF information as specified and act upon the result.

Mechanisms
The following words provide mechanisms to use to determine if a domain is eligible to send mail. Eight mechanisms are defined:
ALL	=> Matches always; used for a default result like -all for all IPs not matched by prior mechanisms.
A	  => If the domain name has an address record (A or AAAA) that can be resolved to the sender's address, it will match.
IP4	=> If the sender is in a given IPv4 address range, match.
IP6	=> If the sender is in a given IPv6 address range, match.
MX	=> If the domain name has an MX record resolving to the sender's address, it will match (i.e. the mail comes from one of the domain's incoming mail servers).
PTR	=> If the domain name (PTR record) for the client's address is in the given domain and that domain name resolves to the client's address (forward-confirmed reverse DNS), match. This mechanism is deprecated and should no longer be used.[8]
EXISTS	=> If the given domain name resolves to any address, match (no matter the address it resolves to). This is rarely used. Along with the SPF macro language it offers more complex matches like DNSBL-queries.
INCLUDE	References the policy of another domain. If that domain's policy passes, this mechanism passes. However, if the included policy fails, processing continues. To fully delegate to another domain's policy, the redirect extension must be used.

Qualifiers
Each mechanism can be combined with one of four qualifiers:
+ for a PASS result. This can be omitted; e.g., +mx is the same as mx.
? for a NEUTRAL result interpreted like NONE (no policy).
~ (tilde) for SOFTFAIL, a debugging aid between NEUTRAL and FAIL. Typically, messages that return a SOFTFAIL are accepted but tagged.
- (minus) for FAIL, the mail should be rejected (see below).

Modifiers
The modifiers allow for future extensions to the framework. To date only the two modifiers defined in the RFC 4408 have been widely deployed:
exp=some.example.com gives the name of a domain with a DNS TXT record (interpreted using SPF's macro language) to get an explanation for FAIL results—typically a URL which is added to the SMTP error code. This feature is rarely used.
redirect=some.example.com can be used instead of the ALL-mechanism to link to the policy record of another domain. This modifier is easier to understand than the somewhat similar INCLUDE-mechanism.
```

```
TXT record type
v=spf1 a mx ip4:69.64.153.131 include:_spf.google.com ~all
```

### DMARC (Domain-based Message Authentication, Reporting and Conformance)

```
DMRAC Record: "v=DMARC1;p=reject;pct=100;rua=mailto:postmaster@dmarcdomain.com"


Tag       Name	                                          Purpose Sample
v         Protocol version	                          v=DMARC1
pct	  Percentage of messages subjected to filtering	  pct=20
ruf	  Reporting URI for forensic reports	          ruf=mailto:authfail@example.com
rua	  Reporting URI of aggregate reports	          rua=mailto:aggrep@example.com
p 	  Policy for organizational domain	          p=quarantine
sp	  Policy for subdomains of the OD	          sp=reject
adkim	  Alignment mode for DKIM	                  adkim=s
aspf	  Alignment mode for SPF	                  aspf=r
```

![DMRAC flow with SPF and DKIM](DMARC_author-to-recipient_flow.jpg "DMRAC Flow")
