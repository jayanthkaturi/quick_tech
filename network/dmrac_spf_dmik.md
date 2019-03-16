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
