<h1>Modernizing Legacy Active Directory via Entra ID and Intune</h1>

<h2>Description</h2>


<br />

<h2>Phase 1: Synchronize On-Premises Active Directory (AD) with Entra ID</h2>

<h4>Microsoft Entra Connect Sync is used on the local Domain Controller to sync the AD identities to Entra ID:</h4>
<img width="880" height="622" alt="Entra Connect Sync" src="https://github.com/user-attachments/assets/9f0bff27-dbfa-4fe9-90fc-f4e07afac24a" />
<img width="1920" height="518" alt="Entra Connect Sync Successful" src="https://github.com/user-attachments/assets/7e5f8c6e-b869-47e4-af1c-82520dc4ba4e" />

<h2>Phase 2: Entra Configuration</h2>
<h4>Before users can access Microsoft 365 apps, they will be assigned a Microsoft 365 E5 license:</h4>
<img width="1223" height="668" alt="e5 license assignments cropped" src="https://github.com/user-attachments/assets/c54216b9-8692-465a-953b-d77d74b3390a" />

<h4>Two Conditional Access policies are configured to restrict access to M365 apps:</h4>
1. Require a compliant device (detailed in Phase 3)<br />
2. Require multi-factor authentication if connecting from outside the corporate network <br /><br />
<img width="1289" height="606" alt="Conditional access policies cropped" src="https://github.com/user-attachments/assets/b369f982-4dd1-4687-a9a6-998a391427e7" />

<h4>The Conditional Access policies work as a user who connects from a non-compliant device is denied access:</h4>
<img width="407" height="548" alt="compliant device fail access denied" src="https://github.com/user-attachments/assets/ebea15b6-ccca-4f66-8ae6-5ee17916b2ea" />


<h2>Phase 3: Intune Configuration</h2>

<h2>Phase 4: Deploy Computer with Out-of-Box Experience (OOBE)</h2>

