# Module 3: Preparing the Configuration Manager management infrastructure

# Lab A: Configuring boundaries and resource discovery
Scenario

A. Datum Corporation has expanded its operations, and you must configure two new network segments that the Configuration Manager infrastructure will manage. The first segment is in Toronto, Canada. The second segment is in Sydney, Australia. The Active Directory administrator has created the appropriate OU and site for the Toronto and Sydney locations, and now you need to configure an appropriate discovery method to discover new users and devices in these locations. You also need to configure boundaries to represent the Toronto and Sydney network ranges and configure the appropriate boundary group settings.

# Exercise 1: Configuring boundaries, boundary groups, and fallback relationships
Scenario

Your manager has asked you to incorporate new locations into the Configuration Manager environment. Your current Configuration Manager configuration already contains a boundary group named London. This boundary group provides automatic site assignment requests for client workstations that are members of associated boundaries. This boundary group also has LON-CFG.Adatum.com configured as a site system server providing distribution point services.
You must configure additional boundaries to represent the Toronto and Sydney locations. You need to associate these boundaries with an appropriate boundary group. The Toronto and Sydney locations will be used for automatic site assignment. The Sydney location will not contain any site system servers initially, but will be configured to use the London boundary group as a fallback for the distribution point site system.

The main tasks for this exercise are as follows:

Configure boundaries.
Configure boundary groups and relationships.

## Task 1: Configure boundaries

On LON-CFG, on the taskbar, click the Configuration Manager Console icon.

In the System Center Configuration Manager console, click the Administration workspace, and then expand Hierarchy Configuration.

Click Discovery Methods, and then click Active Directory Forest Discovery.

On the ribbon, click Properties.

In the Active Directory Forest Discovery Properties dialog box, select the following check boxes:

Enable Active Directory Forest Discovery

Automatically create Active Directory site boundaries when they are discovered

Note: Do not select the Automatically create IP address range boundaries for IP subnets when they are discovered check box.

To close the Active Directory Forest Discovery Properties dialog box, click OK.

When you see the Do you want to run full discovery as soon as possible? message, click Yes.

Note: Before continuing, wait approximately one minute for the discovery to complete and for boundary objects to be created.

Click the Boundaries node, and then refresh the details pane. It might take a minute or two for the results to display.

Note: Do not continue until you see the following boundaries created by the Active Directory Forest Discovery method:

Sydney

Toronto

## Task 2: Configure boundary groups and relationships

In the Administration workspace, expand Hierarchy Configuration, and then click the Boundary Groups node.

Note: Notice the London boundary group in the results pane. This has been preconfigured for the labs in this course.

Right-click London, and then click Properties. Notice that AdatumHQ is the only member of this group.

Click the References tab.

Note: Notice that the S01-Adatum Site is used for site assignment for all clients that are part of the boundaries assigned to this boundary group. LON-CFG.Adatum.com is configured as policy and content location for the boundary group.

To close the London Properties dialog box, click OK.

Right-click Boundary Groups, and then click Create Boundary Group.

In the Name box, type Toronto, and then click Add.

In the Add Boundaries dialog box, select Toronto, and then click OK.

In the Create Boundary Group dialog box, click the References tab, and then click Add.

In the Add Site Systems dialog box, select \LON-CFG.Adatum.com, and then click OK.

Under Site assignment, select the check box next to Use this boundary group for site assignment.

To close the Create Boundary Group dialog box, click OK.

Verify that Toronto now displays in the results pane.

Right-click Boundary Groups, and then click Create Boundary Group.

In the Name box, type Sydney, and then click Add.

In the Add Boundaries dialog box, select Sydney, and then click OK.

In the Create Boundary Group dialog box, click the References tab.

Under Site assignment, select the check box next to Use this boundary group for site assignment.

To close the Create Boundary Group dialog box, click OK.

Verify that Sydney now displays in the results pane.

Configure fallback

In the Administration workspace, click the Boundary Groups node.

Right-click Sydney and then click Properties.

In the Sydney Properties dialog box, click the Relationships tab, and then click Add.

In the Fallback Boundary Groups dialog box, select London.

Under Fallback times (in minutes), change the Distribution point value to 10 minutes.

Click OK to close the Fallback Boundary Groups dialog box. This will ensure that if a client cannot find a distribution point within 10 minutes, it will fall back and use the Distribution point in London.

Click OK to close the Sydney Properties dialog box.

Results: After completing this exercise, you should have created and configured boundaries and boundary groups.

# Exercise 2: Configuring Active Directory discovery methods

Scenario

The Active Directory administrator informed you that a new OU named Toronto Clients has been created, and it contains all of the computers located in Toronto. You need to configure the appropriate discovery methods to discover all the computers and users in the Toronto location. User discovery also must include the Active Directory department attribute. You also need to use an appropriate discovery method to help you configure boundaries and boundary groups, which these new locations will use.

The main tasks for this exercise are as follows:

Configure the Active Directory System Discovery method.
Configure the Active Directory User Discovery method.
Examine the discovered resources.
Prepare for the next lab.

