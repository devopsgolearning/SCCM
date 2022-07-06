# Module 4: Deploying and managing the Configuration Manager client

# Lab A: Deploying the Configuration Manager client software

Scenario

System Center Configuration Manager has been deployed in your environment. You now need to configure the environment in your headquarters for client push installation, including the roles that the client installation requires. Then, you need to push the Configuration Manager client software on the local network.

# Exercise 1: Preparing the site for client installation

Scenario

Before deploying the Configuration Manager client software, you decide to deploy a fallback status point so that the installation process can send state messages and report problems with the installation.

The main task for this exercise is as follows:

Install a fallback status point.

## Task 1: Install a fallback status point

Sign in to 20703-1B-LON-CFG-A as ADATUM\Administrator with the password Pa55w.rd.

On the taskbar, click Configuration Manager Console.

In the Configuration Manager console, click the Administration workspace, expand Site Configuration, and then click Servers and Site System Roles.

In the results pane, right-click \LON-CFG.Adatum.com, and then click Add Site System Roles.

In the Add Site System Roles Wizard, on the General page, click Next.

On the Proxy page, click Next.

On the System Role Selection page, select the Fallback status point check box, and then click Next.

Review the Fallback Status Point page, and then click Next.

Review the Summary page, and then click Next.

Note: The summary page should list existing settings plus the fallback status point. If there is an issue, click Previous to change the settings.

Review the Completion page, and then click Close.

Note: The completion page should show that everything installed successfully. If it does not, contact your instructor.

After clicking Close, the details pane should display the fallback status point that you have added to the LON-CFG server.

In the preview pane, right-click the Management point role, and then click Properties.

Select the Generate alert when the management point is not healthy check box.

In the Management point Properties dialog box, click OK.

Right-click Sites, and then click Hierarchy Settings.

In the Hierarchy Settings Properties dialog box, select the Use a fallback site check box, and then click OK.

Results: After completing this exercise, you should have installed and configured a fallback status point.

# Exercise 2: Deploying the Configuration Manager client software by using client push installation

Scenario

Before you can push the Configuration Manager client software to discovered systems, you need to configure the properties for the installation. After you push the client software to a computer system, use log files and reports to verify that the client installed successfully.

The main tasks for this exercise are as follows:

Configure the client push installation properties.
Perform a client push installation.
Verify the client installation.
Prepare for the next lab.

## Task 1: Configure the client push installation properties

In the Configuration Manager console, in the Administration workspace, click the Sites node.

On the ribbon, click Settings, click the Client Installation Settings drop-down list box, and then click Client Push Installation.

Click the Accounts tab.

Verify that Adatum\ClientInstall is configured as a Client Push Installation account. This is pre-configured for the lab and is not a default account.

Click the Installation Properties tab.

On the Installation Properties tab, in the Installation properties box, after SMSSITECODE=S01 type the following on one line each separated by a space:

FSP=LON-CFG DISABLESITEOPT=True SMSCACHEDIR=Cache SMSCACHEFLAGS=MAXDRIVE
In the Client Push Installation Properties dialog box, click OK.

## Task 2: Perform a client push installation

Click the Assets and Compliance workspace, and then click Devices.

Right-click LON-CL1, and then click Install Client.

In the Install Configuration Manager Client Wizard, on the Before You Begin page, click Next.

Review the Installation Options page, and then click Next.

Review the Summary page, verify that one resource is going to be installed, and then click Next.

On the Completion page, click Close.

Minimize the Configuration Manager console.

## Task 3: Verify the client installation

Switch to LON-CL1, and then click the desktop.

Right-click the taskbar, click Task Manager, click More details, and then click Details.

Wait for the ccmsetup.exe process to complete, and then verify that CcmExec.exe displays in the list of processes.

After ccmsetup.exe has completed, close Windows Task Manager.

In the File Explorer, open the C:\Windows\ccmsetup\logs\ccmsetup.log file.

In the log file, click Edit and then click Find, search for Successfully. If the installation was successful, you will see Installation succeeded near the end of the file.

