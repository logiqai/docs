# Get All Business Rules

This API returns details on all rules within a single coverage set.  It is sent as a POST, with the same header details as the ‘create’ and ‘update’ calls.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (90).png" alt=""><figcaption><p>URL for Get All Rules call</p></figcaption></figure>

&#x20;The body of the call looks like the body of the ‘Get Rule Details’ call.

&#x20;

{

&#x20;   "context": {

&#x20;       "user": "mbj\_test",

&#x20;       "password": "xxxx",

&#x20;       "project": {

&#x20;           "name": "imp\_payments\_demo",

&#x20;           "version": "1.0"

&#x20;       },

&#x20;       "coverage" : {

&#x20;           "name": "api\_demo\_coverage",

&#x20;         "version": "1.2"

&#x20;       }

&#x20;   }

}

&#x20;The return message of the API shows the information for all rules contained in this coverage set.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (91).png" alt=""><figcaption><p>Results for Get All Rules</p></figcaption></figure>

This coverage set now contains three rules; the information on all three is included above.  In TDO, the three rules are also shown.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (92).png" alt=""><figcaption><p>Rules in TDO</p></figcaption></figure>
