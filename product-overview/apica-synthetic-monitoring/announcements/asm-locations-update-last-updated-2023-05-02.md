# ASM Locations Update (Last updated 2023-05-02)

Starting in February 2023, Apica will begin the transformation of our check location network and nodes in Apica Synthetic Monitoring.\
We are improving our global execution of checks by replacing the underlying platform with an enhanced model that brings improved reliance (High-Availability - HA), security and operational simplicity for both Apica and its customers. This check execution platform and set of locations will be referred to as NG - Next Generation.

The NG platform is based on major cloud provider regions that satisfy our requirements regarding security, redundancy and auto-scaling. This means that our new, improved locations will be based on AWS (Amazon Web Services), Azure and GCP (Google Cloud Platform) provided regions and zones. With this platform, we will evolve with these cloud providers and be ready to expand to any new provider(s) in that space that bring the same high level of service.

Due to this improved check execution platform, there will be changes to our geographical presence in terms of available check locations. The migration to the new NG platform will be executed in phases and existing checks will be migrated with no downtime or work required by you as a user of the platform.

Below you will find a breakdown of planned location changes. All in all, the result of this transformation will mean that some geographical regions currently provided, will go away and new regions will also be added. At this stage, we want to announce the first phase of this transformation and the changes outlined below.

## IP CHANGES: <a href="#asmlocationsupdate-lastupdated2023-05-02-ipchanges" id="asmlocationsupdate-lastupdated2023-05-02-ipchanges"></a>

**As we are changing providers on these locations, new IPs will be distributed.**

Keep in mind that we will **not** perform any migration until 30 days after the new IPs have been shared with you.

We expect this announcement will allow you and all customers enough time to add whitelisting rules for the new locations and related IP addresses.

### **Please see the tables below on which locations are ready for migration and from which date. IP addresses for targeted locations are included in the following list:** <a href="#asmlocationsupdate-lastupdated2023-05-02-pleaseseethetablesbelowonwhichlocationsarereadyformigration" id="asmlocationsupdate-lastupdated2023-05-02-pleaseseethetablesbelowonwhichlocationsarereadyformigration"></a>

### **Production IP Address List:** [**https://s3.eu-central-1.amazonaws.com/apica-ip-addresses/asm-agent-ips.json**](https://s3.eu-central-1.amazonaws.com/apica-ip-addresses/asm-agent-ips.json) <a href="#asmlocationsupdate-lastupdated2023-05-02-productionipaddresslist-https-s3.eu-central-1.amazonaws.com" id="asmlocationsupdate-lastupdated2023-05-02-productionipaddresslist-https-s3.eu-central-1.amazonaws.com"></a>

### **Location Modifications**: <a href="#asmlocationsupdate-lastupdated2023-05-02-locationmodifications" id="asmlocationsupdate-lastupdated2023-05-02-locationmodifications"></a>

These locations/regions are today backed by infrastructure in small to large VPS, co-locations and cloud providers and will now be migrated to one of the major cloud providers as described above. The target provider can be found in the column to the right.

_Yellow = The modification is the same region as before, but a different city._

