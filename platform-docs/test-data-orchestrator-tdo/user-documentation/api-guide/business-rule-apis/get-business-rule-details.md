# Get Business Rule Details

This API gets details on a single business rule in a coverage set.  It is sent as a POST.  The ID of the rule you want details on is included in the call.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (88).png" alt=""><figcaption><p>Get business rule details call</p></figcaption></figure>

&#x20;

The body of the call includes the context – user ID, password, and coverage set.  No other items are required.

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

The return message on this API gives all details on the specified rule, including created by, updated by, and all of the conditions.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (89).png" alt=""><figcaption><p>Return message showing business rule details</p></figcaption></figure>
