SimplifyIAM IAM Implementation Portfolio
Cohort: SimplifyIAM Live Cohort  Name: Sheroziy  LinkedIn: [LinkedIn URL] In progress — SimplifyIAM Live Cohort


What I Built
Over five live Saturday sessions I built a complete IAM environment from scratch using midPoint, OpenLDAP, and Auth0. The environment runs on a dedicated cloud server and replicates how IAM provisioning works in a real enterprise engagement.

This repository documents my configuration, screenshots, and decisions for each session. It is intended as portfolio evidence for IAM implementation roles.


Environment
Component
Purpose
midPoint
IGA platform - identity lifecycle, provisioning, reconciliation
SimplifyHR (Flask)
HR source of truth - simulates enterprise HRIS
OpenLDAP
Target directory - user accounts provisioned here
Auth0
Access management - OIDC and SAML federation




Session Deliverables
Saturday 1 - Architecture and Environment
Architecture diagram or description committed
Screenshot: midPoint Screens
Screenshot: SimplifyHR dashboard running
Screenshot: OpenLDAP screens and OU structure

What I built: [Fill in - 2 sentences max]

Resume bullet: [Your bullet here]


Saturday 2 - Joiner Workflow
HR source connector configuration (screenshot or XML snippet)
Correlation rule definition (screenshot or XML snippet)
Inbound mapping table (screenshot)
Screenshot: New Joiner account in OpenLDAP after reconciliation

What I built: [Fill in - 2 sentences max]

Resume bullet: [Your bullet here]


Saturday 3 - Mover and Leaver Workflows
Role definitions created (screenshot or XML snippet)
Mover workflow configuration (screenshot)
Screenshot: Robert Klein account disabled/deleted after leaver trigger
Reconciliation results (screenshot)

What I built: [Fill in - 2 sentences max]

Resume bullet: [Your bullet here]


Saturday 4 - Access Management
Auth0 OIDC application configuration (screenshot)
SAML integration SP and IdP config (screenshot)
SAML assertion screenshot (redact any sensitive values)
JWT claims screenshot

Auth0 OIDC flow — what you configured and the sequence of redirects:
I configured OpenID Connect single sign-on between Auth0 (identity provider — proves who the user is) and Salesforce (service provider — the app being logged into). In Salesforce I set up a Connected App and an Auth Provider pointing at my Auth0 tenant's authorize, token, and userinfo endpoints; in Auth0 I created a matching application with the Salesforce callback URL.

```
Salesforce (Service Provider)
      |  user hits login → redirected to Auth0
      v
Auth0 Universal Login (Identity Provider)
      |  test user authenticates
      v
Salesforce /authcallback
  - receives identity: email, provider "Open ID Connect", auth0| user ID
  - SSO confirmed
```

![Salesforce authcallback showing the authenticated Auth0 test user](week-04-auth0-ciam/screenshots/week04-salesforce-sso-success.png)
Salesforce authcallback showing the authenticated Auth0 test user — provider "Open ID Connect" confirms the OIDC federation worked.

How federation connects to the IGA layer you built in Sessions 2 and 3:
In Weeks 2–3 I built the IGA side — midPoint provisioning governed accounts into the directory from an HR source. Federation is the layer on top: once an identity exists, OIDC lets that user log into an external app like Salesforce using their central identity. IGA answers "who exists and what may they have"; federation answers "how they prove who they are at login."

What I built: I configured single sign-on between Salesforce and Auth0 using OpenID Connect, with Auth0 as the identity provider (the service that proves who the user is) and Salesforce as the service provider (the app the user logs into). I created a test user in Auth0, set up the connected app and auth provider on both sides, and confirmed the flow worked by seeing Auth0 pass the user's identity into Salesforce.

Resume bullet: Implemented B2B single sign-on federating Salesforce (service provider) with Auth0 (identity provider) over OpenID Connect — configured the connected app, OAuth scopes, and provider endpoints, and validated end-to-end federation by confirming identity claims flowed from Auth0 into Salesforce.


Saturday 5 - Career Preparation
Final resume bullets section (5 bullets, one per session)
LinkedIn before and after headline
Mock interview reflection

Resume bullets (copy these to your CV):

[Saturday 1 bullet]
[Saturday 2 bullet]
[Saturday 3 bullet]
[Saturday 4 bullet]
[Saturday 5 bullet]


My Transformation
Where I started: [Role, experience level, what you could not explain or do before the cohort]

Where I am now: [What you built, what you can demo, what you can now explain in an interview]

Roles I am targeting: [Job titles, geography, companies if relevant]



