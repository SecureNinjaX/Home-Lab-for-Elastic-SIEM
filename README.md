# Home Lab for Elastic SIEM

## Description
This project sets up a home lab environment for Elastic SIEM (Security Information and Event Management) a comprehensive setup for learning and practicing security monitoring and incident response. It involves setting up Elastic SIEM to receive data from a Kali Linux VM, generating security events with tools like Nmap, and utilizing Elastic's web interface to query, analyze logs, create visual dashboards, and set up alerts for detecting security events. 

## Table of Contents
1. [Description](#description)
2. [Installation](#installation)
3. [Features](#features)

## Installation

### Step 1: Set up a free trial Elastic Account
- Create a free Elastic account.
- Start a free trial, create an Elasticsearch deployment, and choose your region and deployment size.

### Step 2: Setting up the Linux VM

### Step 3: Setting up the Agent to Collect Logs
- Elastic Deployment successfully setup.
  
  ![Screenshot 2024-07-04 174041](https://github.com/SecureNinjaX/Home-Lab-for-Elastic-SIEM/assets/153300620/095d9f32-83ed-49c8-92a2-e29813cc4640)
  
- Click on “Add integrations” on the bottom left.
- 
  ![Screenshot 2024-07-04 174056](https://github.com/SecureNinjaX/Home-Lab-for-Elastic-SIEM/assets/153300620/d7f0a842-9939-4617-a24c-a426ffade09f)

- Click on “Elastic Defend” and follow the instructions to install the Elastic agent on your Kali VM in your Kali terminal.
  
  ![Screenshot 2024-07-04 174130](https://github.com/SecureNinjaX/Home-Lab-for-Elastic-SIEM/assets/153300620/677f5a6e-b5d4-4ebf-8b7e-99021fa679a1)

- Verify that the agent successfully downloaded with the terminal command:
    ```sh
    sudo systemctl status elastic-agent.service
    ```

### Step 4: Generating Security Events on the Kali VM using Nmap
- Run some Nmap scans on your Kali VM’s IP address to generate security events in Elastic.

  ![msg1250952167-1004](https://github.com/SecureNinjaX/Home-Lab-for-Elastic-SIEM/assets/153300620/4a3326f2-1025-46cc-aac8-5c3ac6e5fff2)

- Remember, make sure to run Nmap scans on your Kali VM’s IP address.

### Step 5: Querying for Security Events in the Elastic SIEM
- Within your Elastic Deployment, click the menu icon (three horizontal lines at the top left) and then click on the “Logs” tab under “Observability”.

  ![Screenshot 2024-07-04 181345](https://github.com/SecureNinjaX/Home-Lab-for-Elastic-SIEM/assets/153300620/c077b4a1-fe7a-4b38-bbf1-4f33080225c3)

- Now see log events from your Kali VM. In the search bar under “Stream” type in:
    ```sh
    process.args: “nmap”
    ```
  to display the Nmap events created on your Kali VM.
- Click on the three dots to the right of the event to view the event’s details.
- Analyzing diverse security events in Elastic SIEM provides valuable insights into real-world security incident detection, investigation, and response procedures.

### Step 6: Create a Dashboard to Visualize the Events
- We can use visualizations and dashboards to analyze event logs.
- Click on “Dashboard” under “Analytics” in the menu.
  
  ![msg1250952167-1007](https://github.com/SecureNinjaX/Home-Lab-for-Elastic-SIEM/assets/153300620/a43f5e0e-aab4-4629-b6dc-792ea84a823e)

- Click on “Create dashboard” at the top right to create a new dashboard.
- Click on “Create Visualization” to add a new visualization to the dashboard.
  
  ![Screenshot 2024-07-04 174221](https://github.com/SecureNinjaX/Home-Lab-for-Elastic-SIEM/assets/153300620/8c06c6a6-d5d9-459f-bfc7-5db066c4807a)

- Pick a visualization display type by choosing “Area”, “Line”, or “Bar vertical” (the author picked this one). Doing so will create a chart that shows the count of events over time.
- Set up the parameters for the visualization with those indicated on the right in this example. Click on the “Save” button at the top right.
  
![msg1250952167-1005](https://github.com/SecureNinjaX/Home-Lab-for-Elastic-SIEM/assets/153300620/e4488003-19b0-4aa4-9bd8-cf77f0e8494a)

### Step 7: Create an Alert
- Create an alert in Elastic SIEM to detect Nmap scans based on custom queries.
- Click on “Alerts” in the menu at the top left.
- Select “Manage rules” in the box at the top right.
- Select “Create new rule” in the box at the top right.
- Select the “Custom query” Rule type.
- Under “Custom query,” type:
    ```sh
    event.action: “nmap_scan”
    ```
  which is the condition for the rule and will match all events with the action “nmap_scan.” Next, click “Continue.”
- Fill in the “About rule” section however you prefer. In this example, the Default severity level is set to High with a Default risk score of 85. Click “Continue”.
- Runtime for rules can be adjusted under “Schedule rule”. In this example, the default values were used. Click “Continue”.
- In the “Rule actions” section, pick the action to take when the rule is triggered. Notice that these actions can range from email, Jira, or Slack alerts depending on which tools your business units/teams prefer to use. Click the “Create and enable rule” button to create the alert.

## Features

- **Complete Elastic Stack Setup:**
   
- **Easy Integration with Elastic Cloud:**
  - Guides users through setting up a free trial Elastic account and deploying Elasticsearch in their preferred region and size.
  
- **Agent-Based Log Collection:**
  - Provides instructions to install and verify the Elastic agent on a Linux VM (Kali) for collecting logs and metrics.
  
- **Security Event Generation with Nmap:**
  - Guides users on generating security events by running Nmap scans on the Kali VM's IP address.
  
- **Powerful Querying and Visualization:**
  - Demonstrates querying for security events within Elastic SIEM using custom queries, such as `process.args: "nmap"`.
  - Provides steps to create visualizations and dashboards in Kibana to analyze event logs effectively.
  
- **Alerting Capabilities:**
  - Shows how to create alerts in Elastic SIEM to detect specific events, such as Nmap scans, based on custom queries.
  
- **Flexible Configuration and Customization:**
  - Allows for easy configuration through provided configuration files and supports customization of alerts and visualizations based on user needs.
  
- **Educational and Practical Use:**
  - Designed for learning and practical application in security monitoring, incident detection, investigation, and response using Elastic SIEM.





