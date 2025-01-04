# Get All Worksets

This call returns a list of all of the worksets in any given project.  It is POST call.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (101).png" alt=""><figcaption><p>Get all worksets API call</p></figcaption></figure>

&#x20;The body for this call is very simple, containing only the user credentials and the project name.

&#x20;

{

&#x20;         "context": {

&#x20;                   "user": "mbj\_test",

&#x20;                   "password": "xxxx",

&#x20;                   "project": {

&#x20;                             "name": "mug\_test\_project",

&#x20;                             "version": "1.0"

&#x20;                   }

&#x20;         }

}

&#x20;

When run, the return message shows all of the worksets in this project.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (102).png" alt=""><figcaption><p>Return message (successful) showing all worksets</p></figcaption></figure>
