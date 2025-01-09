# Delete Business Rule

This call is sent as a DELETE call.  You can only delete one rule at a time using this call, as the rule ID is part of the header.

&#x20;

The body of this call is the same as the details calls, only containing the context.

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

&#x20;

For this call, we are sending the ID for the third rule in the ‘Get All Details’ call illustrated earlier.  The return message simply shows a successful call.

&#x20;&#x20;

<figure><img src="../../../../../.gitbook/assets/image (93).png" alt=""><figcaption><p>Results of delete rule API</p></figcaption></figure>

&#x20; Viewing the business rules in TDO after this call is sent, you can see that the third business rule is no longer present.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (94).png" alt=""><figcaption><p>Rule deleted from TDO</p></figcaption></figure>
