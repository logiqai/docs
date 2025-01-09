# Update Workset

This API is used to update worksets, either by changing the datablock underlying the data view or by adding a new data view.  It is sent as a PATCH call.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (98).png" alt=""><figcaption><p>Update workset API call</p></figcaption></figure>

&#x20;There is one difference between the body of the ‘create’ and ‘update’ calls.  The first is that the initial part of the ‘entity’ section \[defines the workset name, the primary data view, and underlying coverage set] is replaced by a single line, ‘id’, that contains the TDO id for the workset being upated.  This id can be found in the return message of the create, get all, and get details APIs.

&#x20;

Also, to perform the update, you need to be making a change.  Here, we have changed the name of the data block underlying the customer data view from ‘imp\_customers 1.0.0’ to ‘customers 1.0.0’.  We have also added a new data view, ‘clh\_view’ to the workset.

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

&#x20;      "id": "6761ae6d98cd8a04d7f4e959",

&#x20;       "dataViews": \[

&#x20;           {

&#x20;             "view": {

&#x20;               "name": "cust\_data\_view",

&#x20;               "version": "1.0"

&#x20;           },

&#x20;           "dataSet": {

&#x20;               "name": "customers",

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

&#x20;           },

&#x20;           {

&#x20;             "view": {

&#x20;               "name": "clh\_view",

&#x20;               "version": "1.0"

&#x20;           },

&#x20;           "dataSet": {

&#x20;               "name": "clh\_view",

&#x20;               "version": "1.0.0"

&#x20;           }           &#x20;

&#x20;           }                     &#x20;

&#x20;       ]

&#x20;   }

}

&#x20;

The return message contains the information on what was sent to TDO, including the updated views.  The workset id (in the response message) has remained the same, but the workset version is now returned as ‘1.1’.&#x20;

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (99).png" alt=""><figcaption><p>Update workset return message (successful)</p></figcaption></figure>

Looking at the workset in TDO, we can see the changes that were made to the workset.  The version has incremented to 1.1, the file for ‘cust\_data\_view’ has changed, and the ‘clh\_view’ has been added to the workset.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (100).png" alt=""><figcaption><p>Updated workset showing changes in TDO</p></figcaption></figure>
