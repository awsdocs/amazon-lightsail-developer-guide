# Tutorial: Install Prometheus on a Linux\-based instance in Amazon Lightsail<a name="amazon-lightsail-install-prometheus"></a>

 *Last updated: August 19, 2022* 

Prometheus is an open source time series monitoring tool for managing a variety of system resources and applications\. It provides a multidimensional data model, the ability to query the collected data, and detailed reporting and data visualization through Grafana\.

By default, Prometheus is enabled to collect metrics on the server where it is installed\. With the help of node exporters, metrics can be collected from other resources like web servers, containers, databases, custom applications, and other third\-party systems\. In this tutorial, we will show you how to install and configure Prometheus with node exporters on a Lightsail instance\. For a full list of available exporters, see [Exporters and integrations](https://prometheus.io/docs/instrumenting/exporters/) in the *Prometheus documentation*\.

**Contents**
+ [Step 1: Complete the prerequisites](#prometheus-prerequisites)
+ [Step 2: Add users and local system directories to your Lightsail instance](#prometheus-add-users-and-directories)
+ [Step 3: Download the Prometheus binary packages](#prometheus-download-binary-packages)
+ [Step 4: Configure Prometheus](#prometheus-configure)
+ [Step 5: Start Prometheus](#start-prometheus)
+ [Step 6: Start Node Exporter](#prometheus-start-node-exporter)
+ [Step 7: Configure Prometheus with the Node Exporter data collector](#configure-prometheus-with-node-exporter)

## Step 1: Complete the prerequisites<a name="prometheus-prerequisites"></a>

Before you can install Prometheus on an Amazon Lightsail instance, you must do the following:
+ Create an instance in Lightsail\. We recommend using the Ubuntu 20\.04 LTS blueprint for your instance\. For more information, see [Create an instance in Amazon Lightsail](getting-started-with-amazon-lightsail.md)\.
+ Create and attach a static IP address to your new instance\. For more information, see [Create a static IP address in Amazon Lightsail](lightsail-create-static-ip.md)\.
+ Open ports 9090 and 9100 on the firewall of your new instance\. Prometheus requires ports 9090 and 9100 to be open\. For more information, see [Adding and editing instance firewall rules in Amazon Lightsail](amazon-lightsail-editing-firewall-rules.md)\.

## Step 2: Add users and local system directories to your Lightsail instance<a name="prometheus-add-users-and-directories"></a>

Complete the following procedure to connect to your Lightsail instance using SSH and add users and system directories\. This procedure creates the following Linux user accounts:
+ `prometheus` – This account is used for installing and configuring the server environment\.
+ `exporter` – This account is used to configure the `node_exporter` extension\.

These user accounts are created for the sole purpose of management and therefore do not require additional user services or permissions beyond the scope of this setup\. In this procedure, you also create directories for storing and managing the files, service settings, and data that Prometheus uses to monitor resources\.

1. Sign in to the [Lightsail console](https://lightsail.aws.amazon.com/)\.

1. On your instance management page, under the **Connect** tab, choose **Connect using SSH**\.  
![\[Connect using SSH in the Lightsail console\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/quick-start-connect-to-your-instance.png)

1. After you're connected, enter the following commands one by one to create two Linux user accounts, `prometheus` and `exporter`\.

   ```
   sudo useradd --no-create-home --shell /bin/false prometheus
   ```

   ```
   sudo useradd --no-create-home --shell /bin/false exporter
   ```

1. Enter the following commands one by one to create local system directories\.

   ```
   sudo mkdir /etc/prometheus /var/lib/prometheus
   ```

   ```
   sudo chown prometheus:prometheus /etc/prometheus
   ```

   ```
   sudo chown prometheus:prometheus /var/lib/prometheus
   ```

## Step 3: Download the Prometheus binary packages<a name="prometheus-download-binary-packages"></a>

Complete the following procedure to download the Prometheus binary packages to your Lightsail instance\.

1. Open a web browser on your local computer and browse to the [Prometheus downloads page](https://prometheus.io/download/)\.

1. At the top of the page, for the **Operating system** dropdown, select **linux**\. For **Architecture**, select **amd64**\.  
![\[Select download filters for Prometheus\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-download-filters.png)

1. Choose or right\-click the **Prometheus** download link that appears, and copy the link address to a text file on your computer\. Do the same for the **node\_exporter** download link that appears\. You will use both copied addresses later in this procedure\.  
![\[Copy download link for Prometheus\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-copy-download-link.png)

1. Connect to your Lightsail instance using SSH\.

1. Enter the following command to change directories to your home directory\.

   ```
   cd ~
   ```

1. Enter the following command to download the Prometheus binary packages to your instance\.

   ```
   curl -LO prometheus-download-address
   ```

   Replace *prometheus\-download\-address* with the address that you copied earlier in this procedure\. The command should look like the following example when you add the address\.

   ```
   curl -LO https://github.com/prometheus/prometheus/releases/download/v2.37.0/prometheus-2.37.0.linux-amd64.tar.gz
   ```

1. Enter the following command to download the `node_exporter` binary packages to your instance\.

   ```
   curl -LO node_exporter-download-address
   ```

   Replace *node\_exporter\-download\-address* with the address that you copied in the previous step of this procedure\. The command should look like the following example when you add the address\.

   ```
   curl -LO https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz
   ```

1. Run the following commands one by one to extract the contents of the downloaded Prometheus and Node Exporter files\.

   ```
   tar -xvf prometheus-2.37.0.linux-amd64.tar.gz
   ```

   ```
   tar -xvf node_exporter-1.3.1.linux-amd64.tar.gz
   ```

   Several subdirectories are created after the contents of the downloaded files are extracted\.

1. Enter the following commands one by one to copy the `prometheus` and `promtool` extracted files to the `/usr/local/bin` programs directory\.

   ```
   sudo cp -p ./prometheus-2.37.0.linux-amd64/prometheus /usr/local/bin
   ```

   ```
   sudo cp -p ./prometheus-2.37.0.linux-amd64/promtool /usr/local/bin
   ```

1. Enter the following command to change the ownership of the `prometheus` and `promtool` files to the `prometheus` user that you created earlier in this tutorial\.

   ```
   sudo chown prometheus:prometheus /usr/local/bin/prom*
   ```

1. Enter the following commands one by one to copy the `consoles` and `console_libraries` subdirectories to `/etc/prometheus`\. The `-r` option performs a recursive copy of all directories within the hierarchy\.

   ```
   sudo cp -r ./prometheus-2.37.0.linux-amd64/consoles /etc/prometheus
   ```

   ```
   sudo cp -r ./prometheus-2.37.0.linux-amd64/console_libraries /etc/prometheus
   ```

1. Enter the following commands one by one to change the ownership of the copied files to the `prometheus` user that you created earlier in this tutorial\. The `-R` option performs a recursive ownership change for all of the files and directories within the hierarchy\.

   ```
   sudo chown -R prometheus:prometheus /etc/prometheus/consoles
   ```

   ```
   sudo chown -R prometheus:prometheus /etc/prometheus/console_libraries
   ```

1. Enter the following commands one by one to copy the configuration file `prometheus.yml` to the `/etc/prometheus` directory and change the ownership of the copied file to the `prometheus` user that you created earlier in this tutorial\.

   ```
   sudo cp -p ./prometheus-2.37.0.linux-amd64/prometheus.yml /etc/prometheus
   ```

   ```
   sudo chown prometheus:prometheus /etc/prometheus/prometheus.yml
   ```

1. Enter the following command to copy the `node_exporter` file from the `./node_exporter*` subdirectory to the `/usr/local/bin` programs directory\.

   ```
   sudo cp -p ./node_exporter-1.3.1.linux-amd64/node_exporter /usr/local/bin
   ```

1. Enter the following command to change the ownership of the file to the `exporter` user that you created earlier in this tutorial\.

   ```
   sudo chown exporter:exporter /usr/local/bin/node_exporter
   ```

## Step 4: Configure Prometheus<a name="prometheus-configure"></a>

Complete the following procedure to configure Prometheus\. In this procedure, you open and edit the `prometheus.yml` file, which contains various settings for the Prometheus tool\. Prometheus establishes a monitoring environment based on the settings that you configure in the file\.

1. Connect to your Lightsail instance using SSH\.

1. Enter the following command to create a backup copy of the `prometheus.yml` file before you open and edit it\.

   ```
   sudo cp /etc/prometheus/prometheus.yml /etc/prometheus/prometheus.yml.backup
   ```

1. Enter the following command to open the `prometheus.yml` file using Vim\.

   ```
   sudo vim /etc/prometheus/prometheus.yml
   ```

   Following are a few important parameters that you might want to configure in the `prometheus.yml` file:
   + `scrape_interval` — Located under the `global` header, this parameter defines the time interval \(in seconds\) for how often Prometheus will collect or *scrape* metric data for a given target\. As indicated by the `global` tag, this setting is universal for all resources that Prometheus monitors\. This setting also applies for exporters, unless an individual exporter provides a different value that overrides the global value\. You can keep this parameter set to its current value of 15 seconds\.
   + `job_name` — Located under the `scrape_configs` header, this parameter is a label that identifies exporters in the result set of a data query or visual display\. You can specify the value of a job name to best reflect the resources that are being monitored in your environment\. For example, you can label a job for managing a website as `business-web-app`, or you can label a database as `mysql-db-1`\. In this initial setup, you are only monitoring the Prometheus server, so you can keep the current `prometheus` value\.
   + `targets` — Located under the `static_configs` header, the `targets` setting uses an `ip_addr:port` key\-value pair to identify the location where a given exporter is running\. You will change the default setting in steps 4–7 of this procedure\.  
![\[Prometheus YAML file\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-yaml-file.png)
**Note**  
For this initial setup, you don't need to configure the `alerting` and `rule_files` parameters\.

1. In the `prometheus.yml` file that you have open in Vim, press the **I** key to enter insert mode in Vim\. 

1. Scroll and find the `targets` parameter located under the `static_configs` header\.

1. Change the default setting to `<ip_addr>:9090`\. Replace `<ip_addr>` with the static IP address of the instance\. The modified parameter should look like the following example\.  
![\[Prometheus YAML file modified static_configs parameter\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-static-configs.png)

1. Press the **Esc** key to exit insert mode, and type **:wq\!** to save your changes and quit Vim\.

1. \(Optional\) If something went wrong, enter the following command to replace the `prometheus.yml` file with the backup that you created earlier in this procedure\.

   ```
   sudo cp /etc/prometheus/prometheus.yml.backup /etc/prometheus/prometheus.yml
   ```

## Step 5: Start Prometheus<a name="start-prometheus"></a>

Complete the following procedure to start the Prometheus service on your instance\.

1. Connect to your Lightsail instance using SSH\.

1. Enter the following command to start the Prometheus service\.

   ```
   sudo -u prometheus /usr/local/bin/prometheus --config.file /etc/prometheus/prometheus.yml --storage.tsdb.path /var/lib/prometheus --web.console.templates=/etc/prometheus/consoles --web.console.libraries=/etc/prometheus/console_libraries
   ```

   The command line outputs details on the startup process and other services\. It should also indicate that the service is listening on port 9090\.  
![\[Prometheus start output\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-start-output.png)

   If the service doesn't start, see the [Step 1: Complete the prerequisites](#prometheus-prerequisites) section of this tutorial for information about creating instance firewall rules to allow traffic on this port\. For other errors, review the `prometheus.yml` file to confirm that there are no syntax errors\.

1. After the running service is validated, press **Ctrl\+C** to stop it\.

1. Enter the following command to open the `systemd` configuration file in Vim\. This file is used to start Prometheus\.

   ```
   sudo vim /etc/systemd/system/prometheus.service
   ```

1. Insert the following lines into the file\.

   ```
   [Unit]
   Description=PromServer
   Wants=network-online.target
   After=network-online.target
   
   [Service]
   User=prometheus
   Group=prometheus
   Type=simple
   ExecStart=/usr/local/bin/prometheus \
   --config.file /etc/prometheus/prometheus.yml \
   --storage.tsdb.path /var/lib/prometheus/ \
   --web.console.templates=/etc/prometheus/consoles \
   --web.console.libraries=/etc/prometheus/console_libraries
   
   [Install]
   WantedBy=multi-user.target
   ```

   The preceding instructions are used by the Linux `systemd` service manager to start Prometheus on the server\. When invoked, Prometheus runs as the `prometheus` user and references the `prometheus.yml` file for loading the configuration settings and storing the time series data in the `/var/lib/prometheus` directory\. You can run `man systemd` from the command line to see more information about the service\.

1. Press the **Esc** key to exit insert mode, and type **:wq\!** to save your changes and quit Vim\.

1. Enter the following command to load the information into the `systemd` service manager\.

   ```
   sudo systemctl daemon-reload
   ```

1. Enter the following command to restart Prometheus\.

   ```
   sudo systemctl start prometheus
   ```

1. Enter the following command to check the status of the Prometheus service\.

   ```
   sudo systemctl status prometheus
   ```

   If the service launched properly, you receive an output similar to the following example\.  
![\[Prometheus status output\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-status-output.png)

1. Press **Q** to exit the status command\.

1. Enter the following command to enable Prometheus to start when the instance is booted\.

   ```
   sudo systemctl enable prometheus
   ```

1. Open a web browser on your local computer and go to the following web address to view the Prometheus management interface\.

   ```
   http:<ip_addr>:9090
   ```

   Replace *<ip\_addr>* with the static IP address of your Lightsail instance\. You should see a dashboard similar to the following example\.  
![\[The Prometheus dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-dashboard.png)

## Step 6: Start Node Exporter<a name="prometheus-start-node-exporter"></a>

Complete the following procedure to start the Node Exporter service\.

1. Connect to your Lightsail instance using SSH\.

1. Enter the following command to create a `systemd` service file for `node_exporter` using Vim\.

   ```
   sudo vim /etc/systemd/system/node_exporter.service
   ```

1. Press the **I** key to enter insert mode in Vim\.

1. Add the following lines of text into the file\. This will configure `node_exporter` with monitoring collectors for CPU load, file system usage, and memory resources\.

   ```
   [Unit]
   Description=NodeExporter
   Wants=network-online.target
   After=network-online.target
   
   [Service]
   User=exporter
   Group=exporter
   Type=simple
   ExecStart=/usr/local/bin/node_exporter --collector.disable-defaults \
   --collector.meminfo \
   --collector.loadavg \
   --collector.filesystem
   
   [Install]
   WantedBy=multi-user.target
   ```
**Note**  
These instructions disable default machine metrics for Node Exporter\. For a complete list of metrics available for Ubuntu, see the [Prometheus node\_exporter man page](http://manpages.ubuntu.com/manpages/focal/man1/prometheus-node-exporter.1.html) in the *Ubuntu documentation*\.

1. Press the **Esc** key to exit insert mode, and type **:wq\!** to save your changes and quit Vim\.

1. Enter the following command to reload the `systemd` process\.

   ```
   sudo systemctl daemon-reload
   ```

1. Enter the following command to start the `node_exporter` service\.

   ```
   sudo systemctl start node_exporter
   ```

1. Enter the following command to check the status of the `node_exporter` service\.

   ```
   sudo systemctl status node_exporter
   ```

   If the service launched successfully, you receive an output similar to the following example\.  
![\[Node exporter status output\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-status-node-exporter.png)

1. Press **Q** to exit the status command\.

1. Enter the following command to enable Node Exporter to start when the instance is booted\.

   ```
   sudo systemctl enable node_exporter
   ```

## Step 7: Configure Prometheus with the Node Exporter data collector<a name="configure-prometheus-with-node-exporter"></a>

Complete the following procedure to configure Prometheus with the Node Exporter data collector\. You do this by adding a new `job_name` parameter for `node_exporter` in the `prometheus.yml` file\.

1. Connect to your Lightsail instance using SSH\.

1. Enter the following command to open the `prometheus.yml` file using Vim\.

   ```
   sudo vim /etc/prometheus/prometheus.yml
   ```

1. Press the **I** key to enter insert mode in Vim\.

1. Add the following lines of text into the file, below the existing `- targets: ["<ip_addr>:9090"]` parameter\.

   ```
   - job_name: "node_exporter"
   
   static_configs:
   - targets: ["<ip_addr>:9100"]
   ```

   The modified parameter in the `prometheus.yml` file should look like the following example\.  
![\[Static configs for Node Exporter\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-node_exporter-static-configs.png)

   Note the following:
   + Node Exporter listens to port 9100 for the `prometheus` server to scrape the data\. Confirm that you followed the steps for creating instance firewall rules as outlined in the [Step 1: Complete the prerequisites](#prometheus-prerequisites) section of this tutorial\.
   + As with the configuration of the `prometheus` `job_name`, replace *<ip\_addr>* with the static IP address that's attached to your Lightsail instance\.

1. Press the **Esc** key to exit insert mode, and type **:wq\!** to save your changes and quit Vim\.

1. Enter the following command to restart the Prometheus service so that the changes to the configuration file can take effect\.

   ```
   sudo systemctl restart prometheus
   ```

1. Enter the following command to check the status of the Prometheus service\.

   ```
   sudo systemctl status prometheus
   ```

   If the service restarted properly, you receive output similar to the following\.  
![\[Prometheus status output\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-status-output2.png)

1. Press **Q** to exit the status command\.

1. Open a web browser on your local computer and go to the following web address to view the Prometheus management interface\.

   ```
   http:<ip_addr>:9090
   ```

   Replace *<ip\_addr>* with the static IP address of your Lightsail instance\. You should see a dashboard similar to the following example\.  
![\[The Prometheus dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-dashboard2.png)

1. In the main menu, choose the **Status** dropdown and select **Targets**\.  
![\[Targets menu option on the Prometheus dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-dashboard-targets.png)

On the next screen, you should see two targets\. The first target is for the **node\_exporter** metrics collector job, and the second target is for the **prometheus** job\.

![\[Targets on the Prometheus dashboard\]](https://d9yljz1nd5001.cloudfront.net/en_us/f1c62fa5316bf1df017e7afb5a0e0a21/images/amazon-lightsail-prometheus-dashboard-targets2.png)

The environment is now properly set up for collecting metrics and monitoring the server\.