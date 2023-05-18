# CVE-2022-46169 PoC: Authentication Bypass and Remote Code Execution

This repository contains a PoC for the CVE-2022-46169 vulnerability, which allows an attacker to bypass authentication and execute arbitrary code remotely on the affected system. This vulnerability affects Cacti, version 1.2.22, released on August 18, 2022.

The vulnerability occurs due to `remote_agent.php` has a function to retrieves IP address and verify an entry within the `poller` table. If an entry was found, the function will return `true` and the client is authorized. One of the actions is called `polldata` which retrive few request parameter, if the `action` of a `poller_item` equals to `POLLER_ACTION_SCRIPT_PHP` can lead the attacker to execute command injection vulnerability through `proc_open`

The PoC demonstrates how an attacker can exploit this vulnerability to bypass authentication and execute arbitrary code remotely on the affected system.

## Requirement

* Python3
* Requests

## Usage

Make sure `X-Forwarded-For` value is within the `poller` table
You may change the `payload`

```
python3 cacti.py
```

## Disclaimer

This PoC is intended for educational and testing purposes only. Use of this PoC on any system or network without explicit permission from the system owner is illegal and may result in prosecution. The author assumes no liability for any damage caused by the use or misuse of this PoC. Use at your own risk.


## Reference

[CVE Details](https://www.cvedetails.com/cve/CVE-2022-46169/)

[Github](https://github.com/Cacti/cacti/security/advisories/GHSA-6p93-p743-35gf)