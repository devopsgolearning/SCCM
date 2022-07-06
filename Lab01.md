# Module 1: Managing computers and mobile devices in the enterprise
## Lab: Exploring the Configuration Manager tools

<b>Scenario<b>

You have just started your new role as Enterprise Desktop Administrator. To familiarize yourself with the new administrative tools, you plan to explore the Configuration Manager console, and test the search features built into the console. You also plan to identify the Windows PowerShell cmdlets used by Configuration Manager to see how Windows PowerShell can assist you with your administrative tasks. Finally, you plan to verify that the Configuration Manager components are healthy by monitoring the status messages and log files.

# Exercise 1: Searching in the Configuration Manager console
Scenario

In this exercise, you will examine the search functions. The search features in the Configuration Manager console enable you to perform local and global searches.

The main tasks for this exercise are as follows:

Using console filters.
Using search criteria.
Create and save a local node search.
Create and save a global search.
Use saved searches.


## Task 1: Using console filters
Sign in to 20703-1B-LON-CFG-A as ADATUM\Administrator with the password Pa55w.rd.

On the taskbar, click the Configuration Manager console icon.

In the Configuration Manager console, in the Assets and Compliance workspace, click the Users node.

Note: At the top of the results pane, the Users indicator shows that there are 32 items in the results pane.

In the search bar, type ch, and then click Search.

The Users indicator shows that there are 2 items.

## Task 2: Using search criteria
Click the Devices node.

Note: At the top of the results pane, the Devices indicator shows that 8 items are in the results pane.

Click the Add Criteria link. Note the available criteria for devices.

Click Name, and click Add.

In the AND Name row, in the Enter valid characters text box, type LON, and then click Search.

Verify that the Devices indicator now shows that there are 6 items.

Click the Add Criteria link.

Scroll down, click Operating System, and then click Add.

In the AND Operating System row, in the Enter valid characters text box,type Server, and then click Search.

Note: Note that the results contain three servers LON-SVR2, LON-SVR1, and LON-CFG.

In the AND Operating System row, delete Server, and in the Enter valid characterstext box, type Windows, and then click Search.

Note: The results show that all the LON computers run a Windows operating system.

## Task 3: Create and save a local node search
In the Configuration Manager console, click the Assets and Compliance workspace.

Click User Collections.

Double-click All Users. This runs a local node search automatically, and displays all the members of the collection.

Next to the Search button, click Add Criteria, select the Name check box, and then click Add.

In the AND Name row, click contains, and then note the options available for refining the search.

Click starts with, type Adatum\T in the Enter valid characters text box, and then click Search. The results are now limited to the Adatum users whose names begin with T.

On the ribbon, in the Save group, click Save Current Search.

In the Configuration Manager dialog box, type T users, and then click OK.

## Task 4: Create and save a global search
Select the Overview node, and on the ribbon, click All Objects.

In the Search text box, type Configuration Manager, and then click Search.

Note: Notice the different Object Types and Workspaces that the search returns.

On the ribbon, in the Save group, click Save Current Search.

In the Configuration Manager dialog box, in the Search name field, type Configuration Manager Objects, and then click OK.

Close the Configuration Manager console.

## Task 5: Use saved searches
On the taskbar, click the Configuration Manager console icon.

Note: You should notice that the sticky nodes from your previous searches were closed when the console was closed.

On the ribbon, click Saved Searches. This displays a drop-down list of the saved searches categories.

Note: The only available option is global searches: Manage Searches for All Objects.

In the Configuration Manager console, click the Assets and Compliance workspace.

Click the User Collections node.

Click Saved Searches, and click Manage Searches for Current Node. Note that no searches are available, and click Cancel.

Double-click the All Users collection.

On the ribbon, click the Home tab.

Click Saved Searches, and click Manage Searches for Current Node. Note that the T users search is available, and click Cancel.

Click the Device Collections node.

On the ribbon, click Saved Searches, and then click Manage Searches for All Objects.

Click the Configuration Manager Objects search, and click OK.

