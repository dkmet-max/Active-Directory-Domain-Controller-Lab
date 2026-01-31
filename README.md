# Active-Directory-Domain-Controller-Lab
Windows Server 2016 | Step-by-Step with Images
Step 1: Verify System Security Baseline

Action:
Reviewed Windows Server security status before installing any roles by opening Control Panel → System and Security → Security and Maintenance.

Screenshot:

<img width="1012" height="723" alt="Screenshot 2026-01-16 203909" src="https://github.com/user-attachments/assets/1bfbb5cc-511e-449a-b430-234272ea0dc0" />

<img width="1013" height="756" alt="Screenshot 2026-01-16 203929" src="https://github.com/user-attachments/assets/b0a0e5f7-14e7-4941-844f-0f9f700c4130" />

<img width="1016" height="764" alt="Screenshot 2026-01-16 203943" src="https://github.com/user-attachments/assets/977a1c49-28bb-4fbe-b2b6-c1b6f0b3b67a" />

Why this matters:
Validating the OS security baseline ensures Active Directory is not deployed on an unstable or misconfigured system.

🔹 Step 2: Review Windows Firewall Status

Action:
Confirmed Windows Defender Firewall is enabled and manageable prior to exposing domain services.

Screenshot:

<img width="1014" height="703" alt="Screenshot 2026-01-16 204110" src="https://github.com/user-attachments/assets/7e45796c-7ae4-4684-ba50-ca09b7bfbad9" />

Why this matters:
Enterprise environments keep the firewall enabled and explicitly allow only required services.

🔹 Step 3: Allow Required Domain Services Through Firewall

Action:
Allowed only required Active Directory–related services through Windows Defender Firewall on the Private network profile.

Screenshot:

<img width="1010" height="756" alt="Screenshot 2026-01-16 204004" src="https://github.com/user-attachments/assets/1f1ea012-9384-4791-a840-4cc0ecc535fe" />

<img width="1013" height="702" alt="Screenshot 2026-01-16 204023" src="https://github.com/user-attachments/assets/251bfe7b-f9b2-49dd-9154-c4908226006b" />

<img width="1016" height="761" alt="Screenshot 2026-01-16 205140" src="https://github.com/user-attachments/assets/334b1ed8-630b-4d22-8729-30387314d200" />

Why this matters:
Blocking DNS, Kerberos, or Netlogon traffic will break authentication, domain joins, and Group Policy processing.

🔹 Step 4: Install Active Directory Domain Services (AD DS)

Action:
Installed the Active Directory Domain Services role using Server Manager.

Screenshot:

<img width="1019" height="760" alt="Screenshot 2026-01-16 204643" src="https://github.com/user-attachments/assets/f9dae86e-03e8-4b7c-92e7-bda58d0e15bb" />

<img width="1007" height="757" alt="Screenshot 2026-01-16 205015" src="https://github.com/user-attachments/assets/17bfb5c4-981e-4cff-88f3-306110c88b1c" />

Why this matters:
Role installation prepares the system without immediately changing authentication authority.

🔹 Step 5: Promote Server to Domain Controller

Action:
Promoted the server to a Domain Controller by creating a new forest.

Screenshot:

<img width="1019" height="760" alt="Screenshot 2026-01-16 204643" src="https://github.com/user-attachments/assets/0f9ce937-b7e6-47dd-908e-f40f775af15e" />

<img width="1007" height="757" alt="Screenshot 2026-01-16 205015" src="https://github.com/user-attachments/assets/87a800b9-4510-4548-9a55-dff4a723deb7" />

Why this matters:
This establishes the server as the authoritative identity provider for the environment.

🔹 Step 6: Confirm NetBIOS Name

Action:
Verified the automatically generated NetBIOS name during domain creation.

Screenshot:

<img width="1910" height="1071" alt="Screenshot 2026-01-16 203827" src="https://github.com/user-attachments/assets/c4bdb1c3-cf68-40af-8087-cff7da57b74c" />

Why this matters:
NetBIOS naming is still required for compatibility with many Windows processes and legacy systems.

🔹 Step 7: Review AD DS Database, Logs, and SYSVOL Paths

Action:
Confirmed default directory service storage paths for NTDS and SYSVOL.

Screenshot:

<img width="1019" height="760" alt="Screenshot 2026-01-16 205204" src="https://github.com/user-attachments/assets/ec81a5ce-b1b5-481c-95f7-56951b6e5eab" />

Why this matters:
SYSVOL integrity is critical for Group Policy distribution and domain stability.

🔹 Step 8: Review Prerequisites Check

Action:
Reviewed prerequisite check results before completing domain promotion.

Screenshot:

<img width="1019" height="758" alt="Screenshot 2026-01-16 205421" src="https://github.com/user-attachments/assets/e2f60ade-ad7b-4b5c-8331-dc0a2269beff" />

Why this matters:
Understanding warnings (such as DHCP usage) demonstrates real administrative judgment.

🔹 Step 9: Apply Domain Configuration and Reboot

Action:
Allowed Windows to apply domain configuration and complete the promotion process.

Screenshot:

<img width="1025" height="758" alt="Screenshot 2026-01-16 205641" src="https://github.com/user-attachments/assets/a6e96c11-7648-47b1-aea6-accc643bdc58" />

Why this matters:
This step transitions the system from a standalone server into a Domain Controller.

🔹 Step 10: Validate Domain Administrator Login

Action:
Logged in using domain credentials to confirm authentication functionality.

Screenshot:

<img width="1021" height="758" alt="Screenshot 2026-01-16 210149" src="https://github.com/user-attachments/assets/5823829a-b13a-410a-8c71-300e56979456" />

