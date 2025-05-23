# Unlock Workset

This call is used to remove a lock placed on a workset.  In TDO, you can see that the workset ‘api\_workset’ has a lock placed by user ‘mbj\_test’.  Note that locks can be removed under two circumstances:  the user who placed the lock can remove their own lock.  In addition, an Admin user can remove any lock.

&#x20;NOTE:  there is no API call to place a lock on a workset; this lock is placed when you run the data assembly process (either via the UI or API).

<figure><img src="../../../../../.gitbook/assets/image (9) (1) (1) (1) (1).png" alt=""><figcaption><p>Locked workset in TDO</p></figcaption></figure>

This API is sent as a PATCH call.  The call includes the instruction ‘unlock’ and the id of the workset to have the lock removed.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Unlock workset API call</p></figcaption></figure>

&#x20;The body is the same as the body for the Get Details API.

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

&#x20;The return message shows that the lock has been removed (last fields) where the ‘lockedBy’ and ‘lockDateTime’ fields are blank/null and the ‘lockTimeout’ is ‘-1.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Unlock workset return message</p></figcaption></figure>

Viewing the workset screen in TDO after this API has been run, you can see that there is no longer a lock present on this workset (no value in the ‘locked by’ column).

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Lock removed in TDO</p></figcaption></figure>