Note: This displays the same results as before.

Results: At the end of this exercise, you should have performed both local node and global searches. You also should have refined the local node search and saved the custom local node search for future use. Finally, you should have observed the differences between saving a global search and saving a local node search. You can view the expected results in the lab answer key.

# Exercise 2: Using Windows PowerShell with Configuration Manager
<b>Scenario<b>

In this exercise, you will use Windows PowerShell to determine information about Configuration Manager devices, distribution and management points, packages, applications, sites, users, and user and device collections.

The main tasks for this exercise are as follows:

View all commands related to Configuration Manager.
View Configuration Manager information.

## Task 1: View all commands related to Configuration Manager
In the Configuration Manager console, in the upper-left corner, click the Down Arrow, and then click Connect via Windows PowerShell.

When prompted in the Windows PowerShell window, on the keyboard, press A, and then press Enter.

To view all of the cmdlets in the Configuration Manager module for Windows PowerShell, at the Windows PowerShell command prompt, type the following command, and then press Enter:

Get-Command -Module ConfigurationManager | Out-Gridview
Review the commands, and close the Get-Command --Module ConfigurationManager | Out-Gridview dialog box.

## Task 2: View Configuration Manager information
To view a list of devices, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMDevice | ft Name, ADSiteName, SiteCode, DeviceOS
To view a list of distribution points, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMDistributionpoint
To view a list of management points, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMManagementPoint | ft NetworkOSPath, RoleName, SiteCode, RoleCount
To view a list of packages, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMPackage | ft Name, Description, PkgSourcePath
To view a list of applications, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMApplication | ft LocalizedDisplayName, SourceSite
To view a list of sites, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMSite | ft SiteName, SiteCode, ServerName
To view a list of users, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMUser | ft Name, Domain
To view a list of user collections, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMUserCollection | ft Name, Comment, MemberCount
To view a list of device collections, in the Windows PowerShell window, type the following command, and then press Enter:

Get-CMDeviceCollection | ft Name, Comment, MemberCount
Close the Administrator: Windows PowerShell window.

Results: At the end of this exercise, you will have used Windows PowerShell to determine information about Configuration Manager devices, distribution and management points, packages, applications, sites, users, and user and device collections.

# Exercise 3: Using Configuration Manager Service Manager to manage components
Scenario

Configuration Manager Service Manager enables you to control the different services and threads that make up a Configuration Manager site system. You might find that the generated log files are too small, or you might want to change the location to which Configuration Manager saves the log files. Additionally, you might find it beneficial to stop or start a service while troubleshooting a problem. In this exercise, you will explore the options available in the Configuration Manager Service Manager.

The main tasks for this exercise are as follows:

Configure the log file size for a single component.
Manage Configuration Manager components.

## Task 1: Configure the log file size for a single component
Click the Monitoring workspace, and expand the System Status folder.

Click the Component Status node.

On the ribbon, click the Home tab, click the Start drop-down list box, and then click Configuration Manager Service Manager.

Click to expand S01, and click Components.

In the right pane, scroll down, right-click SMS_POLICY_PROVIDER, and then click Logging.

In the Configuration Manager Component Logging -- Single Component dialog box, set the Log Size (MB): scroll box to 5.

From the Log filename field, write down the name of the log file that displays.

To close the Configuration Manager Component Logging -- Single Component dialog box, click OK.

## Task 2: Manage Configuration Manager components
Right-click SMS_POLICY_PROVIDER, and click Select All.

Right-click one of the selected components, and click Query.

To dismiss the Configuration Manager Service Manager dialog box, click OK. You can dismiss the messages about error communicating with components. This message indicates that some components are not configured, which is expected.

Scroll through the list of services, and note that some services are not running. To remove the highlighting, click SMS_POLICY_PROVIDER.

Right-click SMS_POLICY_PROVIDER, and click Stop. Note that the status display does not change.

Right-click SMS_POLICY_PROVIDER, and click Query.

