# Manage Power Users

In the **Manage Power Users** view you can configure the behavior for the [Check Power User](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2135396436) role.



A user can be associated with a Monitor Groups as either a co-owner as a regular user. (This can be defined in the [Edit Users](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2133758795) view.)

The permissions can be separately configured for these two types of association.



This configuration applies to the entire customer account.

|                | Column                                                      | Description                                                                                                                                                                                             |
| -------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Check Type     | Introduction to Apica Check Types.                          | <p><br></p>                                                                                                                                                                                             |
| Create         | Allows user to create checks of this type.                  | Only in `user` or `co-owner` monitor groups. Checks must be placed in a monitor group, ungrouped checks are not allowed.                                                                                |
| Edit           | Allows user to change the settings for checks of this type. | An edit button next to an item indicates that user edit permissions are [Detailed Configuration](https://apica-kb.atlassian.net/wiki/spaces/ASMDOCS/pages/2133760783). Checks cannot be edited in bulk. |
| Delete         | Allows user to remove checks of this type.                  | Only in `user` or `co-owner` monitor groups.                                                                                                                                                            |
| Enable/Disable | Allows user to turn checks of this type on an off.          | <p><br></p>                                                                                                                                                                                             |

In addition to these settings, the following restrictions apply to any Power Users:

* Only checks in associated monitor groups can be run.
* Checks cannot be cloned.

## Managing User Groups <a href="#managepowerusers-managingusergroups" id="managepowerusers-managingusergroups"></a>

The settings configured for **User** applies to all Monitor Groups where the Check Power User is not designated Co-Owner.

* A user can be associated with a Monitor Groups as either a co-owner or a regular user.
* The permissions can be separately configured for these two types of associations.



The Power User role represents certain trusted colleagues as appointed by the Administrators.

* Power Users are assigned as co-owners of Top Groups where they can create or edit checks according to a set of restrictions.
* The restrictions are set by the Administrators and put limits on which settings are available to the Power Users when creating and editing checks.
* Being a co-owner of a group gives the Power Users elevated rights for checks within that group according to the settings set by the Administrator.
* It is also possible to set up the user rights for all groups that the Power User is not co-owner of, so-called non-co-owned groups.

## Managing Co-Owned User Groups <a href="#managepowerusers-managingco-ownedusergroups" id="managepowerusers-managingco-ownedusergroups"></a>

The settings configured for **Co-Owner** applies to all [Monitor Groups](https://apica-kb.atlassian.net/wiki/pages/createpage.action?spaceKey=ASMDOCS\&title=Monitor%20Groups\&linkCreation=true\&fromPageId=2133760760) where the Check Power User is designated Co-Owner. The restrictions are set by the Administrators and puts limits on which settings are available to the Power Users when creating and editing checks. Being a co-owner of a group gives the Power Users elevated rights for checks within that group according to the settings set by the Administrator. It is also possible to set up the user rights for all groups that the Power User is not co-owner of, so-called non co-owned groups.



## Configuring Detailed Edit Check Settings for Power Users <a href="#managepowerusers-configuringdetailededitchecksettingsforpowerusers" id="managepowerusers-configuringdetailededitchecksettingsforpowerusers"></a>

The Edit settings allowed to be changed by Check Power Users can be restricted on a per-check-type basis. To change the check information that a Power User is allowed to edit, press the Notepad icon next to the check mark in the Edit column on the Manage Power Users page:



The page will show a list of all the check fields for that check type. Settings that can be changed by the Check Power User are indicated with a green background. Each configurable option can be enabled or disabled with the checkbox next to it:

