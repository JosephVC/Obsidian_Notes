
https://learn.microsoft.com/en-us/windows-server/security/kerberos/kerberos-authentication-overview

- authentication protocol for verifying the identity of a user or host
- Allows for single sign on to organization resources
	- after the initial sign on through Winlogon, Kerberos manages credentials via the forest whenever there is an attempted access to resources
		- Winlogon
			- component of Windows responsible for managing user logon/logoff, handles secure attention sequences, and loading user profiles
		- forest - 