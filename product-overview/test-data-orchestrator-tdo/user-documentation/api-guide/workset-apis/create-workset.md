# Create Workset

This is sent as a POST call.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (60).png" alt=""><figcaption><p>Create workset API</p></figcaption></figure>

&#x20;The body of the call to create a workset with two data views is shown below. Note that the ‘data views’ section of the entity portion of the body is an array and needs to follow JSON formatting rules for an entity.

&#x20;

{

&#x20;   "context": {

&#x20;       "user": "mbj\_test",

&#x20;       "password": "xxxx",

&#x20;       "project": {

&#x20;           "name": "imp\_payments\_demo",

&#x20;           "version": "1.0"

&#x20;       }

&#x20;   },

&#x20;   "entity": {

&#x20;       "name": "api\_workset",

&#x20;       "scenario": {

&#x20;           "name": "imp\_make\_payment",

&#x20;           "version": "1.0"

&#x20;       },

&#x20;       "primary": {

&#x20;           "view": {

&#x20;               "name": "format\_cov\_view",

&#x20;               "version": "1.0"

&#x20;           },

&#x20;           "dataSet": {

&#x20;               "name": "api\_demo\_coverage",

&#x20;               "version": "1.0.0"

&#x20;           }

&#x20;       },

&#x20;       "dataViews": \[

&#x20;           {

&#x20;             "view": {

&#x20;               "name": "cust\_data\_view",

&#x20;               "version": "1.0"

&#x20;           },

&#x20;           "dataSet": {

&#x20;               "name": "imp\_customers",

&#x20;               "version": "1.0.0"

&#x20;           }

&#x20;           },

&#x20;           {

&#x20;             "view": {

&#x20;               "name": "acts\_view",

&#x20;               "version": "1.0"

&#x20;           },

&#x20;           "dataSet": {

&#x20;               "name": "imp\_accounts",

&#x20;               "version": "1.0.0"

&#x20;           }           &#x20;

&#x20;           }           &#x20;

&#x20;       ]

&#x20;   }

}

&#x20;

The return message shows the status of the call as well as the details of the workset that has been created.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (61).png" alt=""><figcaption><p>Create workset return message (successful)</p></figcaption></figure>

&#x20;

The created workset can now be viewed in the worksets page of TDO.  When you enter edit mode for this workset you can see the workset details in this page match the parameters sent in the body of the call.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (62).png" alt=""><figcaption><p>New workset shown in TDO</p></figcaption></figure>
