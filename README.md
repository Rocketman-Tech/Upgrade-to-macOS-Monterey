# Upgrade-to-macOS-Monterey

Quick & Easy way to get macOS Monterey Full Installer Package:

https://mrmacintosh.com/macos-12-monterey-full-installer-database-download-directly-from-apple/

_______________________________________________________________________

Step 1: Download/Create FULL macOS Monterey Installer Package. Name Package "Install macOS Monterey Version#.pkg" for this example, we will use "Install macOS Monterey 12.1.pkg"
_______________________________________________________________________

Step 2: Create 2 Smart Computer Groups

Smart Computer Group 1: macOS Update Monterey (Deploy Latest Package)

Create a Smart Group titled "macOS Update Monterey (Deploy Latest Package)" with the 'Criteria' - "Packages Installed by Casper" with the 'Operator' - "Does Not Have" - with the 'Value' of the Package Name, in this example "Install macOS Monterey 12.1.pkg"

Smart Computer Group 2: macOS Update Monterey (Has Latest Package)

Create a Smart Group titled "macOS Update Monterey (Has Latest Package)" with the 'Criteria' - "Packages Installed by Casper" with the 'Operator' - "Has" - with the 'Value' of the Package Name, in this example "Install macOS Monterey 12.1.pkg"

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
