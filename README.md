# Entra-ID-Security-Lab-Detecting-Authentication-Method-Takeover
An attacker's first move after compromising a password is often to establish persistence by adding their own Multi-Factor Authentication (MFA) method. This lab simulates that critical attack vector and demonstrates how security teams can use Microsoft Entra ID's native audit logs to detect and respond to the activity immediately.

🎯 Project Goal
The primary goal of this exercise is to provide hands-on experience in forensic analysis within Microsoft Entra ID.

Simulation: Successfully simulate an Account Takeover (ATO) by registering a new, unauthorized authentication method to a test user.

Detection: Utilize the Entra ID Audit Logs to isolate and confirm the exact log entry corresponding to the method registration event.

🛠️ Prerequisites
To successfully complete this lab, you need access to the following:

Microsoft Entra ID Test Tenant: Access to an Azure/Entra ID environment where you have the permissions to create users and view Audit Logs (e.g., Security Administrator or Global Reader).

Two User Accounts:

Test User: A standard user account with existing MFA configured (the target of the simulated attack).

Administrator User: An account with permissions to access and filter Audit Logs.

Browser: Access to a private/incognito window for the simulation phase.

💻 Lab Walkthrough (Step-by-Step)
Follow these steps to replicate the simulation and detection process:

Phase 1: Preparation (Target Account Setup)
Ensure your Test User account is enabled and has at least one MFA method already registered (e.g., Authenticator App or Phone).

Phase 2: Simulation (The Account Takeover)
Open a Private/Incognito browser window.

Navigate to the Security Info Portal: https://myaccount.microsoft.com/security-info

Log in using the Test User credentials. Authenticate using the existing MFA method.

Once signed in, click the + Add sign-in method button.

Select a method you can control (e.g., Phone or Microsoft Authenticator) and complete the registration process.

💡 Result: The Test User account now has an unauthorized second MFA method, providing the simulated attacker with persistence.

Phase 3: Detection and Forensic Analysis
Switch back to your Administrator account and log into the Microsoft Entra admin center.

Navigate to Identity > Monitoring & health > Audit logs.

Use the Filter options to isolate the suspicious activity:

Service: User Management

Activity: Add authentication method

Date: Select the timeframe you executed Phase 2.

Review the log results. You should find a log entry where the Target is your Test User.

Click on the log entry to review the full details, including the IP Address, Location, and the specific properties that were modified (e.g., the addition of MobilePhone to the StrongAuthenticationMethods).