In the ccmsetup.log -- Notepad window, search for Installing. Verify that entries for each prerequisite display as installed by ccmsetup.

In the ccmsetup.log -- Notepad window, search for Fallback. Verify that entries for the state messages display as sent by ccmsetup.

Close the ccmsetup.log -- Notepad window.

Click Start button, and then type Control Panel.

Click Control Panel.

In Control Panel, click System and Security.

Click Configuration Manager, and then on the General tab, verify that the Site code shows SMS: S01.

Click the Components tab. Verify that most of the components display as Installed and as Enabled. Verify that the Software Metering Agent is Enabled.

Note: This indicates that the client has downloaded client settings from a management point.

Click the Site tab. Verify that the DISABLESITEOPT=True that was configured in the installation properties was applied, and that the Configure Settings button is unavailable.

Click the Cache tab, and then click the Configure Settings button.

Verify that SMSCACHEDIR=Cache SMSCACHEFLAGS=MAXDRIVE that was configured in the installation properties was applied, and that the Cache folder is set to C:\Cache\ccmcache.

Click OK to close the Configuration Manager Properties dialog box.

Results: After completing this exercise, you should have installed a client using the client push method, and verified that the client was installed with your custom settings.

# Lab B: Configuring and monitoring client status

Scenario

You need to monitor client activity and health within your Configuration Manager environment. To ensure that you receive timely notifications, you want to increase the reporting intervals for client health to every three days. Additionally, you want to be able to identify the last time someone signed in to an inactive client. Finally, you would like to receive an alert if more than five percent of your clients are inactive or unhealthy.

# Exercise 1: Configuring and monitoring client health status

Scenario

You have decided to use the Client Status feature both to monitor the status of your Configuration Manager clients, and to verify client remediation.

The main tasks for this exercise are as follows:

Configure client status settings.
Trigger a client health evaluation.
Use Client Check.
Use Client Activity.
Configure alerts.
Test client health automatic remediation.
Prepare for the next lab.

## Task 1: Configure client status settings

On LON-CFG, on the taskbar, click Configuration Manager Console.

Click the Monitoring workspace, and then click the Client Status folder.

Right-click Client Status, and then click Client Status Settings.

In the Client Status Settings Properties dialog box, set all of the evaluation periods to 3 days.

In the Client Status Settings Properties dialog box, click OK.

## Task 2: Trigger a client health evaluation

Switch to LON-CL1, and if necessary, sign in as Adatum\Administrator with the password Pa55w.rd.

Right-click the Start button, and then click Computer Management.

Expand Task Scheduler, expand Task Scheduler Library, expand Microsoft, and then click Configuration Manager.

Right-click Configuration Manager Health Evaluation, and then click Run.

Wait for the Last Run Result to change to The operation completed successfully. You might have to click Refresh to view updated results.

Note: The client health report could take up to 10 minutes before status is reported back to the site server, stored in the database, and is ready to update the display.

## Task 3: Use Client Check

Switch to 20703-1B-LON-CFG-A.

Verify that the Configuration Manager console is still open to the Monitoring workspace, and to the Client Status folder.

Right-click Client Status, and then click Refresh Client Status.

In the results pane, click the Client Check link.

On the Client Check page, review the charts. You may need to click the Refresh Client Status button to refresh the results.

On the Client Check pie chart, click the green section.

In the Clients that passed client check from All Desktops and Server Clients temporary node, examine the contents of the Summary tab.

Click the Client Check Detail tab. Verify whether the client failed any rules.

## Task 4: Use Client Activity

In the Configuration Manager console, click the Monitoring workspace, and then click the Client Activity node.

Review the charts on the Client Activity page.

On the Client Activity pie chart, click the green section.

Click the Client Activity Detail tab, and then examine the client summary information.

## Task 5: Configure alerts

In the Configuration Manager console, click the Assets and Compliance workspace, click the Device Collections node.

Right-click the All Desktop and Server Clients collection, and then click Properties.

In the All Desktop and Server Clients Properties dialog box, click the Alerts tab, and then
click Add.

In the Add New Collection Alerts dialog box, under Client status, select the following check boxes, and then click OK:

