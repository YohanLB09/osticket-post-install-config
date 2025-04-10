# <p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" height="100%" width="100%" alt="Setting Up in Azure"/>
<br />

<h1>osTicket - Post-Install Configuration</h1>

<h2>Description</h2>
In this guided lab, we will configure osTicket settings, so it can be used properly as a ticketing system. It consists of setting up multiple agents along with their departments, roles, and permissions. As well as, configuring SLAs (Service Level Agreements), help topics, and users.<br/>
<br/>

<h2>Environments and Technologies</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- osTicket


<h2>Operating Systems Used </h2>

- Windows 10 Pro, version 22H2


<h2>High-Level Steps</h2>

- Step 1: Login to osTicket
- Step 2: Configure Roles
- Step 3: Configure Departments
- Step 4: Configure a Team
- Step 5: Verify permissions for ticket creation
- Step 6: Configure Agents
- Step 7: Configure Users
- Step 8: Configure SLA
- Step 9: Configure Help Topics


<h2>Configuration Steps</h2>

<h3>Step 1: Login to osTicket</h3>
<p>
<img src="https://i.imgur.com/jSnJGrL.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Back in your Windows VM, login to the admin/agent portal of osTicket: http://localhost/osTicket/scp/login.php. 

It's important to distinguish between the admin panel and the agent panel; the admin panel allows to configure back-end configurations and management while the agent panel is where support agents handle tickets.
</p>
<br />




<h3>Step 2: Configure Roles</h3>
<p>
<img src="https://i.imgur.com/NKevdUm.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Navigate to the Admin panel, and click on "Admin Panel" -> "Agents" -> "Roles"

From here, you can explore the different roles and set of permissions assigned to each role.
Read more about roles here: https://docs.osticket.com/en/latest/Admin/Agents/Roles.html
</p>
<br />

<p>
<img src="https://i.imgur.com/CRGHMGM.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-To create a new role, click on "Add New Role".

-Specify a name for a new privilege role (ex: Rootuser) -> navigate to the "Permissions" tab, check all boxes to assign all permissions for "Tickets", "Tasks", and "Knowledgebase" -> click on "Add Role".

Configuring a Role specifies what permissions the agent has access to for handling tickets, tasks, and knowledgebase. 
</p>
<br />




<h3>Step 3: Configure Departments</h3>
<p>
<img src="https://i.imgur.com/ggzYRkR.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-From within the Admin panel, navigate to "Agents" -> click on "Add New Departments".

-Under the "Settings" tab, specify a name for the department (ex: SysAdmins), leave all other configurations as default (for now).

-Click on "Create Dept".

Configuring a Department in osTicket determines which types of tickets the agents in that department will handle. It ensures that tickets are routed to the right team based on their category.
Read more about Departments here: 
https://docs.osticket.com/en/latest/Admin/Agents/Departments.html
</p>
<br />


<p>
<img src="https://i.imgur.com/AbWX8xc.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Additionally, we need to delete the "Maintenance" Departement to ensure that no tickets get auto-assigned to this department when practicing troubleshooting ticket handling in the next lab. 
</p>
<br />




<h3>Step 4: Configure a Team</h3>
<p>
<img src="https://i.imgur.com/zzvTwnX.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-From within the Admin panel, navigate to "Agents" -> click on "Teams" -> "Add New Team".

-Under the "Team" tab, create a name (ex: Level II Support). Leave all other configurations as default.

-Click on "Create Team".

Configuring a Team allows to pull agents from different Departments to collaborate on specific tickets without changing departments assignments.
Read more about Teams here: 
https://docs.osticket.com/en/latest/Admin/Agents/Teams.html
</p>
<br />




<h3>Step 5: Verify permissions for ticket creation</h3>
<p>
<img src="https://i.imgur.com/1bMMMMk.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-From within the Admin panel, navigate to the "Settings" tab -> click on "Users".

