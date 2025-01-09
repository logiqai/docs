# Ingest (Upload) Data Files

Currently, only csv files can be ingested by TDO.  These files must meet some simple rules:

·       Each file must contain column headers in the first row, and at least one row of data.

·       The column header field names must be lower case only, and use underscores instead of spaces.

·       Files cannot contain commas.  This is due to rules governing csv files, which interpret a comma as a field delimiter. Including a comma in a field will cause it to be split into two fields upon ingestion and all subsequent fields in that row will be out of sync with the column headers.

&#x20;Data upload is sent as two separate API’s, first a POST request to create an object ID in TDO and then a PUT request to load the file.&#x20;

&#x20;No body text is required for the POST request, but for the PUT request the body must contain the file name and the data block name.  If this is a new upload, that is all that is needed.  If this is a refresh of an existing data block then you must also include a third line in the body, with a version number for the existing data block that is to be updated.&#x20;

&#x20;The POST request format is  http://\<server:port>/core/1.0/API/upload.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Data upload POST request to create object ID</p></figcaption></figure>

The return message contains the UUID for the object as well as the sample for the second API.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (15).png" alt=""><figcaption><p>Data upload response with object ID and sample API for completion</p></figcaption></figure>

The second API URL is http://\<server:port>/core/1.0/API/project/\<project-name>/\<project-version>/upload/\<file-id>.

&#x20;In Postman, the header line, body, and response for a new file put will look like the below example.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Header (API), body, and response for second half of data upload calls</p></figcaption></figure>

&#x20;After this is run, you can see the resulting data block in TDO.

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (17).png" alt=""><figcaption><p>New data block shown in TDO</p></figcaption></figure>

&#x20;If you were running a subsequent upload of this data, the body would be modified to include the data block version.

&#x20;{

&#x20;   "fileName": "accounts\_4.csv",

&#x20;   "dataBlockName":  "sample\_file",

&#x20;   “dataBlockVersion”: “1.1”

}
