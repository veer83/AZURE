# Disaster Recovery (DR) Run Book

## Objective
To provide clear steps for teams to follow during a disaster recovery scenario to ensure that services are restored promptly and efficiently.

## Overview
This DR run book will outline the steps to be taken by the Platform team and the Network team during the recovery process.

### **Platform Team Responsibilities**

1. **Run Azure Pipeline for Deleting Data Stream**
    - Navigate to the Azure DevOps portal.
    - Go to your project and then to the Pipelines section.
    - Identify the specific pipeline for deleting data streams.
    - Click on 'Run' and monitor the progress to ensure the data streams are deleted successfully.

2. **Restore Snapshot Through Kibana (Both Global State and Data Streams)**
    - Open Kibana dashboard.
    - Navigate to the "Management" section.
    - Go to "Snapshot and Restore".
    - Identify the snapshot that you want to restore from. 
    - Click on "Restore" and ensure both "Global State" and "Data Streams" are selected.
    - Monitor the progress and confirm successful restoration.

3. **Recreate Fleet Server**
    - Log into the Azure portal.
    - Navigate to the Fleet Server resources.
    - Follow the specific guidelines or scripts provided by your organization to recreate the fleet server.
    - Once recreated, validate by checking the status and ensuring the server is responsive.

4. **Deploy AKS Agent on DC06**
    - Log into the Azure portal.
    - Navigate to AKS clusters and select DC06.
    - Deploy the AKS agent following the standard deployment procedure.
    - Validate the deployment and ensure the agent is running correctly.

5. **Deploy Logstash Pipeline on DC06**
    - Log into the Azure portal or the respective tool used to manage Logstash deployments.
    - Navigate to the Logstash section.
    - Initiate the deployment process for DC06.
    - Once deployed, check the Logstash logs to ensure the pipeline processes are running as expected.

### **Network Team Responsibilities**

1. **Enable DC06 Ingress Health Check**
    - Access the network monitoring and management tool.
    - Navigate to the health check configuration for DC06.
    - Enable the health check, ensuring all configurations are correct.
    - Monitor for a short period to confirm health check responses are as expected.

2. **Enable DC06 on GTM and Disable DC04**
    - Go to the Global Traffic Manager (GTM) configuration.
    - Enable routing to DC06.
    - Navigate to DC04's configuration and disable it.
    - Ensure traffic starts routing to DC06 and monitor for any anomalies.

## Conclusion
Once all the steps have been completed, perform an overall system health check to ensure everything is functioning correctly. This run book should be periodically reviewed and tested to ensure it remains effective in disaster recovery scenarios.
