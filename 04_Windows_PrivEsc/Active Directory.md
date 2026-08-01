#Active Directory Notes

There is a market overdependence on Microsoft Active Directory and Entra ID. 

"Azure Active Directory has a 19.96% market share in the Identity And Access Management category, while Microsoft Active Directory has a 17.65% market share in the same space." Together both Microsoft products easily make up a third of the IAM market, which comes with a huge target of equal size to match.

- https://6sense.com/tech/identity-and-access-management/azureactivedirectory-vs-microsoftactivedirectory.

##Entra ID (AD for the cloud) - NOT ON THE OSCP

Fully hosted in the cloud as a multi-tenant, flat-architected service with no domain controllers. Uses modern web-based protocols like HTTPS, OAuth 2.0, SAML, and OpenID Connect; handles policies via cloud tools like Microsoft Intune.

##Active Directory (AD) - OSCP FOCUS

Deployed on-premises using local physical or virtual servers requiring domain controllers. A directory service for Windows enterprise environments that was officially implemented in 2000. AD is based on x.500 and LDAP protocols that came before it. AD provides AAA functions within a Windows enterpise environment. Uses legacy directory protocols like Kerberos, NTLM, and LDAP; managed via Group Policy Objects (GPOs) and Organizational Units (OUs).

Gaining a foothold in Active Directory is generally performed through privesc by moving laterally or vertically throughout the network until we accomplish the intent of the assessment.