Why this matters:
Successful domain login confirms AD, DNS, and Kerberos services are functioning correctly.

🔹 Step 11: Verify Domain Status in Server Manager

Action:
Verified domain membership and installed roles via Server Manager → Local Server.

Screenshot:

<img width="949" height="760" alt="Screenshot 2026-01-16 210442" src="https://github.com/user-attachments/assets/c8333671-91e4-4aa7-8f27-6d9d93779036" />

Why this matters:
Confirms the server is fully operating as a Domain Controller.

🔹 Step 12: Review Network Adapter Configuration

Action:
Reviewed Ethernet adapter settings and confirmed required protocols were enabled.

Screenshot:

<img width="954" height="760" alt="Screenshot 2026-01-16 210501" src="https://github.com/user-attachments/assets/2021d5c4-7f9c-495d-ac66-80b4dcee44eb" />

<img width="380" height="590" alt="Screenshot 2026-01-16 210522" src="https://github.com/user-attachments/assets/0342502b-38ac-4bef-807e-230e4469c821" />

Why this matters:
Improper adapter configuration can cause intermittent authentication and DNS failures.

🔹 Step 13: Configure Static IPv4 and DNS

Action:
Assigned a static IPv4 address and configured DNS to loopback (127.0.0.1).

Screenshot:

<img width="458" height="602" alt="Screenshot 2026-01-16 210631" src="https://github.com/user-attachments/assets/0f11f478-4661-4352-84c9-6791379c7cde" />

<img width="464" height="169" alt="Screenshot 2026-01-16 210743" src="https://github.com/user-attachments/assets/17265ad8-cf9c-43f2-9914-413fc2d4b007" />

Why this matters:
Domain Controllers require stable IP and DNS settings to function reliably.

🔹 Step 14: Configure DNS Forwarders

Action:
Configured DNS forwarders to allow external name resolution.

Screenshot:

<img width="947" height="758" alt="Screenshot 2026-01-16 211317" src="https://github.com/user-attachments/assets/1136102e-3552-4e3a-abdf-bb7954eda620" />

<img width="952" height="758" alt="Screenshot 2026-01-16 211345" src="https://github.com/user-attachments/assets/59c04d8e-75e9-4a53-8b40-97163f6df45d" />

Why this matters:
Forwarders allow internet resolution without compromising internal AD DNS authority.

🔹 Step 15: Open Group Policy Management Console

Action:
Opened Group Policy Management Console to verify policy infrastructure.

Screenshot:

<img width="520" height="460" alt="Screenshot 2026-01-16 211128" src="https://github.com/user-attachments/assets/dabe9fa1-9cb1-4c88-bae5-43b850c456de" />

<img width="953" height="765" alt="Screenshot 2026-01-16 211251" src="https://github.com/user-attachments/assets/98b3ad2c-571b-4227-aa12-26a66893e843" />

Why this matters:
Healthy Group Policy infrastructure is required for centralized security enforcement.

🔹 Step 16: Create Password Policy GPO

Action:
Created a new domain-wide Group Policy Object named Password Policy.

Screenshot:

<img width="949" height="762" alt="Screenshot 2026-01-16 211749" src="https://github.com/user-attachments/assets/ac1c0539-cc9f-4fcc-81aa-13da295e82e6" />

<img width="749" height="519" alt="Screenshot 2026-01-16 211705" src="https://github.com/user-attachments/assets/9da2122b-3af7-4aa2-8998-d7b8c01141e6" />

<img width="747" height="521" alt="Screenshot 2026-01-16 211644" src="https://github.com/user-attachments/assets/e0e8b2ea-81c8-433c-bf5e-72a5cf6a6086" />

Why this matters:
Using a custom GPO instead of default policies follows enterprise best practices.

🔹 Step 17: Configure Domain Password Policy Settings

Action:
Configured strong password requirements via Group Policy.

Screenshot:

<img width="785" height="573" alt="Screenshot 2026-01-16 211838" src="https://github.com/user-attachments/assets/ce8e7e26-1522-4d75-a577-6cbca2d86af0" />

<img width="782" height="572" alt="Screenshot 2026-01-16 211851" src="https://github.com/user-attachments/assets/2e80c3ba-eebc-4104-9c73-fb1d2d8fe6f2" />

<img width="784" height="575" alt="Screenshot 2026-01-16 211907" src="https://github.com/user-attachments/assets/177c9061-18e4-4180-8118-223fe54cdc48" />

<img width="781" height="557" alt="Screenshot 2026-01-16 211926" src="https://github.com/user-attachments/assets/514cbedd-9a1d-46d3-b42a-eda8340d372c" />

<img width="781" height="572" alt="Screenshot 2026-01-16 211955" src="https://github.com/user-attachments/assets/d67da926-7f6f-4c83-9d75-06eeefefa862" />

<img width="788" height="575" alt="Screenshot 2026-01-16 212014" src="https://github.com/user-attachments/assets/e3eceae1-3913-419d-8144-a6e55f0b0835" />

<img width="785" height="574" alt="Screenshot 2026-01-16 212026" src="https://github.com/user-attachments/assets/26d101e8-d232-4820-87bb-e1b2dd3ac606" />

<img width="783" height="575" alt="Screenshot 2026-01-16 212043" src="https://github.com/user-attachments/assets/19307ef6-e3ee-4c1e-92cf-899e1e063cde" />

<img width="792" height="573" alt="Screenshot 2026-01-16 212057" src="https://github.com/user-attachments/assets/af0e60d7-b7b4-4ff8-a91c-4aa8033f00aa" />

Why this matters:
Strong password policy is a foundational defense against credential compromise and lateral movement.
