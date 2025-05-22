# Delete Workset

This API deletes an existing workset.  As the workset ID is passed in the URL, you can only delete one workset at a time.  It is run as a DELETE call.  This API can only be run by a user with Admin privileges; all other users will get a return message that they do not have proper authorization to perform this function.

<figure><img src="../../../../../.gitbook/assets/image (8) (1) (1) (1).png" alt=""><figcaption><p>Delete workset API</p></figcaption></figure>

&#x20;The body is the same body as the other simple calls (other than ‘create’ and ‘update’).

&#x20;{

&#x20;   "context": {

&#x20;       "user": "mbj\_test",

&#x20;       "password": "xxxx",

&#x20;       "project": {

&#x20;           "name": "imp\_payments\_demo",

&#x20;           "version": "1.0"

&#x20;       }

&#x20;   }

}

&#x20;Here is the workset listing prior to running this call.  The ID in the call URL is for the ‘cloned\_workset’.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (9) (1) (1) (1).png" alt=""><figcaption><p>Workset list from TDO</p></figcaption></figure>

&#x20;When run, the response contains the result (‘0’ for false and ‘1’ for true).  A response of ‘1’ indicates that the workset has been deleted.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption><p>Results message for delete workset API</p></figcaption></figure>

When viewing the workset listing in TDO, the workset ‘cloned\_workset’ is no longer present.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption><p>TDO workset list showing successful deletion</p></figcaption></figure>