## Task 1: Configure the Active Directory System Discovery method

Click the Administration workspace, expand Hierarchy Configuration, and then click Discovery Methods.

In the results pane, double-click Active Directory System Discovery. Notice that the Enable Active Directory System Discovery check box is selected and that several organizational units (OUs) have been configured.

Click New.

In the Active Directory Container dialog box, click Browse.

In the Select New Container dialog box, click the Toronto Clients container, and then click OK.

Verify that the Recursively search Active Directory child containers check box is selected, and then click OK.

Repeat steps 3 through 6 for Toronto Servers, Sydney Clients, and Sydney Servers.## 

On the Polling Schedule tab, click Schedule, configure the recurrence to take place every 5 days, and then click OK.

Verify that the Enable delta discovery check box is selected and that the interval is configured as 5 minutes, and then click OK.

Right-click Active Directory System Discovery, and then click Run Full Discovery Now.

When Configuration Manager displays the Do you want to run full discovery as soon as possible? message, click Yes.

## Task 2: Configure the Active Directory User Discovery method

On LON-CFG, in the System Center Configuration Manager console, click the Administration workspace, and then expand Hierarchy Configuration.

Click the Discovery Methods node, and then double-click Active Directory User Discovery.

In the Active Directory User Discovery Properties dialog box, verify that the Enable Active Directory User Discovery check box is selected.

Click New, and then click Browse.

In the Select New Container dialog box, click the Adatum container, and then click OK.

Verify that the Recursively search Active Directory child containers check box is selected, and then click OK. 

On the Polling Schedule tab, click Schedule, configure the recurrence to take place every 3 days, and then click OK.

Verify that the Enable delta discovery check box is selected with an interval of 5 minutes.

On the Active Directory Attributes tab, in the Available attributes list, scroll down and click the department attribute, click Add, and then click OK.

Right-click Active Directory User Discovery, and then click Run Full Discovery Now.

When Configuration Manager displays the Do you want to run full discovery as soon as possible? message, click Yes.

## Task 3: Examine the discovered resources

Click the Assets and Compliance workspace.

In the Assets and Compliance workspace, click the Devices node.

In the results pane, right-click TOR-CL2, and then click Properties.

Note: Notice that the client was discovered by using the SMS_AD_SYSTEM_DISCOVERY_AGENT component and that it resides in the Toronto Clients OU.

Click Close.

In the Assets and Compliance workspace, click the Users node. Notice the users that have been discovered in the Adatum domain.

In the Assets and Compliance workspace, click the User Collections node. Notice that the Toronto Users collection shows a member count of 5.

Click Toronto Users, and then on the ribbon, click Update Membership.

In the Configuration Manager dialog box, click Yes.

After the hourglass icon appears on the Toronto Userscollection, with the Toronto Userscollection selected, click Refresh. (You might need to click Refresh additional times until the hourglass icon disappears.) Notice that the Toronto Users collection now shows a member count of 38. If the number does not refresh, first update the All Users and User Groups collection.

Click the Administration workspace, expand the Hierarchy Configuration node, and then click the Active Directory Forests node.

In the preview pane, click the Domains tab. Notice that the Adatum.com domain has been discovered.

Click the Discovery Status tab, and then verify that the discovery has succeeded.

Click the Publishing Status tab, and verify that the publishing has succeeded.

In the results pane, right-click Adatum.com, and then click Show Active Directory Sites. Notice that three sites have been discovered: AdatumHQ, Sydney, and Toronto. Click Back.

In the results pane, right-click Adatum.com, and then click Show IP Subnets. Notice that three IP subnets have been discovered:

172.16.0.0/24

172.16.1.0/24

172.16.2.0/24

Results: After completing this exercise, you should have configured discovery methods and viewed the discovery results.

# Lab B: Configuring user and device collections
Scenario

To support the new Toronto location, you need to create several collections. You must create a device collection that contains only Windows 10 workstations that belong to the Toronto Clients OU. You also need to create a user collection that represents all the users located in Toronto. Additionally, you must ensure that deployments are installed to the Toronto location only during the hours of 8 P.M. and 4 A.M. daily.

# Exercise 1: Creating a device collection
Scenario

You need to create a device collection that contains only Windows 10 workstations that are located in the Toronto OU. A collection named All Windows 10 Workstations already exists, and you need to use queries to create a collection for Toronto workstations.

The main task for this exercise is as follows:

Create the Toronto Windows 10 Workstations collection.

## Task 1: Create the Toronto Windows 10 Workstations collection

If the Microsoft System Center Configuration Manager (Configuration Manager) console is not already open, on LON-CFG, on the taskbar, click the Configuration Manager Console icon in the Taskbar.

In the System Center Configuration Manager console, click the Assets and Compliance workspace, and then click the Device Collections node. Notice that several created collections exist.

Right-click Device Collections, and then click Create Device Collection.

In the Create Device Collection Wizard, in the Name box, type Toronto Windows 10 Workstations.

