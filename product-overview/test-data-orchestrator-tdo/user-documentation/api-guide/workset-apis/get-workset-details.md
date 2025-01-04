# Get Workset Details

This call returns details on a specific workset.  It is very similar to the ‘Get all Worksets for Project’ call, with the exception of having the workset’s TDO id in the call.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (68).png" alt=""><figcaption><p>Get workset details API call</p></figcaption></figure>

&#x20;The body for this call is the same as the body for ‘get all worksets’.

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

&#x20;The return message contains the details for the requested workset.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (69).png" alt=""><figcaption><p>Get workset details result (successful)</p></figcaption></figure>

&#x20;These details can be compared to the details shown in the ‘Edit Workset’ screen on TDO.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (70).png" alt=""><figcaption><p>Workset details in TDO</p></figcaption></figure>
