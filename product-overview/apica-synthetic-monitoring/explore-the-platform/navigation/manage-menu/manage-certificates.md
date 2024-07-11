# Manage Certificates

The following menu option for Managing Certificates will only be available for customers that have this feature enabled for their accounts. **Certificate Manager for ZebraTester Checks**



Do you want to use certificates as a Client Authentication mechanism? Now you can with the Apica Certificate Manager.

The Certificate Manager allows customers to upload a PKCS12 certificate for use as a Client Authentication certificate when running ZebraTester checks.

A **PKCS12**(Public-Key Cryptography Standards) defines an archive file format for storing server certificates, intermediate certificates if any, and private key into a single encryptable file.

For added security, the role and ASM Portal screen for uploading certificates is separated from the ability to apply the uploaded certificates to ZebraTester scenarios. So this means that only select users with the proper permission levels will be able to attach strong digital certificates to their account for use in scripts and scenarios.

To accomplish this, we have added the following to ASM:

* **Manage Certificates Page** - A centralized ASM page for uploading and managing PKCS12 Certificates



* **Certificate Manager Role** - A role that allows access to the Manage Certificates page.
  * Users without this role will not be able to add/delete certificates, but will still be able to "apply" these certificates to ZebraTester scenarios _if_ they have permissions to edit check configurations.
* **Apica must enable the customer account for Certificate Manager**

### The Certificate Process <a href="#managecertificates-thecertificateprocess" id="managecertificates-thecertificateprocess"></a>

The process of using certificates is as follows:

1. A user with the Certificate Manager role accesses the Manage Certificates page in ASM
2. That user adds a new PKCS12 Certificate with a name of their choosing
   1.
   2.
3. A user with Check Admin (or equivalent) permissions creates or edits a ZebraTester check
   1. That user adds a new ZebraTester scenario OR edits an existing ZebraTester scenario and chooses the recompile option
4. Check the box “Use PKCS12 Certificate”
5. Select the certificate name used when adding the certificate above from the list
6.  Re-Compile the ZebraTester scenario to incorporate the certificate into the scenario, changing it from an external asset to an integrated asset



Any ZebraTester check using this scenario will now present the selected certificate for all requests when the scenario is run.

Important notes:

* Certificates are compiled into ZebraTester scenarios so deleting a certificate on the Manage Certificates page does NOT affect ZebraTester scenarios already compiled with that certificate
* There is a "**Hide Certificate Names**" option on the Manage Certificates page.
  * If this option is checked, then when users view or edit ZebraTester scenarios, they WILL be able to see if a certificate was used when last compiling the ZebraTester scenario, but will NOT be able to see that certificate's name.
* For security reasons, the Certificate Manager role cannot be added directly to the SAML/SSO role mappings. Customers who want to add the Certificate Manager role to SAML/SSO users will need to contact Apica to have that added by PS/Support.
* Once a Certificate is uploaded to ASM, there is no way for anyone to view or download it.  The only action allowed on uploaded certificates is to apply it to a ZebraTester scenario during compilation or to delete the certificate from the ASM portal.