Right-click SMS_POLICY_PROVIDER, and click Start.

Right-click SMS_POLICY_PROVIDER, and click Query.

Close the Configuration Manager Service Manager.

Results: At the end of this exercise, you should have used Configuration Manager Service Manager to manage Configuration Manager components by adjusting the log file sizes, and stopping and starting components.

# Exercise 4: Monitoring Site and Component Status
Scenario

Monitoring the Configuration Manager environment is an important daily task. In this exercise, you will use the Site Status and Component Status nodes to view status messages.

The main tasks for this exercise are as follows:

Examine the Site Status node.
View Site Status messages.
View Component Status messages.

## Task 1: Examine the Site Status node
Click the Site Status node.

Examine the Site Status node.

Note: All of the icons should have a green circle with a white check mark to indicate that they are okay. If there are any red circles with a white X (Critical), notify your instructor.

## Task 2: View Site Status messages
Under Site System Role, right-click the Site server role, click Show Messages, and then click All.

In the Status Messages: Set Viewing Period dialog box, retain the default settings, and then<br /> click OK.

In Configuration Manager Status Message Viewer for , click View, and then click Filter.

In the Message ID: text box, type 5104, and then click OK.

Double-click the status message for the latest milestone from SMS_POLICY_PROVIDER.

Examine the status message, and write down the Process ID information.

To close the Status Message Details dialog box, click OK, and then close the Configuration Manager Status Message Viewer for .

## Task 3: View Component Status messages
Click the Component Status node, and examine the status of the components.

Note: If any of the components display a red circle with a white X, notify your instructor.

Right-click SMS_POLICY_PROVIDER, click Show Messages, and then click All.

In the Status Messages: Set Viewing Period dialog box, retain the default settings, and then click OK.

Note the number of entries between the latest 5104 milestone and the previous 5104 milestone.

Double-click the latest 5104 status message, and examine the status message.

Note: This is the same status that you reviewed in the previous task.

To close the Status Message Details dialog box, click OK.

Close Configuration Manager Status Message Viewer for , and close the Configuration Manager console.

Results: At the end of this exercise, you should have examined the status messages for a site system and a component.

# Exercise 5: Reviewing log files by using the Configuration Manager Trace tool
Scenario

All the Configuration Manager components generate logs files in a standard text file format. You can read these log files in a traditional text reader such as Notepad. However, the Configuration Manager Trace Log tool provides some unique features that make it easier to read a log file. In this exercise, you will explore some of these features, and review the relationship of the log file to the status messages that you reviewed earlier.

The main task for this exercise is as follows:

Use the Configuration Manager Trace Log tool.
Prepare for the next module.

## Task 1: Use the Configuration Manager Trace Log tool
On the taskbar, click the File Explorer icon.

Navigate to the C:\Program Files\Microsoft Configuration Manager\tools folder.

Right-click cmtrace.exe, and click Pin to Taskbar.

On the taskbar, click the Configuration Manager Trace Log Tool icon.

In the Configuration Manager Trace Log Tool, click File, and then click Open.

Scroll down, click the Policypv.log file, and then click Open.

Click Tools, and click Highlight. In the Highlight text box, type 5104, and then click OK.

Click Tools, and click Find. In the Find text box, type the Process ID that you recorded earlier, and then click Find.

To find the next entry, press the F3 key, and repeat until there are no more new responses.

Scroll up until you see the previous highlighted entry. Note the number of entries between the two milestones.

Question: How does the number of events between milestones compare to the number of events shown in the status message viewer?
Answer: Typically, there are more entries in the log file than in the status message viewer.

Click Tools, and click Filter.

In the Filter Settings dialog box, select the Filter when the Entry Text check box.

In the Filter when the Entry Text drop-down list box, click contains.

In the text box next to the Filter when the Entry Text drop-down list box, type the Process ID that you recorded earlier, and then click OK.

Close the Configuration Manager Trace Log tool.

Results: At the end of this exercise, you should have used the Configuration Manager Trace Log tool to review a component log file.

