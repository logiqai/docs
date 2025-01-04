# Create Determining Attribute (Range-based)

In the example shown below, we are creating a determining attribute called ‘amount\_1’ as a numerical range determining attribute, with 3 values:  0 – 250, 250.01 – 2500, and 2500.01 – 25000.  We are creating this in the ‘imp\_payments\_demo’ project, version 1.0

&#x20;

The API is defined as

<figure><img src="../../../../../.gitbook/assets/image.png" alt=""><figcaption><p>URL format</p></figcaption></figure>

&#x20;

&#x20;

Where ‘http://99.99.99.99:8080/ is the protocol://server:port where TDO resides.

&#x20;

{

&#x20;   "context": {

&#x20;       "user": "mj\_test",

&#x20;       "password": "xxxx",

&#x20;       "project": {

&#x20;           "name": "imp\_payments\_demo",

&#x20;           "version": "1.0"

&#x20;       }

&#x20;   },

&#x20;   "entity": {

&#x20;       "name": "amount\_1",

&#x20;       "dataType": "NUMBER",

&#x20;       "type": "RANGE",

&#x20;       "values": \[

&#x20;           {

&#x20;               "minValue": 0.01,

&#x20;               "maxValue": 250

&#x20;           },

&#x20;           {

&#x20;               "minValue": 250.01,

&#x20;               "maxValue": 2500

&#x20;           },

&#x20;           {

&#x20;               "minValue": 2500.01,

&#x20;               "maxValue": 25000

&#x20;           }

&#x20;       ]

&#x20;   }

}

&#x20;

This screen print shows the results code in Postman.  You will also note that the parameters screen is set up with the type of call (POST) and the full URL for the call (server name/port + URL from the initial table).

&#x20;

&#x20;

<figure><img src="../../../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Results message with determining attribute details</p></figcaption></figure>

&#x20;

&#x20;

Here is how the determining attribute looks in TDO.

<figure><img src="../../../../../.gitbook/assets/image (2).png" alt=""><figcaption><p>Determining attribute in TDO after creation</p></figcaption></figure>
