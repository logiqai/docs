# Apica plugin 2.0.10 - Supported Grafana Versions

### **Grafana 10.4.2** <a href="#apicaplugin2.0.10-supportedgrafanaversions-grafana10.4.2" id="apicaplugin2.0.10-supportedgrafanaversions-grafana10.4.2"></a>

Grafana 10.4.2 is supported with the Apica plugin

#### Latest stable Grafana version available today <a href="#apicaplugin2.0.10-supportedgrafanaversions-lateststablegrafanaversionavailabletoday" id="apicaplugin2.0.10-supportedgrafanaversions-lateststablegrafanaversionavailabletoday"></a>

As of documenting this on 22nd of April 2024, the latest Grafana (Enterprise) version available is **10.4.2**

Availability based on [https://grafana.com/grafana/download](https://grafana.com/grafana/download)

### **Grafana 10.4.0** <a href="#apicaplugin2.0.10-supportedgrafanaversions-grafana10.4.0" id="apicaplugin2.0.10-supportedgrafanaversions-grafana10.4.0"></a>

The Apica Plugin on Browser Access Mode is currently supported for Grafana 10.2.2

Server Access Mode supports up to 10.4.0

For Server Access Mode, later versions than 10.4.0 may work, but has not yet been verified by Apica.

### Adding support for later versions <a href="#apicaplugin2.0.10-supportedgrafanaversions-addingsupportforlaterversions" id="apicaplugin2.0.10-supportedgrafanaversions-addingsupportforlaterversions"></a>

As of Grafana 10.2.3, the header X-GRAFANA-DEVICE-ID was added as a new default behaviour for client side requests. As the Apica plugin is developed entirely to pull data using the ASM Rest API, and the new header has not been added as an acceptable request header, a Cross-origin resource sharing (CORS) error is triggered when using Browser Access Mode.

Implementation can be found here [https://github.com/grafana/grafana/blob/5e88d29814184d2a7cee70c581c373ecab6ee972/public/app/core/services/backend\_srv.ts#L161](https://github.com/grafana/grafana/blob/5e88d29814184d2a7cee70c581c373ecab6ee972/public/app/core/services/backend\_srv.ts#L161)\
We explored the option to disable the header but such support has not been applied.

Based on this, an implementation task has been set up for ASM development to implement this change as soon as possible

### Latest stable Grafana version available today <a href="#apicaplugin2.0.10-supportedgrafanaversions-lateststablegrafanaversionavailabletoday.1" id="apicaplugin2.0.10-supportedgrafanaversions-lateststablegrafanaversionavailabletoday.1"></a>

As of documenting this on 11th of March 2024, the latest Grafana (Enterprise) version available is **10.4.0**

Availability based on [https://grafana.com/grafana/download](https://grafana.com/grafana/download)
