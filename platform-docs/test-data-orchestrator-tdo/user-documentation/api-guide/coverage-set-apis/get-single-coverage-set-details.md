# Get Single Coverage Set Details

This call is used to obtain details on a single coverage set.  This call is sent as a ‘POST’.  You must know the ID prior to setting this one up as the target coverage set ID is used in the API header.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (67).png" alt=""><figcaption><p>Call to get single coverage set details</p></figcaption></figure>

&#x20;&#x20;

The body of the call is the same as used for ‘get all coverage sets’.

&#x20;

{

&#x20;   "context": {

&#x20;       "user": "mbj\_test",

&#x20;       "password": "xxxx",

&#x20;       "project": {

&#x20;           "name": "imp\_payments\_demo",

&#x20;           "version": "1.0"

&#x20;       }

&#x20;   }

}

&#x20;

The return message contains details only for the requested coverage set.

&#x20;&#x20;

<figure><img src="../../../../../.gitbook/assets/image (68).png" alt=""><figcaption><p>Return message showing details on a single coverage set</p></figcaption></figure>
