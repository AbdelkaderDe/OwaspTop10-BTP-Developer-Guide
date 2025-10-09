# Exercise 3.2 – Security Event Monitoring in SAP BTP Production Environment

Vulnerability: [A09:2021-Security Logging and Monitoring Failures](https://owasp.org/Top10/A09_2021-Security_Logging_and_Monitoring_Failures/)


## 1. Overview

In this exercise you will extend the local audit-logging setup from [Exercise 3.1 - Audit Logging for Sensitive Data Access](../ex3.1/README.md) production-grade SAP BTP Cloud Foundry environment.

### 🎯 Key Learning Objectives

  * Bind the managed SAP Audit Log Service to your Incident Management application.
  * Deploy the incident management application  on the SAP BTP Cloud Foundry runtime and configure the managed Audit Log Service.
  * Generate and validate audit events triggered by authenticated OData requests to sensitive data endpoints.
  * Use the SAP Audit Log Viewer to access, filter, and analyze audit trails with full context (user, timestamp, action, resource)

## 2. 📋 Prerequisites

* Completed [Exercise 2.1 - Audit Logging for Sensitive Data Access](../ex2.1/README.md) (local audit‐logging using @cap-js/audit-logging, including @PersonalData annotations, the server.js custom logging handler, and successful local validation of SensitiveDataRead, PersonalDataModified, and SecurityEvent logs).

* The SAP Audit Log Viewer service has already been subscribed to in your Enterprise BTP subaccount with the standard plan. No further subscription is required.

## 3. 🪜 Step-by-Step Procedure

### 1. Bind the Managed SAP Audit Log Service

Your mta.yaml already includes the correct service definition. Confirm the following resource exists under the resources: section:

- name: incident-management-auditlog
  type: org.cloudfoundry.managed-service
  parameters:
    service: auditlog
    service-plan: standard

✅ No changes needed — this matches your provided mta.yaml.
⚠️ Do not use cds add audit-logging — it modifies authentication modules and breaks your manual binding.








  