| **Current location**    | **New location (provider, region ID/code)**                | **Migration start date** |
| ----------------------- | ---------------------------------------------------------- | ------------------------ |
| Argentina, Buenos Aires | Argentina, Buenos Aires (AWS Local Zone, us-east-1-bue-1a) | 2023-05-02               |
| Australia, Sydney       | Australia, Sydney (Azure, aus-east)                        | 2023-05-02               |
| Belgium, Brussels       | Belgium, St. Ghislain (GCP, europe-west1)                  | 2023-06-02               |
| Brazil, Sao Paulo       | Brazil, Sao Paulo (Azure, bra-south)                       | 2023-05-02               |
| Canada, Montreal        | Canada, Toronto (Azure, can-central)                       | 2023-05-02               |
| Canada, Vancouver       | Canada, Toronto (Azure, can-central)                       | 2023-05-02               |
| Chile, Santiago         | Chile, Santiago (GCP, southamerica-west1)                  | 2023-06-02               |
| China, Beijing          | China, Beijing (AWS, cn-north-1)                           |                          |
| China, Hong Kong        | China, Hong Kong (GCP, asia-east2)                         | 2023-06-02               |
| Denmark, Copenhagen     | Denmark, Copenhagen (AWS Local Zone, eu-north-1-cph-1a)    | 2023-05-02               |
| Finland, Pori           | Finland, Hamina (GCP, europe-north1)                       | 2023-06-02               |
| Finland, Espoo          | Finland, Hamina (GCP, europe-north1)                       | 2023-06-02               |
| France, Paris           | France, Paris (Azure, fr-central)                          | 2023-03-14               |
| Germany, Frankfurt      | Germany, Frankfurt (AWS, eu-central-1)                     | 2023-05-02               |
| India, Mumbai           | India, Pune (Azure, ind-central)                           | 2023-05-02               |
| Ireland, Dublin         | Ireland, Dublin (Azure, eu-north)                          | 2023-05-02               |
| Italy, Milan            | Italy, Milan (AWS, eu-south-1)                             | 2023-03-14               |
| Japan, Tokyo            | Japan, Tokyo (Azure, jap-east)                             | 2023-05-02               |
| Netherlands, Amsterdam  | Netherlands, Amsterdam (Azure, westeurope)                 | 2023-03-14               |
| Norway, Oslo            | Norway, Oslo (Azure, norwayeast)                           | 2023-03-14               |
| Poland, Gdansk          | Poland, Warsaw (GCP, europe-central2)                      | 2023-06-02               |
| Singapore, Singapore    | Singapore, Singapore (Azure, asia-south-east)              | 2023-05-02               |
| South Africa, Cape Town | South Africa, Johannesburg (Azure, saf-north)              | 2023-05-02               |
| South Korea, Seoul      | South Korea, Seoul (Azure, kor-central)                    | 2023-05-02               |
| Spain, Madrid           | Spain, Madrid (AWS, eu-south-2)                            | 2023-06-02               |
| Sweden, Stockholm       | Sweden, Stockholm (AWS, eu-north-1)                        | 2023-03-14               |
| Switzerland, Zurich     | Switzerland, Zurich (Azure, switzerlandnorth)              | 2023-03-14               |
| UAE, Dubai              | UAE, Dubai (Azure, uaenorth)                               | 2023-03-14               |
| UK, London              | UK, London (Azure, uk-south)                               | 2023-05-02               |
| USA, Atlanta            | USA, Atlanta (AWS Local Zone, us-east-1-atl-1)             | 2023-05-02               |
| USA, Dallas             | USA, Dallas (AWS Local Zone, us-east-1-dfw-1)              | 2023-05-02               |
| USA, Las Vegas          | USA, Las Vegas (AWS Local Zone, us-west-2-las-1)           | 2023-05-02               |
| USA, Los Angeles        | USA, Los Angeles (AWS Local Zone, us-west-2-lax-1)         | 2023-05-02               |
| USA, Miami              | USA, Miami (AWS Local Zone, us-east-1-mia-1)               | 2023-05-02               |
| USA, New York           | USA, New York (AWS Local Zone, us-east-1-nyc-1)            | 2023-03-14               |
| USA, Ohio               | USA, Ohio (AWS, us-east-2)                                 | 2023-03-14               |
| USA, Oregon             | USA, Oregon (AWS, us-west-2)                               | 2023-03-14               |
| USA, San Francisco      | USA, N. California (San Francisco) (AWS, us-west-1)        | 2023-03-14               |
| USA, Washington DC      | USA, Virginia (Washington DC) (AWS, us-east-1)             | 2023-03-14               |

### &#x20;**Location Termination**: <a href="#asmlocationsupdate-lastupdated2023-05-02-locationtermination" id="asmlocationsupdate-lastupdated2023-05-02-locationtermination"></a>

The following locations will be removed and all existing checks will be migrated to the replacement location specified to the right.

The reason these locations are removed is because there is no major cloud provider with the service level required in this location/region today. During and after these migrations, we will continuously monitor the major cloud providers as they continue to expand into new regions.

As new regions become available, we will be adding them to our network. Stay tuned for these announcements in the coming months.

If you wish for another replacement location, please find the contact persons at the bottom of this document, or reach out to your TAM and we will map your requests during migration.

