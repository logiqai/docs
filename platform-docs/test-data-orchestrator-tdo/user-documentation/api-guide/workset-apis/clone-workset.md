# Clone Workset

This API will create a copy of the workset with the new name specified in the API call.  It is run as a POST call and adds a variable for the new workset name to the call used to get workset details (ie, after 'workset' the API includes the instruction 'clone' and then the ID of the workset being cloned and the name of the new workset being created).

The API looks like the example below.

https://\<server>:\<port>/core/API/workSet/clone/\<workset\_id>?name=\<new\_name>

When creating this url, remember to use a new name ending in '\_workset'.

&#x20; In this case, we are cloning the workset ‘api\_2\_workset’ shown below.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption><p>workset list showing workset to be cloned</p></figcaption></figure>

&#x20;The body of this call is still the very simple body (user ID, password, and project).

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

When run, the response shows the details of the cloned workset.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption><p>Results for clone workset API</p></figcaption></figure>

&#x20;TDO now shows the cloned workset in the workset listing, and when you edit that workset the details are the same as the one that was cloned.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption><p>New workset shown in list</p></figcaption></figure>

&#x20;&#x20;

<figure><img src="../../../../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption><p>New workset details</p></figcaption></figure>