-Make sure the "Registration Method" box in unchecked. This will ensure that any end-user, including the one without registered accounts, can create their own tickets.
</p>
<br />




<h3>Step 6: Configure Agents</h3>
<p>
<img src="https://i.imgur.com/TAZviNx.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-From within the admin panel, navigate to the "Agents" tab -> click on "Add New Agent".

-Create a name, email address, username.

-To set the password, click on "Set Password" -> uncheck the box for "Send the agent a password reset email" -> uncheck the box for "Require password change at next login" -> click on "Set".

-Under the "Access" tab, assign the first agent to the "SysAdmins" Primary Department, and select "rootuser" for the Role.

-Under the "Teams" tab, select "Level II Support", and click on "Create".

-Repeat the same process for a second agent, but create a different profile with different specifications (Account informations, Access specifications, Permissions, Teams).

Configuring an agent allows them to manage tickets, respond to customer inquiries, and access specific help topics based on assigned roles and departments.
Read more about Agents here: 
https://docs.osticket.com/en/latest/Admin/Agents/Agents.html
</p>
<br />




<h3>Step 7: Configure Users</h3>
<p>
<img src="https://i.imgur.com/dqAQD4n.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Navigate to the Agent Panel -> "Users" tab -> click on "Add User".

-Create an email address and a full name (just the first name is enough for this lab).

-Click on "Add User".

-Create a second user.

Configuring a user allows them to create tickets, check a ticket's status, and interact with support agents.
Read more about Agents here: 
https://docs.osticket.com/en/latest/Agent/Users/User%20Directory.html
</p>
<br />




<h3>Step 8: Configure SLA</h3>
<p>
<img src="https://i.imgur.com/p2SLTtV.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-Navigate back to the Admin panel -> click on the "Manage" tab -> "SLA"-> "Add New SLA Plan".

-Specify the name, grace period (in hours), and schedule for 3 different SLA plans like so (leave other configurations as default):
1) Name: "Sev-A" / Grace Period: "1" / Schedule: "24/7" -> click on "Add Plan".
2) Name: "Sev-B" / Grace Period: "4" / Schedule: "24/7" -> click on "Add Plan".
3) Name: "Sev-C" / Grace Period: "8" / Schedule: Business Hours -> click on "Add Plan".

Configuring SLA (Service Level Agreements) allows to specify the time and response objectives for tickets based on priority, department, or help topic.
Read more about SLA here: https://docs.osticket.com/en/latest/Admin/Manage/SLA%20Plans.html
</p>
<br />




<h3>Step 9: Configure Help Topics</h3>
<p>
<img src="https://i.imgur.com/xpvIE46.png" height="100%" width="100%" alt="Configuration step"/>
</p>
<p>
-From within the Admin panel, under the "Manage" tab, click on "Help Topics" -> "Add New Help Topic".

-Add the following help topics (leave other configurations as default):
1) Topic: "Business Critical Outage" / Parent Type: "Report a Problem"
2) Topic: "Personal Computer Issues" / Parent Type: "Report a Problem"
3) Topic: "Equipment Request" / Parent Type: "General Inquiry"
4) Topic: "Password Reset" / Parent Type: "Report a Problem"
5) Topic: "Network issues" / Parent Type: "Report a Problem"
6) Topic: "Other" / Parent Type: "General Inquiry"

Configuring Help Topics in osTicket involves setting up predefined troubleshooting subjects that guide users when creating a ticket. This helps structure the ticketing process by allowing users to select the nature of their issue, ensuring it is categorized correctly without needing to understand the internal workflow of the support team.
</p>
<br />




<h2>osTicket Configuraton Setup Completed!</h2>

<b>We've successfully set up multiple agents with their respective departments, roles, and permissions. Additionally, we've configured SLAs (Service Level Agreements), help topics, and users. In the next lab, we will create and simulate different ticket handling scenarios using multiple agents and users. Next lab: https://github.com/YohanLB09/osticket-ticket-simulation/blob/main/README.md</b>
<br />
<br />
</p>