Client check pass or no results for active clients falls below threshold (%)

Client remediation success falls below the threshold (%)

Client activity falls below threshold (%)

In the All Desktop and Server Clients Properties dialog box, under Conditions, select Client check, and then in the text box for threshold value, ensure that it is set to 95.

Repeat step 5 for both Client remediation and Client activity.

In the All Desktop and Server Clients Properties dialog box, click OK.

## Task 6: Test client health automatic remediation

Switch to LON-CL1.

In Computer Management, expand Services and Applications, and then click Services.

Scroll down and double-click Windows Management Instrumentation.

In the Windows Management Instrumentation Properties(Local Computer) dialog box, click the Stop button.

In the Stop Other Services dialog box, click Yes.

In the Startup Type list, click Disabled.

In the Windows Management Instrumentation Properties(Local Computer) dialog box, click OK.

Click the SMS Agent Host service.

Question: What is its status?
Answer: Its status is blank (Stopped).

Click the IP Helper service.

Question: What is its status?
Answer: Its status is blank (Stopped).

Expand Task Scheduler, expand Task Scheduler Library, expand Microsoft, and then click Configuration Manager.

Right-click Configuration Manager Health Evaluation, and then click Run.

Wait for the Last Run Result to change to The operation completed successfully. This will take a few minutes to complete, and you might need to refresh the display.

Click Services.

Scroll down, and then click Windows Management Instrumentation.

Question: What is the status and startup type for the Windows Management Instrumentation service?

Answer: The status is Running (Started), and the startup type is Automatic.

Question: What is the status for the SMS Agent Host service?

Answer: The status is Running (Started).

Question: What is the status for the IP Helper service?

Answer: The Status is blank (stopped).

Close all open windows, and then sign out of LON-CL1.

Results: After this exercise, you should have configured client status monitoring and verified client remediation.

# Lab C: Managing client settings

Scenario

You have recently deployed Configuration Manager to your environment. As part of your initial deployment, you have decided that you want to temporarily increase the frequency with which the clients will download new policy settings and report state information. You also have decided to disable the power management feature at all locations. Additionally, you have decided not to collect software-metering information from the desktop systems in London.

# Exercise 1: Configuring client settings

Scenario

You need to create a new collection for the London clients so that you can apply the custom configuration settings to them. To do this, you will configure a custom client device setting for the London clients, and then apply the settings.

The main tasks for this exercise are as follows:

Create a London client collection.
Configure the Default Client Settings.
Create a custom setting for a client device.
Deploy a custom client device setting.
Verify client device settings.

## Task 1: Create a London client collection

On LON-CFG, on the taskbar, click Configuration Manager Console.

In the Configuration Manager console, click the Assets and Compliance workspace, and then click the Device Collections node.

Right-click Device Collections, and then click Create Device Collection.

In the Create Device Collection Wizard, in the Name text box, type London Clients.

Next to the Limiting collection field, click the Browse button.

Select the All Desktop and Server Clients collection, and then click OK.

In the Create Device Collection Wizard, click Next.

On the Membership Rules page, in the Add Rule list, click Direct Rule.

In the Create Direct Membership Rule Wizard, click Next.

In the Attribute name text box, select Name. In the Value text box, type LON-CL1, and then click Next.

On the Select Resources page, select LON-CL1, and then click Next.

On the Summary page, click Next.

On the Completion page, click Close.

In the Create Device Collection Wizard, on the Membership Rules page, click Next.

On the Summary page, click Next.

On the Completion page, click Close.

Click Refresh, and verify that the results pane for the Member Count column displays 1 member in the London Clients collection. You may need to click Refresh several times over the course of 5 minutes before this information is displayed.

Double-click the London Clients collection, and then verify that LON-CL1 is a member.

## Task 2: Configure the Default Client Settings

In the Configuration Manager console, click the Administration workspace, and then click the Client Settings node.

Right-click the Default Client Settings policy, and then click Properties.

In the Default Settings dialog box, click the Client Policy setting.

Set the Client policy polling interval (minutes) to 30 minutes.

Click the Power Management setting.

Set Allow power management of devices to No.

