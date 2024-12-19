# User Maintenance

## ORSON - Test Data Orchestrator

### User maintenance guide&#x20;

Follow the instructions in the installation guide to create an initial admin user if this is your first time using TDO.

&#x20;

To perform user maintenance, you will need to log in with an ID that has ‘admin’ rights.  Users with standard (‘user’) rights can only perform password maintenance on their own ID on the user maintenance screen.

&#x20;

### User security levels

TDO has two user levels and one permissions control:

·       Admin – has rights to perform all user maintenance actions on all users.  Can create new users and delete existing users.  Admin users also have delete permission for all functions in the application amd can remove all locks (coverage set, workset, etc.)

·       User – only has rights to reset their own password.  Cannot create or delete.  Users do not have delete permission for project objects and can only remove locks that are assigned to their user ID.

·       Read-only – a permission control on people with User level rights; they can view all screens in TDO for any project that is assigned to them, but they cannot make any changes.  This level is generally used for new users who have not yet completed training to prevent unauthorized actions on existing projects.



### &#x20;Creating new users

To navigate to the User Maintenance screen, on the menu navigate down to the ‘User Maintenance + LDAP’ section and select ‘Users’ below this.  The User maintenance screen will populate, and will show all enrolled users:

&#x20;

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>User Maintenance Screen (Admin view)</p></figcaption></figure>

&#x20;

To create a new user, click the “+” sign in the bottom right corner of the screen.  The new user enrolment window will open:

&#x20;

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Create User Screen</p></figcaption></figure>

&#x20;

Fill in the fields as follows:

·       First name, last name – user’s given names

·       Username – if this is LDAP, you must use their network ID that will be passed to your SSO program for authentication.  If you are not using LDAP, you can choose the name to give (first initial\_last name, network ID, etc.).

·       Email – enter user’s assigned organizational email address.

·       Password – assign the user an initial password.

o   You may want to use a random password generator to create a strong initial password.

o   We recommend that passwords only be sent to the user (no .cc or .bcc on the note) and that they be sent in a separate email.

o   Include a reminder to the user that they should change their password after their initial sign in.

·       Click the ‘Read Only’ box only if you want to create a ‘read only’ user; otherwise leave blank.

·       On the ‘Role’ line, USER is the default value.  Only grant ADMIN rights to those individuals who need to perform administrative duties (grant/remove access, authorize project access, perform LDAP setup, etc.).  You can change the role by clicking the arrow to the right to open the drop down menu.

&#x20;

Once the user setup is complete, click ‘SAVE’ to save the new enrolment.

&#x20;

### Deleting a user

Only Admins can delete a user. To delete a user, open the User maintenance screen.&#x20;

&#x20;

Navigate to the user you want to delete, and click the checkbox to the left of their name.  Hover your cursor to the right and the edit (pencil) and delete (trash can) icons will become visible.

&#x20;

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Deleting a User</p></figcaption></figure>

&#x20;

Click on the trash can icon to delete the user you have selected.  A warning box will open with the following message:

&#x20;

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Confirmation message pop-up</p></figcaption></figure>

&#x20;

Click ‘OK’ to delete the user and ‘Cancel’ to keep the user.

&#x20;

### Change a user password

If you are using LDAP, passwords will be managed via your organization’s SSO software and not in TDO.  If you are not using LDAP, passwords are changed here.

&#x20;

Navigate to the User Maintenance screen.  Move your cursor to the right of the user you want to update and click on the pencil icon.  The User enrolment / maintenance screen will open.&#x20;

&#x20;

On the password line, remove the old password and enter the new one.  Click ‘SAVE’ to save the password change.  Remember to notify the user of their new temporary password and remind them to change it after their first login.

&#x20;

If you are a User changing your own password, your User Maintenance screen will look like this:

&#x20;

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>User Maintenance Screen (User view)</p></figcaption></figure>

&#x20;

You will only see your ID on this screen, and you will only see the pencil icon to the right.  Click on the pencil icon and the personal maintenance screen will open.  Remove the old password and type in your new password.  Remember to save this password.

&#x20;

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Edit User Screen</p></figcaption></figure>

### Updating project access

By default, any project created by a TDO user (USER or ADMIN rights) will be visible only to that user.  To make it visible to other users they must be assigned project access.

&#x20;

You can only look at/edit projects that you have been given access to use.&#x20;

&#x20;

Only an ADMIN can assign project access.  Individuals with USER access will not see this menu option.

&#x20;

To update project access, navigate to the ‘User Maintenance + LDAP’ section of the menu and select ‘Project Access’.  You will see this window:

&#x20;

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Project Access Screen</p></figcaption></figure>

&#x20;

User names are listed down the left side and projects are listed across the top, in alphabetical order.  You can move right in the project list by using the scroll bar on the bottom of the screen. Each user can only see the projects that are checked here for their user ID.

&#x20;

To add a user to a project, scroll to the desired project and check the box for that user.  Click ‘SAVE’ in the top right corner to save the new assignments.

&#x20;

To remove a user from a project, scroll to the desired project, uncheck the box for that user, and click ‘SAVE’ to save the deletion.
