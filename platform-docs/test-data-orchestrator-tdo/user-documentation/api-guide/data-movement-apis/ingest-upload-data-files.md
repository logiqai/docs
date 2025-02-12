# Ingest (Upload) Data Files

Currently, only csv files can be ingested by TDO.  These files must meet some simple rules:

·       Each file must contain column headers in the first row, and at least one row of data.

·       The column header field names must be lower case only, and use underscores instead of spaces.

·       Files cannot contain commas.  This is due to rules governing csv files, which interpret a comma as a field delimiter. Including a comma in a field will cause it to be split into two fields upon ingestion and all subsequent fields in that row will be out of sync with the column headers.

&#x20;Data upload is sent as two separate API’s, first a POST request to load the data and create an object ID in TDO and then a PUT request to provide the object names in TDO.&#x20;

&#x20;The file contents are the body of the message for the POST request, and for the PUT request the body must contain the file name and the data block name.  If this is a new upload, that is all that is needed.  If this is a refresh of an existing data block then you may also include a third line in the body, with a version number for the existing data block that is to be updated. If you do not include a version number, TDO will assign the the next sequence number available (i.e., 1.0 for a new data block name, 1._n_ for an existing data block).

&#x20;The POST request format is  http://\<server:port>/core/1.0/API/upload.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (277).png" alt=""><figcaption><p>Header and body for POST request</p></figcaption></figure>

The return message contains the UUID for the object as well as the sample for the second API.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (278).png" alt=""><figcaption><p>Return message with object ID</p></figcaption></figure>

The second API URL is http://\<server:port>/core/1.0/API/project/\<project-name>/\<project-version>/upload/\<file-id>.

&#x20;In Postman, the header line, body, and response for a new file put will look like the below example.  (This example does not use a version number.)

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (279).png" alt=""><figcaption><p>PUT call with object ID, file name, and data block name</p></figcaption></figure>

&#x20;After this is run, you can see the resulting data block in TDO.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (280).png" alt=""><figcaption><p>Newly created data block in TDO (bottom of list)</p></figcaption></figure>

The contents of the data block can be viewed in TDO.

<figure><img src="../../../../../.gitbook/assets/image (281).png" alt=""><figcaption><p>Contents of first row of data </p></figcaption></figure>

