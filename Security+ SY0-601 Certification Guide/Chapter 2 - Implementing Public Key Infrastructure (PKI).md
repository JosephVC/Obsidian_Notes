---
---
* **public key infrastructure -** an asymmetric encryption strategy that has some Certificate Authority and the infrastructure to support the issuing and managing of certificates
* pki provides asymmetry using two keys - a public key and a private key
* a **certificate authority** is the highest authority, and they hold the master key (root key) for signing all the certificates it provides to an **intermediary**; the intermediary provides these certificates to the **requester**
	* ![[./_resources/Chapter_2_-_Implementing_Public_Key_Infrastructure_(PKI).resources/image.png]]
	* **a certificate is known as an X509 certificate**
	* **online CA -** an internal online CA that is always online so people can request a certificate at any time;  for government or secure situations this would not be the case
	* **offline CA -** this is an offline CA for instances where security requires vetting and authorization before a certificate is issued
		* the CA is kept offline, turned off, and locked up when not in use so it cannot issue new certs
	* **public CA -** a third-party CA that is commercially accepted as an authority for issuing certificates; examples are Symantec, GoDaddy, etc.
		* the value of a third-party CA is that you don't have to manage anything about the certificate yourself
		* the third-party will keep their own **Certificate Revocation List (CRL)** to check if your certificate is still valid
			* to sell goods and services, an invalid certificate will not be accepted
			* **B2B transactions require a valid public certificate**
		* **the OID** of a cert is basically its serial number
	* **private CA** **\-** these can only be used internally ; while these are free, you have to take care of the certificate yourself
	* **registration authority (RA) -** the RA accepts and validates the incoming requests for certificates and notifies the CA to issue the certs. these issued certs are **X509 certificates**
	* **Subordinate CA -** this can also be called an **intermediary** can be the RA that issues the cert
	* **certificate pinning -** prevents the issuing of fraudulent certs and the compromising of the CA; also protects against MiM attacks
* **Certificate trust**
	* **trust anchor - in** a PKI environment, a trust anchor is the root certificate from which the whole chain of trust is derived; the root CA
	* **Trust Model -** proves the authenticity of a certificate
		* **hierarchical trust model -** the normal PKI model; uses a hierarchy from the root certificate down to the intermediary (aka a subordinate) ; note the above CA Hierarchy diagram
		* **Bridge trust Model -** this is peer-to-peer, where to separate PKI environments trust each other; the cert authorities communicate with each other and thus allow for cross-certification; this can be referred to as the **trust model**
	* **certificate chaining -** used to verify the validity of a cert, as it includes the details of CRL.  there are three layers in the cert chain
		* the cert vendor
		* the vendors CA
		* thecomputer where the cert is installed
		* **fewer than three layers can cause trust issues**

* **Certificate Validity**
	* certs must be checked for validity every time they are used; below is the validity process:
		* ![[./_resources/Chapter_2_-_Implementing_Public_Key_Infrastructure_(PKI).resources/image.1.png]]
			* **Certificate Revocation List (CRL)**
				* if a cert (X509) is in the CRL it is invalid and must not be accepted
				* the CRL will be providing validity unless it is slow or it is a web server looking for a faster lookup
			* **Online Certificate Status Protocol (OCSP)**
				* this comes in to play when the CRL is very slow, as the OCSP is fast and can thus take load off the CRL
			* **Cert Stapling**
				* also known as OSCP stapling
				* when a web server bypasses the CRL to use the faster OCSP **regardless if the cert is valid**

* **Cert Management Concepts**
	* ![[./_resources/Chapter_2_-_Implementing_Public_Key_Infrastructure_(PKI).resources/image.2.png]]
		
	* **Certificate Signing Request (CSR)**
		* the process of requesting a new cert
	* **Key Escrow**
		* holds the private keys for 3rd parties and stores them in a **Hardware Security Module (HSM)**
			* the HSM is a piece of hardware meant to store keys, attached to the server; it stores and manages certificates
	* **Data Recovery Agent (DRA)**
		* if a user cannot access their data because their key is corrupted , the DRA will recover the data; the DRA needs to get the private key from the key escrow
		* needs a private key from a key escrow to recover data
	* **Certificate**
		* public key is sent to 3rd parties while the private key decrypts the data
			* the public key is always given away, and you will always received other's public key
	* **Object Identifier (OID)**
		* comparable to a serial number on a bank note; helps to identify the cert
	* **Cert formats**
		* ![[./_resources/Chapter_2_-_Implementing_Public_Key_Infrastructure_(PKI).resources/image.3.png]]

* **Types of Certs**
	* **Self-signed Cert**
		* used by the same entity that issued it; **does not have a CRL thus can't be validated or trusted**
	* **Wildcard**
		* for a domain called foo.bar, a wildcard would be \*.foo.bar; a wildcard cert would work for the variety of domains that would be contained in the \*
			* if there is a mail.foo.bar  and a web.foo.bar, the wildcard cert for \*.foo.bar would work for hte **Fully Qualified Domain Names (FQDN)** of multiple servers in the same domain
	* **Domain Validation (DV)**
		* a domain validated cert is an X.509 cert - a cert that comes from a registration authority - that proves the ownership of the domain name
	* **Subject Alternative Name (SAN)**
		* a SAN cert can be used on multiple domain names, such as [foo.com](http://foo.com) or bar.com; other information such as IP addresses, can be inserted into the cert
	* **code signing**
		* code signed certs are used to sign and authenticate software
	* **computer/machine cert**
		* computer/machine certs are used to identify a computer within a domain
	* **user certificate**
		* a user cert authenticates a given user on an application they use
	* **extended validation**
		* provides a higher level of trust for the entity using the cert; often used in the financial area
		* additional details about an organization must be provided when applying for an extended validation cert
		* a cheaper option for public facing sites would be a wildcard cert while for internal websites you could use a self-signed cert
		* often indicated by a **green URL bar**
			* ![[./_resources/Chapter_2_-_Implementing_Public_Key_Infrastructure_(PKI).resources/image.4.png]]
				

**Asymmetric and Symmetric Encryption**
