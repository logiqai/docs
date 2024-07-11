# Manage Users

ASM users with the [User Admin and Customer Admin roles](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2150498307/Configuring+Users#Understanding-Basic-User-Roles) can add, change, or remove user accounts from the Manage Users page. The Manage Users page can be accessed by clicking “Manage > Users” from the ASM navigation bar:



| Column        | Description                                                                                                                                                 |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Username      | Name used to login                                                                                                                                          |
| Name          | Full name of user                                                                                                                                           |
| Customer      | Customer account the user belongs to                                                                                                                        |
| Approved      | Indicates whether the user has been approved                                                                                                                |
| Locked Out    | Indicates whether the user has been locked out                                                                                                              |
| Created       | Timestamp when the account was created                                                                                                                      |
| Last Login    | Last time the user was logged in                                                                                                                            |
| Last Activity | Last time the user was active in the system                                                                                                                 |
|               | Change [Configuration Settings](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2150498307/Configuring+Users#Managing-Other-Users) for the account |

## Roles <a href="#manageusers-roles" id="manageusers-roles"></a>

The Roles section contains user roles which define access to features in Synthetic Monitoring:



| Role Name              | Description                                                                                                                                                              |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Alert Admin            | Manage [alerts](broken-reference) and [alert recipients](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2133759384/Manage+Alerts#Adding-Alert-Recipients)      |
| Alert Editor           | Manage [alerts](broken-reference)                                                                                                                                        |
| Alert Recipient Editor | Manage [alert recipients](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2133759384/Manage+Alerts#Adding-Alert-Recipients)                                     |
| Check Admin            | Manage [checks](broken-reference)                                                                                                                                        |
| Check Power User       | [Manage checks in groups delegated from administrators](broken-reference)                                                                                                |
| Customer Admin         | Administrate the customer account in Apica Synthetic Monitoring                                                                                                          |
| Impersonator           | Allows admins to [impersonate](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2155282433/Navigation#Impersonate) their users                                   |
| Maintenance Admin      | Modify Service Level Agreement settings for checks in the [Maintenance](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2155282433/Navigation#Maintenance) view |
| Panel Editor           | Manage [Apica Panels](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2133754194/Integrating+ASM+Metrics+into+Grafana+Using+Apica+Panels)                       |
| Partner                | Administer partner accounts. This is used for partner API actions through the API                                                                                        |
| Report User            | Manage ad-hoc and subscription [reports](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2132181068/Reports)                                                    |
| User                   | Minimal permissions to view and execute checks                                                                                                                           |
| User Admin             | Manage customer account users                                                                                                                                            |
| Scenario Admin         | Can create, edit and delete [scenarios](broken-reference)                                                                                                                |

## Password <a href="#manageusers-password" id="manageusers-password"></a>

The Password section lets you either create a new password manually or have a password automatically generated and sent out to the user's e-mail address:



| Button          | Description                                                                       |
| --------------- | --------------------------------------------------------------------------------- |
| Change password | Save manual changes                                                               |
| Reset password  | Create a random password and send it to the user using the Greeting Mail Template |

## Mail User <a href="#manageusers-mailuser" id="manageusers-mailuser"></a>

The Greeting Mail Template section allows you to send a mail to the user if you have made changes and would like to inform them of those changes. The following steps explain how to send a greeting e-mail:

1. Navigate to the manage users view:\

2.

    Find the desired user account in the list
3. Click the configure button
4. Edit the Greeting Mail Template, if needed
5. Click Send Mail Now

The user will receive an e-mail with their credentials according to the defined Greeting Mail Template.