Click the State Messaging setting.

Set the State message reporting cycle (minutes) to 10 minutes.

Click OK to accept changes.

## Task 3: Create a custom setting for a client device

Right-click the Client Settings node, and then click Create Custom Client Device Settings.

In the Create Custom Client Device Settings dialog box, in the Name text box, type LON Desktop Systems.

In the Description text box, type Client settings for all LON Desktop Systems.

In the Select and then configure the custom settings for client devices section, select the Software Metering check box.

Click the Software Metering node.

Set Enable software metering on clients to No.

Click OK to accept changes, and close the Create Custom Client Device Settings dialog box.

## Task 4: Deploy a custom client device setting

Right-click the LON Desktop Systems client setting, and then click Deploy.

In the Select Collection dialog box, click London Clients, and then click OK.

In the preview pane, click the Deployments tab to verify the assignment.

## Task 5: Verify client device settings

Switch to LON-CL1, and if not already signed in, sign in as Adatum\Administrator with the password Pa55w.rd.

If the Control Panel is not open, right-click the Start button, and then click Control Panel.

In Control Panel, click System and Security, and then click Configuration Manager.

Click the Actions tab, click Machine Policy Retrieval & Evaluation Cycle, and then click Run Now.

When a message box displays, click OK.

In the Configuration Manager Properties dialog box, click the Components tab.

Verify that the Power Management Agent is Installed, and that the Software Metering Agent is Disabled.

Close all open windows.

Results: After this exercise, you should have created a collection, and configured Default Client Settings. You also should have created and assigned a custom client device setting. Additionally, you should have verified that both settings were applied to a system.

# Exercise 2: Performing management operations

Scenario

You need to refresh the computer policy on LON-CFG and you need to use the Run Scripts feature to create a new folder named Files and a text document named Test.

The main tasks for this exercise are as follows:

Perform management operations.
Run scripts on target devices.
Prepare for the next module.

## Task 1: Perform management operations

On LON-CFG, on the taskbar, click Configuration Manager Console.

In the Configuration Manager console, click the Assets and Compliance workspace, and then click the Devices node.

Select LON-CFG.

Right-click LON-CFG and then point to Client Notification. Take note of the management tasks that can be run.

Click Download Computer Policy.

Click OK.

## Task 2: Run scripts on target devices

In the Configuration Manager console, click the Administration workspace.

Expand Site Configuration, and then select Sites.

In the ribbon, click Hierarchy Settings.

On the General tab, remove the check mark next to Script authors require additional script approver. Note that this is only done in this lab so that the administrator can approve the script manually.

Click OK to close the Hierarchy Settings Properties box.

In the Configuration Manager console, click the Software Library workspace.

Click the Scripts node and then on the ribbon, click Create Script.

In the Create Script Wizard, next to Script name enter Create Folder and File.

Open File Explorer and then browse to E:\Software.

Open NewFolder.txt and copy the text.

In the Create Script window, paste the copied text. Click Next.

On the Script Parameters page, click Edit. Take notice of how you can change default values.

Click Cancel and then click Next.

On the Summary page, click Next and then click Close. Notice that the Approval State shows Waiting for approval.

Select the Create Folder and File script and then in the ribbon click Approve/Deny. The Approve or Deny Script Wizard starts. Click Next twice.

On the Script Approval page, select Approve and then click Next.

On the Summary page, click Next and then click Close.

In the Configuration Manager console, click the Assets and Compliance workspace.

Click the Devices node.

Select LON-CFG, right click LON-CFG and then click Run Script.

In the Run Script Wizard, select the Create Folder and File script and then click Next.

Next to FileName type C:\Files\Test.txt.

Next to FolderName type C:\Files.

Click Next.

On the Summary page, click Next.

Take note of the Script status. Click Close.

Click the Monitoring workspace and then click Script Status.

Select the Create Folder and File script and notice its Overall Script Execution State.

In the ribbon, click Show Status to view the script details.

Click OK to close the status information.

Results: After this exercise, you should have refreshed the computer policy on LON-CFG and used the Run Scripts feature to create a folder and file within the folder.

