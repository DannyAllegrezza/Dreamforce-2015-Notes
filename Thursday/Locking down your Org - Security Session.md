## Locking down your Org - Security Session
2 factor auth - what you know and what you have (cell phone) or bio metric)

Permission set for 2 factor authentication.

Locking the Gates: 
## IP Restrications
- You specify the IP range that your users can use to log in to the org.
- 1. Organization level trusted IP ranges
- 2. UI/ Browser login

Two factor sends out a SMS to the phone. Once the user Logs back in from th esame IP restriction, they won't require the same authentication restrication.


Security Controls -> Network Access (This is where you can allow a start IP range and End IP range).

Profile Level Trusted Login IP Ranges
- You go to the actual profile, and then you can set the Login Ranges for that particular profile.


## Single Sign On SSO with Salesforce
1. Delegated authentication (must request a support case)
2. SAML Federated Authentication

## SAML Federated Authentication
- User picks 1 password, and it connects to all systems. Now in version 2.0
- Security Controls -> Single Sign On

## Keeping The Bad Guys out with Secure Sessions
Administrator functions to maintain secure sessions
- session settings
- activations
- session management
- expire all passwords (extreme options - will force all users re-generate new passwords).
- They recommend they use and look at the Timeout value. All communications contain the session ID, so if you leave the Timeout session to a high level, you become vulnerable to someone stealing the session ID. 

##Activations
Activated Login IP
Recommend that you remove the IP's that are no longer necessary. 

##User Session Information
If you need to remove an employee, you need to also cancel their session immediately.

## Expire all Passwords
- Super extreme! This will expire all user passwords. 

## Password Policies

Connected Apps: Introduction

- A connected app allows your business to integrate with the Salesforce orginization using APIs.
- The admins may have control who can use the connected app.
- Two deployment modes
- 1. The app is created and used in the same org
- 2. The app is created in one org and installed on other orgs.

## What is an attacker looking for on your connected app?
- Obtaining of the client Secrets (key/secret) (They are not in the source code.. have them hidden or in env. variables).
- Protection of access token and refresh token

## OAuth Permissions
Enable OAuth Settings (bool)
Callback URL
Selected OAuth Scopes (Use as little as possible).
If you check "Use digital Signatures". It ensures that the requests are cryptographically signed. 