In the Comment box, type Based upon the Active Directory Toronto Clients organizational unit, and then click Browse.

In the Select Collection dialog box, ensure that Device Collections is selected, select the All Windows 10 Workstations collection, and then click OK.

In the Create Device Collection Wizard, click Next.

On the Membership Rules page, click the Add Rule list, and then click Query Rule.

In the Query Rule Properties dialog box, in the Name box, type Toronto Windows 10 Workstations.

In the Query Rule Properties dialog box, ensure that System Resource is listed, and then click Edit Query Statement.

In the Query Statement Properties dialog box, click the Criteria tab.

On the Criteria page, click New.

In the Criterion Properties dialog box, in the Criterion Type box, ensure that Simple value is selected, and then click Select.

In the Select Attribute dialog box, configure the following options, and then click OK:

Attribute class: System Resource

Alias as:

Attribute: System OU Name

In the Criterion Properties dialog box, ensure that the Operator value is set to is equal to, and then in the Value box, type ADATUM.COM/TORONTO CLIENTS.

To close the Criterion Properties dialog box, click OK.

To close the Query Statement Properties dialog box, click OK.

To close the Query Rule Properties dialog box, click OK.

In the Create Device Collection Wizard, on the Membership Rules page, ensure that both Use incremental updates for this collection and Schedule a full update on this collection are selected, and then click Next.

On the Summary page, click Next.

On the Completion page, click Close.

Ensure that the Device Collections node is selected, and then in the results pane, select the Toronto Windows 10 Workstations collection.

To refresh the collection, press F5, and then double-click the Toronto Windows 10 Workstations collection.

Verify that TOR-CL1 and TOR-CL2 display.

Note: You might need to refresh the console to view the results.

Results: After this exercise, you should have created device collections based on an Active Directory OU and on queries.

# Exercise 2: Creating a user collection
Scenario

You must create a user collection that contains all of the managers in the Toronto office. The Toronto Users collection already exists. For your new collection, you decide to create an include collections rule to include the members of the Toronto Users collection. You then decide to create criteria to filter the membership to show only users in the Managers OU.

The main task for this exercise is as follows:

Create the Toronto Managers collection.

## Task 1: Create the Toronto Managers collection

If the Configuration Manager console is not already open, on LON-CFG, on the taskbar, click the Configuration Manager Console icon in the Taskbar.

In the System Center Configuration Manager console, click the Assets and Compliance workspace, and then click the User Collections node. Notice that several created collections already exist.

Right-click User Collections, and then click Create User Collection.

In the Create User Collection Wizard, in the Name box, type Toronto Managers.

In the Comment box, type Based upon Membership of the Toronto Users collection and the Managers OU in Active Directory, and then click Browse.

In the Select Collections dialog box, ensure that User Collections is selected, select the Toronto Users collection, and then click OK.

In the Create User Collection Wizard, click Next.

On the Membership Rules page, click Add Rule, and then click Query Rule.

In the Name box, type Managers, and then click Edit Query Statement.

In the Query Statement Properties dialog box, click Criteria, and then click New.

In the Criterion Properties dialog box, click Select.

In the Select Attribute dialog box, in the Attribute class list, click User Resource.

In the Attribute list, click User OU Name, and then click OK.

Verify that the Operator displays is equal to, and then click Value.

In the Values dialog box, click ADATUM.COM/MANAGERS, and then click OK four times.

On the Membership Rules page, click Next twice, and then click Close.

In the list of user collections, click Toronto Managers, and then on the ribbon, click Update Membership.

In the Configuration Manager dialog box, click Yes.

With the User Collections node selected, in the results pane, double-click the Toronto Managers collection.

Verify that only the seven Toronto managers are in the collection.

Results: After this exercise, you should have created a user collection that includes and filters members of other collections.

# Exercise 3: Configuring a maintenance window
Scenario

Your final task is to ensure that Toronto deployments can occur only during the hours of 8 P.M. and
4 A.M. each day. You will configure a maintenance window to accomplish this task.

The main task for this exercise is as follows:

Configure a maintenance window for Toronto Windows 10 workstations.
Prepare for the next module.

## Task 1: Configure a maintenance window for Toronto Windows 10 workstations

If the Configuration Manager console is not already open, on LON-CFG, on the taskbar, click the Configuration Manager Console icon in the taskbar.

In the System Center Configuration Manager console, click the Assets and Compliance workspace, and then click the Device Collections node.

Right-click the Toronto Windows 10 Workstations node, and then click Properties.

In the Toronto Windows 10 Workstations Properties dialog box, click the Maintenance Windows tab.

On the Maintenance Windows page, click New.

In the Schedule dialog box, in the Name box, type Deployment Window.

Configure the schedule as follows, and then click OK:

Start: 8 P.M.

End: 4 A.M.

Recurrence pattern: Daily

On the General tab, in the Comment box, type Maintenance Windows: 8 P.M. to 4 A.M.

In the Toronto Windows 10 Workstations Properties dialog box, click OK.

Results: At the end of this exercise, you should have created a maintenance window.