| **Locations that will be removed** | **Replacement location (provider, region ID/code)** | **Migration start date** |
| ---------------------------------- | --------------------------------------------------- | ------------------------ |
| Australia, Perth                   | Australia, Sydney (Azure, aus-east)                 | 2023-05-02               |
| Austria, Vienna                    | Italy, Milan (AWS, eu-south-1)                      | 2023-03-14               |
| Bulgaria, Sofia                    | Poland, Warsaw (GCP, europe-central2)               | 2023-06-02               |
| Canada, Vancouver                  | Canada, Toronto (Azure, canadacentral)              | 2023-05-02               |
| China, HangZhou                    | China, Beijing (AWS, cn-north-1)                    |                          |
| China, Shanghai                    | China, Beijing (AWS, cn-north-1)                    |                          |
| China, ShenZhen                    | China, Beijing (AWS, cn-north-1)                    |                          |
| Croatia, Zagreb                    | Italy, Milan (AWS, eu-south-1)                      | 2023-03-14               |
| Czech Republic, Prague             | Poland, Warsaw (GCP, europe-central2)               | 2023-06-02               |
| Egypt, Cairo                       | UAE, Dubai (Azure, uaenorth)                        | 2023-03-14               |
| Estonia, Tallinn                   | Finland, Hamina (GCP, europe-north1)                | 2023-06-02               |
| Georgia, Tbilsi                    | Poland, Warsaw (GCP, europe-central2)               | 2023-06-02               |
| Greece, Athens                     | Italy, Milan (AWS, eu-south-1)                      | 2023-03-14               |
| Hungary, Budapest                  | Poland, Warsaw (GCP, europe-central2)               | 2023-06-02               |
| Isle Of Man, Isle Of Man           | United Kingdom, London (Azure, uksouth)             | 2023-05-02               |
| Latvia, Riga                       | Finland, Hamina (GCP, europe-north1)                | 2023-06-02               |
| Lithuania, Vilnius                 | Finland, Hamina (GCP, europe-north1)                | 2023-06-02               |
| Mexico, Guadalajara                | USA, N. California (San Francisco) (AWS, us-west-1) | 2023-03-14               |
| New Zealand, Auckland              | Australia, Sydney (Azure, aus-east)                 | 2023-05-02               |
| Portugal, Lisbon                   | Spain, Madrid (AWS, eu-south-2)                     | 2023-06-02               |
| Romania, Bucharest                 | Poland, Warsaw (GCP, europe-central2)               | 2023-06-02               |
| Slovakia, Bratislava               | Poland, Warsaw (GCP, europe-central2)               | 2023-06-02               |
| Sweden, Gothenburg                 | Sweden, Stockholm (AWS, eu-north-1)                 | 2023-03-14               |
| Sweden, Malmoe                     | Sweden, Stockholm (AWS, eu-north-1)                 | 2023-03-14               |
| Turkey, Ankara                     | Italy, Milan (AWS, eu-south-1)                      | 2023-03-14               |
| Turkey, Istanbul                   | Italy, Milan (AWS, eu-south-1)                      | 2023-03-14               |
| Ukraine, Kiev                      | Poland, Warsaw (GCP, europe-central2)               | 2023-06-02               |
| United Kingdom, Manchester         | United Kingdom, London (Azure, uksouth)             | 2023-05-02               |

### Check Migration Process: <a href="#asmlocationsupdate-lastupdated2023-05-02-checkmigrationprocess" id="asmlocationsupdate-lastupdated2023-05-02-checkmigrationprocess"></a>

We do not expect any downtime for any customer during the migration phase.

* During migration, locations will be hosted in parallel to each other (legacy vs NG), allowing a smooth migration with no downtime.
* Each migration will be done by the Apica Customer Success team.
* Whilst we are migrating Browser checks, these will be updated to the latest available Chrome version at the same time.

As part of this migration, we are also deprecating old check types, and your respective TAM and/or Account Manager will reach out to you if this will affect you.\
We will of course assist with replacing/recreating anything that is deprecated.

**Deprecated check types:**

* Pagespeed
* Google Analytics
* Browser checks (Internet Explorer)
  * Internet Explorer checks have been deprecated due to Microsofts own [EOL statement](https://learn.microsoft.com/en-us/lifecycle/announcements/internet-explorer-11-end-of-support)
* Browser checks (Firefox)
* CommandV1
  * Legacy Ping, Port, URL, DNS

**For any questions or concerns, please contact the following Apica individuals for specific regions:**

* Europe and Asia: Joakim Baas ([joakim.baas@apica.io](mailto:joakim.baas@apica.io))
* Americas: Daniel Bengtsson ([daniel.bengtsson@apica.io](mailto:matt.wilkinson@apica.io)) or Matt Wilkinson ([matt.wilkinson@apica.io](mailto:matt.wilkinson@apica.io))
* General Inquiries: Joakim Baas ([joakim.baas@apica.io](mailto:joakim.baas@apica.io))
* [https://apicasystems.atlassian.net/wiki/spaces/ops/pages/3329720323](https://apicasystems.atlassian.net/wiki/spaces/ops/pages/3329720323)
