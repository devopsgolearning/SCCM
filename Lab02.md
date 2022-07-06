# Module 2: Analyzing data using queries, reports, and CMPivot
# Lab A: Creating and running queries
Scenario

You must create queries to help with site management at A. Datum Corporation. You need to create queries for creating collections to help deploy departmental line-of-business applications to users.

# Exercise 1: Creating data queries
Scenario

You have been asked to publish applications based on the Marketing, Production, and Research departments at A. Datum Corporation. You must build and test queries to find the users by department so that you can use these queries to create collections.

The main tasks for this exercise are as follows:

Create a query for Marketing users.
Create a query for Sales or Research users.
Run the user data queries.

## Task 1: Create a query for Marketing users

On LON-CFG, if the Configuration Manager console is not open already, on the taskbar, click the Configuration Manager Console icon.

Click the Monitoring workspace, and then click Queries.

Right-click the Queries node, and then click Create Query.

In the Create Query Wizard, on the General page, in the Name box, type Marketing Users, and then click Import Query Statement.

In the Browse Query dialog box, in the Queries box, click All Users, and then click OK.

In the Create Query Wizard, on the General page, click Edit Query Statement, and then click the Criteria tab.

In the Marketing Users Query Statement Properties dialog box, click New

In the Criterion Properties dialog box, click Select.

In the Select Attribute dialog box, in the Attribute class drop-down list, click User Resource.

In the Attribute drop-down list, click User Group Name, and then click OK.

In the Criterion Properties dialog box, verify that in the Operator box, the is equal to option is selected.

In the Value box, use the Value button to browse to ADATUM\Marketing, and then click OK twice.

In the Marketing Users Query Statement Properties dialog box, click OK.

In the Create Query Wizard, on the General page, click Next.

On the Summary page, click Next, and then on the Completion page, click Close.

## Task 2: Create a query for Sales or Research users
Right-click the Queries node, and then click Create Query.

In the Create Query Wizard, on the General page, in the Name box, type Sales or Research Users, and then click Import Query Statement.

In the Browse Query dialog box, in the Queries box, click All Users, and then click OK.

In the Create Query Wizard, on the General page, click Edit Query Statement, and then click the Criteria tab.

In the Sales or Research Users Query Statement Properties dialog box, click New.

In the Criterion Properties dialog box, click the Criterion Type drop-down list, and then select List of values.

Click Select.

In the Select Attribute dialog box, in the Attribute class list, click User Resource.

In the Attribute list, click User Group Name, and then click OK.

In the Criterion Properties dialog box, verify that in the Operator box, the is in option is selected.

In the Value to add box, type ADATUM\Sales, and then click Add.

In the Value to add box, type ADATUM\Research, click Add, and then click OK.

In the Sales or Research Users Query Statement Properties dialog box, click OK.

In the Create Query Wizard, on the General page, click Next.

On the Summary page, click Next.

On the Completion page, click Close.

## Task 3: Run the user data queries
Right-click the Marketing Users query, and then click Run.

Review the results, which should include 52 users.

Click the Queries node, right-click the Sales or Research Users query, and then click Run.

Review the results, which should include 80 users.

Results: After this exercise, you should have created and tested data queries in Configuration Manager.

# Exercise 2: Creating subselect queries
Scenario

You must create a query to identify all users who are not in the Marketing department so that you can select only these users for certain applications without including the Marketing department.

The main tasks for this exercise are as follows:

Create a query for users who are in the Marketing department.
Create a query for users who are not in the Marketing department.
Prepare for the next lab.

## Task 1: Create a query for users who are in the Marketing department
Right-click the Queries node, and then click Create Query.

In the Create Query Wizard, on the General page, in the Name box, type All Marketing Users.

In the Object Type drop-down list, click User Resource, and then click Edit Query Statement.

In the All Marketing Users Query Statement Properties dialog box, on the General tab, click New

In the Result Properties dialog box, click Select.

In the Select Attribute dialog box, in the Attribute drop-down list, click Unique User Name, and then click OK.

In the Result Properties dialog box, click OK.

In the All Marketing Users Query Statement Properties dialog box, click the Criteria tab, and then click New

In the Criterion Properties dialog box, click Select.

In the Select Attribute dialog box, in the Attribute Class list, click User Resource.

In the Attribute list, click User Group Name, and then click OK.

In the Criterion Properties dialog box, verify that in the Operator box, the is equal to option is selected.

In the Value box, type ADATUM\Marketing, and then click OK.

In the All Marketing Users Query Statement Properties dialog box, click OK.

In the Create Query Wizard, on the General page, click Next.

On the Summary page, click Next.

On the Completion page, click Close.

## Task 2: Create a query for users who are not in the Marketing department

Right-click the Queries node, and then click Create Query.

In the Create Query Wizard, on the General page, in the Name box, type Users Not in the Marketing Group, and then click Import Query Statement.

In the Browse Query dialog box, in the Queries box, click All Users, and then click OK.

