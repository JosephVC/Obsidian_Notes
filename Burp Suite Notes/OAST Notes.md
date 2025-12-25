---
---
**OAST (Out-of-band Application Security Testing)** tests what would be otherwise invisible security vulnerabilities

*     Created to improve **DAST (Dynamic Application Security Testing)** 
* a problem with DAST is how blind or asynchronous bugs can easily be missed, thus dynamic testing needed OAST to augment it
	* **SAST (Static Application Security Testing)** looks at the code itself for vulnerabilities, but can only often guess at what might go on when code is executed (SAST does not execute code itself); SAST thus produces a noisier, less accurate report as it must guess this way
* traditional dynamic testing sends a payload to a target application and analyzes what the response is
	* the problem with this is when there is no clear response, regardless of any underlying vulnerabilities 
* there needs to be a way to bypass the lack of any explicit response from a target, and that's where **out-of-band** testing comes in
	* out-of-band testing sends an attack payload which causes an interaction with an external system the researcher has control over, which sits outside the target domain
