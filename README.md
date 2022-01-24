# Upgrade-to-macOS-Monterey

Quick & Easy way to get macOS Monterey Full Installer Package:

https://mrmacintosh.com/macos-12-monterey-full-installer-database-download-directly-from-apple/

_______________________________________________________________________

Step 1: Download/Create FULL macOS Monterey Installer Package. Name Package "Install macOS Monterey Version#.pkg" for this example, we will use "Install macOS Monterey 12.1.pkg" - Upload package to Jamf Pro Server.
_______________________________________________________________________

Step 2: Create 2 Smart Computer Groups

Smart Computer Group 1: Title "macOS Update Monterey (Deploy Latest Package)"
- Set 'Criteria' to "Packages Installed by Casper" 
- Set 'Operator' to "Does Not Have"
- Set 'Value' to the Package Name, in this example "Install macOS Monterey 12.1.pkg"

Smart Computer Group 2: macOS Update Monterey (Has Latest Package)
- Set 'Criteria' to "Packages Installed by Casper" 
- Set 'Operator' to "Has"
- Set 'Value' to the Package Name, in this example "Install macOS Monterey 12.1.pkg"

*IMPORTANT* - FOR BOTH SMART GROUPS, ADD CRITERIA TO EXCLUDE MACHINES ALREADY ON macOS MONTEREY OR THE VERSION YOU ARE UPGRADING TOO)
_______________________________________________________________________

Step 3: Create 3 Policies

Policy 1: Title "macOS Update : Monterey Deployment"
- Set Scope to Smart Computer Group "macOS Update Monterey (Deploy Latest Package)"
- Set Frequency to "Once Per Computer" with preferred amount of retrys on failure.
- Set Trigger to "Recurring Check-In & Network State Change"
- Add macOS Installer Package to Packages
- Run an Inventory Update post Package

Policy 2: Title "macOS Update : Monterey Installation"
- Set Scope to Smart Computer Group "macOS Update Monterey (Has Latest Package)"
- Set Frequency to "Once Per Computer" with preferred amount of retrys on failure.
- Set Trigger to "Recurring Check-In & Network State Change"
- Add the script "macOS Update: Monterey: 1: Determine Architecture"
- Run an Inventory Update post Script

*Optional*

User Interaction
- Start Message "macOS Requires an operating system update. This update may take several hours & your computer will restart. Please save all of your work. If now is not a good time, you may defer this update to begin at a more convenient time."
- Deferal Type & Duration

Policy 3: Title "macOS Update : Monterey Installation M1"
- Set Scope to Smart Computer Group "macOS Update Monterey (Has Latest Package)"
- Set Frequency to "Once Per Computer" with preferred amount of retrys on failure.
- Set Trigger to "Custom" with Custom Trigger being 'installMonterey'

Scripts Provided Below are predicated upon the environment, if your end users are all admins, Scripts 2 & 3 are what you use, if you have a local management admin, use script 4. If you have a mixed environment, adding all 3 scripts will be a great catch all.

- Add the script "macOS Update: Monterey: 2: End User Is Admin: Prompt for Password"
- Add the script "macOS Update: Monterey: 3: End User Is Admin: Install with End User Credentials"
- Add the script "macOS Update: Monterey: 4: Local Backdoor Admin: Install with Local Backdoor Admin Credentials"
