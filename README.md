<h1>Modernizing Legacy Active Directory via Entra ID and Intune</h1>

<h2>Description</h2>
This project showcases an organization migrating from an on-premises Active Directory (AD) environment to a hybrid cloud setup with Entra ID and Intune device management. <br /><br />

Key features include syncing on-premises AD identities to Entra ID, conditional access policies to secure access to M365 apps, easy deployment of new computers from the Out-of-Box Experience, and automatic configuration of new computers with Google Chrome and security settings.

<h2>Phase 1: Synchronize On-Premises Active Directory with Entra ID</h2>
<h4>To bridge the on-premises domain controller with Entra ID, the Entra tenant's UPN suffix was added as an alternative UPN suffix on the domain controller in AD Domains and Trusts:</h4>
<p align="center">
  <img width="1262" height="454" alt="image" src="https://github.com/user-attachments/assets/19c44031-cf2b-4825-8305-7d2f276c5b7f" />
</p>

<h4>Microsoft Entra Connect Sync is used on the local Domain Controller to sync the AD identities to Entra ID:</h4>
<p align="center">
  <img width="880" height="622" alt="Entra Connect Sync" src="https://github.com/user-attachments/assets/9f0bff27-dbfa-4fe9-90fc-f4e07afac24a" />
</p>
<h4>The identities have been successfully synced with Entra ID:</h4>
<p align="center">
  <img width="1602" height="507" alt="image" src="https://github.com/user-attachments/assets/efb24934-c82d-4f70-916c-1430c5e280c5" />
</p>


<h2>Phase 2: Entra Configuration</h2>
<h4>Before users can access Microsoft 365 apps, they will be assigned a Microsoft 365 E5 license:</h4>
<p align="center">
  <img width="1223" height="668" alt="e5 license assignments cropped" src="https://github.com/user-attachments/assets/c54216b9-8692-465a-953b-d77d74b3390a" />
</p>

<h4>Two Conditional Access policies are configured to restrict access to M365 apps:</h4>
1. Require a compliant device (detailed in Phase 3)<br />
2. Require multi-factor authentication (MFA) if connecting from outside the corporate network <br /><br />
<p align="center">
  <img width="1289" height="606" alt="Conditional access policies cropped" src="https://github.com/user-attachments/assets/b369f982-4dd1-4687-a9a6-998a391427e7" />
</p>

<h4>The public IP address for the on-premises network is added to Entra for the 2nd Conditional Access policy configuration:</h4>
<p align="center">
 <img width="1321" height="421" alt="Off prem MFA required" src="https://github.com/user-attachments/assets/9d371533-20b3-4599-812d-e5603da5c8e7" />
</p>

<h4>The 2nd Conditional Access policy works as a user who connects from a non-compliant device is denied access:</h4>
<p align="center">
  <img width="407" height="548" alt="compliant device fail access denied" src="https://github.com/user-attachments/assets/ebea15b6-ccca-4f66-8ae6-5ee17916b2ea" />
</p>

<h2>Phase 3: Intune Configuration</h2>
<h4>A security baseline is configured on Intune to harden Intune-managed Windows computers automatically:</h4>
<p align="center">
  <img width="1426" height="455" alt="Intune security baseline cropped" src="https://github.com/user-attachments/assets/32a0c67e-2e94-4e7c-8c7c-f65e2cce775e" />
</p>

<h4>For a device to be compliant and access M365 apps, a compliance policy was configured in Intune requiring Windows 10 or later:</h4>
<p align="center">
  <img width="1330" height="460" alt="Intune compliance require windows 10 cropped" src="https://github.com/user-attachments/assets/c9d0d79a-e559-4ce7-b117-c533a9a1bf64" />
</p>

<h4>Google Chrome is added to Intune, so it will automatically install on Intune-managed devices:</h4>
<p align="center">
  <img width="1334" height="367" alt="Intune install Chrome cropped" src="https://github.com/user-attachments/assets/a2013311-4a1c-47b9-a14a-9e86d8e881ce" />
</p>

<h2>Phase 4: Deploy Computer from the Out-of-Box Experience (OOBE)</h2>

<h4>A new, fresh computer is easily deployed from the OOBE solely by connecting the work account:</h4>
<p align="center">
<img width="1023" height="770" alt="image" src="https://github.com/user-attachments/assets/11b2da23-16fe-4ba7-84fa-3fb3f8b9eda8" />
</p>

<h4>The computer is deployed and ready-to-use with Google Chrome installed automatically:</h4>
<p align="center">
  <img width="1022" height="767" alt="google chrome installed" src="https://github.com/user-attachments/assets/65420269-9610-42c2-ad6f-2c6afc199478" />
</p>

<h4>The 1st Conditional Access policy works as the user is prompted for MFA when connecting from outside the corporate network:</h4>
<p align="center">
  <img width="1850" height="638" alt="vpn required outside on prem network" src="https://github.com/user-attachments/assets/a63703da-bf6e-4cb1-97af-d6c24ff862c5" />
  Note: The VPN simulates a connection from outside the corporate network <br />
</p>

<h4>After signing in, the user can access Microsoft 365 apps, such as Outlook:</h4>
<p align="center">
  <img width="1025" height="768" alt="outlook works" src="https://github.com/user-attachments/assets/1f24cd19-5a40-46c5-9563-b722bf92c552" />
</p>