In the Create Query Wizard, on the General page, click Edit Query Statement, and then click the Criteria tab.

In the Users Not in the Marketing Group Query Statement Properties dialog box, click New

In the Criterion Properties dialog box, in the Criterion Type drop-down list, click SubSelected values, and then click Select.

In the Select Attribute dialog box, in the Attribute class list, click User Resource.

In the Attribute list, click Unique User Name, and then click OK.

In the Criterion Properties dialog box, in the Operator list, select is not in.

Click Browse, browse to and select the All Marketing Users query, and then click OK.

In the Criterion Properties dialog box, click OK.

In the Users Not in the Marketing Group Query Statement Properties dialog box, click OK.

In the Create Query Wizard, on the General page, click Next.

On the Summary page, click Next.

On the Completion page, click Close.

Right-click the Users Not in the Marketing Group query, and then click Run.

Review the results, which should include 204 users.

Minimize the Configuration Manager console.

Results: After this exercise, you should have created and tested a subselected data query in Configuration Manager.

# Lab B: Configuring SSRS
Scenario

Your organization is planning to migrate all client systems to Windows 10, and the migration project team wants to be able to view daily reports on the migration progress. You must ensure that Configuration Manager administrators and the migration project team can view the reports that Configuration Manager generates. Although Configuration Manager administrators can use the console to view the reports, the migration project team cannot. To ensure that the migration project team can view the reports, you also must ensure that the SQL Server Reporting Services website is functioning.

# Exercise 1: Configuring a reporting services point
Scenario

To implement a reporting services point, you first need to install and configure SSRS. The SQL team installed SSRS, but did not configure it. Therefore, you need to configure it before you can install a reporting services point. After installing the reporting services point, you should test the installation by running reports in both the Configuration Manager console and the SQL Server Reporting Services website.

The main tasks for this exercise are as follows:

Configure SSRS.
Install and configure the reporting services point role.
Test the reporting services point in the Configuration Manager console.
Test the reporting services point in the SQL Server Reporting Services website.
Prepare for the next lab.

## Task 1: Configure SSRS

On LON-CFG, click Start, expand Microsoft SQL Server 2016, and then click Reporting Services Configuration Manager.

In the Reporting Services Configuration Connection dialog box, click Connect.

In Reporting Services Configuration Manager:LON-CFG\MSSQLSERVER, click the Service Account node.

Under Report Server Service Account, in the Network Service drop-down list, verify that the Network Service account is being used.

Click the Web Service URL node, and review the default settings. Click Apply.

On the Database page, click Change Database.

In the Report Server Database Configuration Wizard, on the Action page, ensure that Create a new report server database is selected, and then click Next.

On the Database Server page, click Test Connection. If it is successful, click OK, and then click Next. If it is not successful, contact your instructor.

On the Database page, click Next.

On the Credentials page, click Next.

On the Summary page, click Next.

On the Progress and Finish page, click Finish.

In Reporting Services Configuration Manager:LON-CFG\MSSQLSERVER, click the Web Portal URL node. Verify the URL, and then click Apply.

Click the URL, and then verify that the SQL Server Reporting Services Home page appears.

Close Internet Explorer.

In Reporting Services Configuration Manager:LON-CFG\MSSQLSERVER, click Exit.

## Task 2: Install and configure the reporting services point role
Restore the Configuration Manager console.

Click the Administration workspace, and then expand Site Configuration.

Click Servers and Site Systems Roles.

Right-click \\LON-CFG.Adatum.com, and then click Add Site System Roles.

In the Add Site System Roles Wizard, on the General page, click Next.

On the Proxy page, click Next.

On the System Role Selection page, select the Reporting services point check box, and then click Next.

On the Reporting Services Point page, click Verify.

On the Reporting Services Point page, click Set, and then click New Account.

In the Windows User Account box, click Browse, type Adatum\Administrator, and then click OK.

In the Password and Confirm password boxes, type Pa55w.rd,and then click OK.

On the Reporting services point page, click Next.

Review the Summary page, and then click Next.

On the Completion page, click Close.

Open File Explorer, and then navigate to and open the C:\Program Files\Microsoft Configuration Manager\Logs\srsrpsetup.log file.

Monitor the reporting services point installation by using the srsrpsetup.log file.

## Task 3: Test the reporting services point in the Configuration Manager console
In the Monitoring workspace, expand Reporting, and then click Reports.

Note: You might have to refresh the console until all reports display. You can also monitor the C:\Program Files\Microsoft Configuration Manager\Logs\srsrp.log file for status on the deployed reports. It will take several minutes for the reports to be deployed.

Expand Reports, and then click Users.

Right-click the Users in a specific domain report, and then click Run.

In the Users in a specific domain window, click Values.

In the Parameter Value dialog box, click ADATUM, and then click OK.

In the Users in a specific domain window, click View Report.

Close the Users in a specific domain window, and then minimize the Configuration Manager console.

## Task 4: Test the reporting services point in the SQL Server Reporting Services website

