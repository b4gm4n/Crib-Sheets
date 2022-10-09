## Table of Contents
- [Introduction](#introduction)
	- [spf](#spf)
	- [dkim](#dkim)
    - [dmarc](#dmarc)

## Introduction
Improve email security and integrity through dns records.

 ### spf - Sender Policy Framework
 displays a list of authorised email senders for this domain. Just simply add to domains dns as a txt record.
 #### syntax

`v=spf1 mx -all`  -- Allow domain’s MXs to send mail for the domain, prohibit all others.

`v=spf1 -all` -- The domain sends no mail at all.

`v=spf1 +all` -- The domain allows all IP addresses on the internet to send mail.  Though ‘valid’, this is not recommended.

`~all` soft fail and mark as suspicious `-all` fail, reject emails that failed the check.

use the `include:` identifier to list servers not already on the dns such as mx and A record servers.

Google `include:_spf.google.com` = `v=spf1 include:_spf.google.com ~all`

Microsoft `include:spf.protection.outlook.com` = `v=spf1 include:spf.protection.outlook.com -all`

 ### DKIM - DomainKeys Identified Mail
This is a method of email authentication that helps prevent spammers impersonating the domain.
DKIM uses a public key to authenticate where an email came from, that it actually came from a server that sends emails from that domain. A pair of cryptographic keys are used: a private key for the sender to sign messages with, and a public key for the receiver to verify signatures. A receiver cannot use the public key to sign messages, and vice versa.

Each email will contain a DKIM header, which contains a digital signature. The receiving email server can check the DKIM DNS record, obtain the public key, and use the public key to verify the digital signature.

This process also ensures that the email has not been changed in transit. The digital signature will not pass if email headers or the email body have been altered.

`[selector]._domainkey.[domain]`

 ### DMARC - Domain-based Message Authentication Reporting and Conformance
A DMARC policy tells a receiving email server what to do after checking a domain's SPF and DKIM records, whether an email passes or fails SPF and DKIM, the DMARC policy determines if failure results in the email being marked as spam, getting blocked, or being delivered to its intended recipient.

A DMARC recored could be as simple as `v=DMARC1; p=reject; adkim=s; aspf=s;` 
where:
    v=DMARC1 indicates that this TXT record contains a DMARC policy and should be interpreted as such by email servers.
    p=quarantine indicates that email servers should "quarantine" emails that fail DKIM and SPF. Alternatives p=none, which allows emails that fail to still go through, and p=reject, which instructs email servers to block emails that fail.
Optional
    adkim=s means that DKIM checks are "strict." This can also be set to r for "relaxed".
    aspf=s is the same as adkim=s, but for SPF.

DMARC policies can contain instructions to send reports about emails that pass or fail DKIM or SPF, this can be used to trace problems, reports are only sent by complying servers and typically only once a day.

`v=DMARC1; p=reject; adkim=s; aspf=s; rua=mailto:example@anotherdomain.com;`