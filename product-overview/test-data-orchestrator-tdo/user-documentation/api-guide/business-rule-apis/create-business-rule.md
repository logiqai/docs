# Create Business Rule

This call will create a new business rule.  You can only create one business rule at a time, so if you are creating multiple business rules you will need to run this for each rule.

&#x20;

The API can be used to create a business rule with one or more determining attributes.  The key is that the determining attributes referenced in the body of your call must match the determining attributes in the coverage set you are working in.  Below, we will show how to create a simple business rule (one determining attribute) and then a more complex rule (multiple determining attributes).&#x20;

&#x20;

The call for creating the business rule is a POST call.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Create business rule API</p></figcaption></figure>

&#x20;

**Simple (one determining attribute)**

&#x20;

The body of the call includes the name of the coverage set after the base context (user ID, password, and project).  The coverage set you identify must be locked by the user ID you are using to send this API.  You will need to send the ‘lock coverage set’ API before creating business rules.

&#x20;

In the ‘entity’ section, you include both the determining attribute name and value(s) in an array.  Note that all values selected must exist in the determining attribute as it is defined in TDO.

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

&#x20;           "name": "api\_testing\_coverage",

&#x20;         "version": "1.1"

&#x20;       }

&#x20;   },

&#x20;   "entity": {

&#x20;       "conditions": {

&#x20;         "account": {

&#x20;               "values": \["Current"]

&#x20;           }

&#x20;   }

&#x20;   }

}

&#x20;

When the rule is created, the return message shows the rule ID as well as the contents of the rule.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (45).png" alt=""><figcaption><p>Return message business rule created</p></figcaption></figure>

Looking at the business rules in this coverage set in TDO, you can see that the rule was set.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (46).png" alt=""><figcaption><p>Simple business rule contents in TDO</p></figcaption></figure>

&#x20;

**Complex (multiple determining attributes)**

&#x20;

For this call, we will use the coverage set ‘api\_demo\_coverage 1.1’.  This coverage set has five determining attributes.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (47).png" alt=""><figcaption><p>Coverage set contents in TDO</p></figcaption></figure>

&#x20;

The body of the call for multiple determining attributes is set up as an array in the ‘conditions’ section.  Note that you can select one or more values for each determining attribute.&#x20;

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

&#x20;       "conditions": {

&#x20;         "has\_app": {"values": \["0"]},

&#x20;         "acct\_type": {"values": \["Checking","Savings"]},

&#x20;         "has\_online": {"values": \["1"]},

&#x20;         "currency\_a": {"values": \["USD"]},

&#x20;         "customer\_type": {"values": \["Retail"]}     &#x20;

&#x20;       }

&#x20;   &#x20;

&#x20;   }

}

&#x20;

The response to this call will show all of the attributes you defined in the body of the message.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (48).png" alt=""><figcaption><p>Return message for complex rule creation</p></figcaption></figure>

&#x20;The business rule now shows in TDO.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (49).png" alt=""><figcaption><p>Complex business rule after creation</p></figcaption></figure>

