## Table of Contents
- [Getting Started](#getting-started)
	- [spf](#spf)
	- [dkim](#dkim)
    - [dmarc](#dmarc)
    
## Getting Started

These are my notes on setting up email security for the Exchange online platform.

### spf
The record is as simple as:
`v=spf1 include:spf.protection.outlook.com -all` you just need to decide if hard `-` or soft `~` fail.

