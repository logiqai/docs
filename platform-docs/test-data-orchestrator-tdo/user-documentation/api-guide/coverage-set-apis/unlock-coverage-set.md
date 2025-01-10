# Unlock Coverage Set

Once you are finished working in a coverage set, you should release the lock so that other users can access it if desired.  The call is very similar to ‘lock coverage set’, except that the command in the header is ‘unlock’ instead of ‘lock’.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (73).png" alt=""><figcaption><p>Unlock coverage set API call</p></figcaption></figure>

&#x20;

&#x20;The body of the call is the same as in the ‘lock’ call.

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

The return message will show the lock attributes removed from the coverage set (highlighted below).

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (74).png" alt=""><figcaption><p>Return message showing lock removed</p></figcaption></figure>

&#x20;

When viewed in TDO, the ‘locked by’ column is now blank for this coverage set (api\_demo\_coverage 1.0), showing that the lock has been removed.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (75).png" alt=""><figcaption><p>TDO screen showing lock removed</p></figcaption></figure>
