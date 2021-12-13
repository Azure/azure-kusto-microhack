# Azure Data Explorer Microhack

Kusto Product Group and Microsoft Global Black Belt team are pleased to present this challenge based, collaboration driven, discover-by-doing learning experience to you. Microhacks are divided into two parts to cater enough time for the participants to understand the key concepts of Azure Data Explorer effectively.
- MicroHack 1: Cluster creation and data ingestion
This MicroHack will focus on enabling the participants to design ADX based big data analytics solution, create an ADX cluster, and ingest data into the cluster.
- MicroHack 2: Data exploration and visualization using Kusto Query Language (KQL)
This MicroHack will focus on enabling the participants to write kusto queries to explore and analyse the data stored in the clusters. Participants will also create cool visualizations. It is recommended to complete the MicroHack 1 to begin with this MicroHack.


## MicroHack 1: ADX Cluster Creation and Data Ingestion

### Scenario 

Contoso is a supply chain logistics company that runs a fleet of ships, trucks, and cargo planes to transport and deliver goods around the world. Some of the world’s largest enterprises rely on Contoso’s logistics capabilities to deliver goods to their end customers. Contoso has invested in connecting its fleet with sensors that measure temperature, pressure, humidity, tilt, shock, and light exposure inside its fleet. These sensors emit telemetry data every 1 minute, property data whenever there is a change in the device property, and command data whenever a new command is executed. 

Contoso is looking for a suitable data storage and analytical solution that provides out of the box integration with Azure IoT services such as IoT Hub, Event Hubs as well as can read data from storage accounts. Contoso is developing a SaaS application that will allow its customers to track, trace and monitor their shipments. Contoso wants to offer out of the box visualizations with interactive capabilities to enable its customers to drill-in/drill-out of the data. Contoso will offer its customers to view and analyze last 6 months data. Contoso will retain every customer’s data for up to 1 year. Contoso wants to offer blazing fast loading of visualizations to its customers.
This MicroHack walks through the steps in designing, creating, and configuring Azure Data Explorer clusters keeping in mind these requirements. Once the cluster is deployed, this MicroHack enlists the steps to ingest data into ADX databases and tables using various integration methods such as One Click ingestion.

### Pre-requisites
- An Azure subscription
- (Not applicable for Proctor led events) Deploy IoT Central application, create simulated devices and create Data Exports to Event Hubs and Storage Accounts (use this guide to create this infrastructure). For proctor led events, this infrastructure has been pre-created for you. Proctor will provide connection strings, or SAS tokens at an appropriate stage of the hack.

### Overview

Following architecture has been deployed for you, except the ADX cluster and its integration with other Azure services (indicated by dashed lines).
IoT Central acts as the source of telemetry generated by Contoso’s sensors installed on its fleet of trucks, vessels, and airplanes. Telemetry data is streamed on continuous basis to the Event Hub. Device logs, device property changes and commands executed on the devices are stored in a Storage Account as blobs. 


1. Challenge 1: Create ADX cluster
In this challenge, you will design an ADX based architecture
Familiarize with Azure portal, KWE, KE

2. Challenge 2: Create integration with Azure services

3. Challenge 3: Ingest and transform data

4. Challenge 4: Retrieve stats on the ingested data

5. Challenge 5: Setup basic monitoring of the cluster
