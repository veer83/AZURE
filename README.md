
Hello 

I hope this email finds you well. I wanted to update you on the current status of our metrics transfer into LaaS for 3PAR, NetApp, and Pure storage systems after we updated the required passwords.

Unfortunately, we've encountered an issue with Filebeat not being able to retrieve metrics for the number of storage systems due to a network port issue. Both Hanu and I have been actively working on this matter and have raised a request to enable the port from source to destination.

It's important to note that this port was functioning perfectly before the network change, which makes it clear that the issue is related to the recent changes.

We would greatly appreciate your assistance in resolving this matter as soon as possible to ensure that our metrics are being transferred correctly into LaaS. If you require any further information or access details to investigate the issue, please don't hesitate to reach out to either Hanu or me, and we will be more than happy to provide the necessary details.

Thank you for your prompt attention to this issue, and we look forward to working together to address and resolve this situation effectively.


# Disaster Recovery Runbook

## Introduction
This Disaster Recovery (DR) runbook outlines the steps required to perform disaster recovery procedures in the event of a system failure or data loss. These procedures are to be carried out by different teams based on their respective responsibilities. This runbook focuses on recovering a specific application or service using Azure Pipelines, Elasticsearch, Kibana, Fleet Server, and network-related tasks.

### Teams and Responsibilities
1. **Platform Team**: Responsible for Azure Pipeline operations, restoring snapshots, recreating Fleet Server, deploying AKS agents, and deploying Logstash pipelines.

2. **Network Team**: Responsible for enabling and disabling data center ingress and Global Traffic Manager (GTM) configuration.

## Disaster Recovery Steps

### 1. Run Azure Pipeline for Deleting Data Stream (Platform Team)
   - **Objective**: To delete the data stream using an Azure Pipeline.
   - **Procedure**:
     1. Execute the appropriate Azure Pipeline job for deleting the data stream.
     2. Monitor the pipeline for success or failure.
     3. If successful, proceed to the next step.

### 2. Restore Snapshot through Kibana (Platform Team)
   - **Objective**: To restore global state and data streams using Kibana.
   - **Procedure**:
     1. Log in to Kibana.
     2. Access the snapshot and restore functionality.
     3. Select the relevant snapshot and initiate the restore.
     4. Monitor the restore process.
     5. Confirm the successful restoration of global state and data streams.

### 3. Recreate Fleet Server (Platform Team)
   - **Objective**: To recreate the Fleet Server.
   - **Procedure**:
     1. Access the Fleet Server configuration.
     2. Recreate the Fleet Server with the required settings and configurations.
     3. Verify that Fleet Server is operational.

### 4. Enable DC06 Ingress Health Check (Network Team)
   - **Objective**: To enable health checking for data center ingress on DC06.
   - **Procedure**:
     1. Access the network configuration for DC06.
     2. Enable health checks for DC06 ingress.
     3. Monitor the health check to ensure it's functioning correctly.

### 5. Enable DC06 on GTM and Disable DC04 (Network Team)
   - **Objective**: To update Global Traffic Manager (GTM) settings to enable DC06 and disable DC04.
   - **Procedure**:
     1. Access the GTM configuration.
     2. Update the configuration to enable DC06 and disable DC04.
     3. Confirm the changes are reflected in the GTM settings.

### 6. Deploy AKS Agent on DC06 (Platform Team)
   - **Objective**: To deploy an AKS agent on DC06.
   - **Procedure**:
     1. Access the AKS agent deployment tool.
     2. Deploy the AKS agent on DC06.
     3. Confirm the agent deployment is successful.

### 7. Deploy Logstash Pipeline on DC06 (Platform Team)
   - **Objective**: To deploy a Logstash pipeline on DC06.
   - **Procedure**:
     1. Access the Logstash pipeline deployment tool.
     2. Deploy the Logstash pipeline on DC06.
     3. Monitor the deployment process and ensure it's operational.

## Post-Disaster Recovery Tasks
After completing the DR steps, the following tasks should be performed:

1. Document the incident, including the cause and recovery steps taken, for post-incident analysis and improvement.

2. Communicate the status of the recovery to relevant stakeholders and teams.

3. Review the effectiveness of the recovery process and make any necessary adjustments for future readiness.

4. Schedule and perform regular disaster recovery drills to ensure the team is well-prepared for any future incidents.

This runbook should be regularly updated to reflect the latest configurations, tools, and procedures.

**Note:** Ensure that the teams responsible for the various steps are trained and prepared for DR scenarios, and that all relevant resources and configurations are well-documented to facilitate the recovery process.
