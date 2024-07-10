# WPM Database Migration

Within Apicas goal to support high availability and fully cloud based services, the WPM platform will undergo a database migration to AWS Cloud.

### When <a href="#wpmdatabasemigration-when" id="wpmdatabasemigration-when"></a>

January 18th 2024

1:00PM-3:00PM CET / 7:00AM-9:00AM EST

### What <a href="#wpmdatabasemigration-what" id="wpmdatabasemigration-what"></a>

As the underlying infrastructure is migrated, new IPs and hostnames will be introduced

Services such as private agents will require whitelisting prior to the migration work in order to stay functional throughout the migration

#### User Interface <a href="#wpmdatabasemigration-userinterface" id="wpmdatabasemigration-userinterface"></a>

| **Endpoint** | **Old hostname**                                                      | **Old IP**      | **New hostname**                                           | **New IP**                   |
| ------------ | --------------------------------------------------------------------- | --------------- | ---------------------------------------------------------- | ---------------------------- |
| **ASM Web**  | [https://wpm.apicasystem.com](https://wpm.apicasystem.com/)           | 194.213.119.98  | [https://asm.apica.io](https://asm-eu.apica.io/)           | 13.50.62.252, 51.21.15.5     |
|              | [https://wpm1.apicasystem.com](https://wpm.apicasystem.com/)          | 194.213.119.98  | [https://asm1.apica.io](https://asm-eu1.apica.io/)         | 51.21.140.210, 13.48.72.97   |
|              | [https://wpm2.apicasystem.com](https://wpm.apicasystem.com/)          | 194.213.119.98  | [https://asm2.apica.io](https://asm-eu2.apica.io/)         | 51.21.137.62, 51.21.43.80    |
| **ASM API**  | [https://api-wpm.apicasystem.com](https://api-wpm1.apicasystem.com/)  | 194.213.119.235 |                                                            |                              |
|              | [https://api-wpm1.apicasystem.com](https://api-wpm1.apicasystem.com/) | 194.213.119.235 | [https://api-asm1.apica.io](https://api-asm-eu1.apica.io/) | 13.50.159.138, 16.171.98.167 |
|              | [https://api-wpm2.apicasystem.com](https://api-wpm1.apicasystem.com/) | 194.213.119.235 | [https://api-asm2.apica.io](https://api-asm-eu1.apica.io/) | 13.48.228.34, 13.50.11.146   |
| **Alerter**  |                                                                       | 194.213.119.5   |                                                            | 13.50.21.125                 |

#### Private Agents <a href="#wpmdatabasemigration-privateagents" id="wpmdatabasemigration-privateagents"></a>

| **Endpoint**    | **Old hostname**                                                       | **Old IP**      | **New hostname**                                               | **New IP**                              |
| --------------- | ---------------------------------------------------------------------- | --------------- | -------------------------------------------------------------- | --------------------------------------- |
| Broker          | [broker1.apicasystem.com](http://broker1.apicasystem.com/)             | 194.213.119.164 | [broker-se1.apica.io](http://broker-se1.apica.io/)             | 13.48.38.218, 51.21.39.118              |
|                 | [broker2.apicasystem.com](http://broker2.apicasystem.com/)             | 194.213.119.154 | [broker-se2.apica.io](http://broker-se1.apica.io/)             | 51.21.125.109, 51.20.237.38             |
| XMPP controller | [ctrl.apicanet.com](http://ctrl.apicanet.com/)                         | 194.213.119.237 | [ctrl.apicanet.com](http://ctrl.apicanet.com/)                 | 51.21.40.39, 51.21.103.255              |
| HTTPDB          | [transfer.apicanet.com](http://world.apicanet.com/)                    | 194.213.119.133 | [transfer.apicanet.com](http://transfer.apicanet.com/)         | 51.21.65.17, 13.53.154.35, 51.20.217.86 |
|                 | [transfer-us1.apicasystems.com](http://transfer-us1.apicasystems.com/) | 194.213.119.133 | [transfer-us1.apicanet.com](http://transfer-us1.apicanet.com/) | 34.236.138.236                          |

### How <a href="#wpmdatabasemigration-how" id="wpmdatabasemigration-how"></a>

#### The following services will still be available during the migration work <a href="#wpmdatabasemigration-thefollowingserviceswillstillbeavailableduringthemigrationwork" id="wpmdatabasemigration-thefollowingserviceswillstillbeavailableduringthemigrationwork"></a>

* Check Execution Service
  * Check execution will not see any interruption

#### The following services might experience temporary downtime <a href="#wpmdatabasemigration-thefollowingservicesmightexperiencetemporarydowntime" id="wpmdatabasemigration-thefollowingservicesmightexperiencetemporarydowntime"></a>

* User Interface
* Rest API
* Alerter
* Reporting

### Support <a href="#wpmdatabasemigration-support" id="wpmdatabasemigration-support"></a>

For any queries prior or throughout this migration, please reach out to [support@apica.io](mailto:support@apica.io)

Sincerely

Joakim Baas

Head of Customer Delivery
