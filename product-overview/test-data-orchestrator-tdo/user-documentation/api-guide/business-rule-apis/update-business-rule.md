# Update Business Rule

This is a PATCH call as opposed to a POST call.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (85).png" alt=""><figcaption><p>Update business rule API call</p></figcaption></figure>

&#x20;&#x20;

In the body of the message, the ‘entity.ID’ is now a required field.  We will update the complex rule created above.  The ‘has\_online’ determining attribute is being updated to include both ‘true’ and ‘false’ and the ‘currency\_a’ attribute is being updated to include both USD and GBP currencies.

&#x20;

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

&#x20;   },

&#x20;   "entity": {

&#x20;       "id": "674dd0fb59c7b96171b5a8fa",

&#x20;       "conditions": {

&#x20;         "has\_app": {"values": \["0"]},

&#x20;         "acct\_type": {"values": \["Checking","Savings"]},

&#x20;         "has\_online": {"values": \["1","0"]},

&#x20;         "currency\_a": {"values": \["USD","GBP"]},

&#x20;         "customer\_type": {"values": \["Retail"]}

&#x20;   }

&#x20;   }

}

&#x20;

The return message shows the values that were sent.

&#x20;&#x20;

<figure><img src="../../../../../.gitbook/assets/image (86).png" alt=""><figcaption><p>Update business rule return message</p></figcaption></figure>

&#x20;

In TDO the rule now reflects the new values for ‘has\_online’ and ‘currency\_a’.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (87).png" alt=""><figcaption><p>Updated business rule in TDO</p></figcaption></figure>