Open Internet Explorer. In the address bar, type http://LON-CFG/Reports, and then press Enter.

Click the ConfigMgr_S01 link, and click the Users folder.

Click the Count users by domain report.

View the results, and then close Internet Explorer.

Results: After this exercise, you should have installed and configured a reporting services point and tested it by opening reports in both the Configuration Manager console and the SQL Server Reporting Services (SSRS) website.

# Lab C: Analyzing the real-time state of a device by using CMPivot
Scenario

Your security manager needs to know the machines on which a specific user is listed as a local administrator. You decide to use CMPivot to analyze and determine the results. You are also having issues with some of your client computers and need to determine which services are in a stopped state. You will use CMPivot to determine the results for these issues also.

# Exercise 1: Using CMPivot to Analyze the current state of devices
Scenario

You need to use CMPivot to find the user who is listed as the local administrator for all the client computers in the collection. You also need to run a CMPivot query to identify the services that are stopped, and then determine the results.

The main tasks for this exercise are as follows:

Create a CMPivot query to analyze local administrative users.
Create a collection based on the CMPivot query results.
Create a user on LON-CL1.
Rerun the CMPivot query to analyze local administrative users.
Export the CMPivot query results to a CSV file.
Run a CMPivot query to identify stopped services.
Prepare for the next module.

## Task 1: Create a CMPivot query to analyze local administrative users

On LON-CFG, if the Configuration Manager console is not already open, on the taskbar, click the Configuration Manager Console icon.

Click the Asset and Compliance workspace, and then click Device Collections.

In the center panel, right-click All Desktop and Server Clients, and then click Start CMPivot.

In the CMPivot (All Desktop and Server Clients) window, click the Query tab.

On the Query tab, in the text box, type Administrators.

Click the Run Query button.

Review the results.

## Task 2: Create a collection based on the CMPivot query results

In CMPivot, select the Query Summary tab.

Next to the Failed row, click 1.

In the Failed Devices window, make a note of the reason for the failure.

Click Create Collection.

In the Create Device Collection Wizard, on the General page, in the Name box, type Computers without PowerShell 5.

Click Next.

On the Membership Rules page, clear the Schedule a full update on this collection check box.

Click Summary.

On the Summary page, click Next.

On the Completed page, click Close.

Close the Failed Devices window.

Close the CMPivot (All Desktop and Server Clients) window.

## Task 3: Create a user on LON-CL1

On LON-CL1, click Start and then type Computer Management.

Click Computer Management.

In the Computer Management window, expand Local Users and Groups.

Right-click Users, and then select New User.

In the New User window, in the User name text box, type Bill.

In the Password text box, type Pa55w.rd.

In the Confirm Password text box, type Pa55w.rd.

Click Create.

Click Close.

Select Users, and then verify that the user account Bill is listed under it.

Right-click Bill, and then select Properties.

Click the Member Of tab.

Click Add….

In the Select Groups window, in the Enter the object names to select text box, type Administrators.

Click OK twice.

## Task 4: Rerun the CMPivot query to analyze local administrative users

On LON-CFG, if the Configuration Manager console is not already open, on the taskbar, click the Configuration Manager Console icon.

Click the Asset and Compliance workspace, and then click Device Collections.

In the center panel, right-click All Desktop and Server Clients, and then click Start CMPivot.

In the CMPivot (All Desktop and Server Clients) window, click the Query tab.

On the Query tab, in the text box, type Administrators.

Click the Run Query button.

Review the results.

Notice that the user Bill is listed on LON-CL1.

## Task 5: Export the CMPivot query results to a CSV file

In the CMPivot (All Desktop and Server Clients) window, on the Query tab, click Export,andthen click To File.

In the Export to File window, under Quick access links, click Desktop.

In the File name text box, type List of who is in the local Administrator group, and then click Save.

On the computer's desktop, double-click the List of who is in the local Administrator group.csv file.

In the How do you want to open this file? window, select Notepad, and then click OK.

Notice these results are the same as the results listed in the CMPivot results pane.

Close Notepad.

## Task 6: Run a CMPivot query to identify stopped services

In the CMPivot (All Desktop and Server Clients) window, on the Query tab, replace the existing text with Services | where State == 'Stopped'.

Note: Make sure that "where" is in lowercase.

Click the Run Query button.

Review the results.

In the CMPivot (All Desktop and Server Clients) window, on the Query tab, replace existing text with Services | where State == 'Stopped'.

Click the Run Query button.

Review the results.

Replace existing text with Services | where State == 'Stopped' | summarize count() by Caption.

Click the Run Query button.

Review the results.

On the Query Results tab, next to the Application Information row, click 1.

Review results in both the query box and the results area.

Results: After this exercise, you should have created a CMPivot query to find all users who are listed as a local administrator for all the client computers in the collection. You should have also created a collection of all the client computers that do not have Microsoft PowerShell 5.0, exported the results of users within the local Administrators group, run a query for services that are stopped, and reviewed a count list of all the stopped services
