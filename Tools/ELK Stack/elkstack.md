# Elk Stack

### Step 1: System Preparation

1. **System Requirements:**
   - A server with at least 4GB of RAM (8GB recommended).
   - A recent version of Linux (Ubuntu is commonly used).
   - Java 8 or higher (Elasticsearch requires Java).

2. **Update Your System:**
   ```bash
   sudo apt-get update
   sudo apt-get upgrade
   ```

3. **Install Java:**
   ```bash
   sudo apt-get install openjdk-11-jdk
   ```

### Step 2: Install Elasticsearch

1. **Add Elasticsearch GPG Key:**
   ```bash
   wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
   ```

2. **Add Elasticsearch Repository:**
   ```bash
   sudo sh -c 'echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" > /etc/apt/sources.list.d/elastic-7.x.list'
   ```

3. **Install Elasticsearch:**
   ```bash
   sudo apt-get update
   sudo apt-get install elasticsearch
   ```

4. **Configure Elasticsearch:**
   - Open the configuration file:
     ```bash
     sudo nano /etc/elasticsearch/elasticsearch.yml
     ```
   - Set `cluster.name` and `node.name` (e.g., `cluster.name: my-elk-cluster` and `node.name: node-1`).
   - Set `network.host` to `localhost` or your server IP address.

5. **Start and Enable Elasticsearch:**
   ```bash
   sudo systemctl start elasticsearch
   sudo systemctl enable elasticsearch
   ```

6. **Verify Elasticsearch Installation:**
   ```bash
   curl -X GET "localhost:9200/"
   ```

### Step 3: Install Logstash

1. **Install Logstash:**
   ```bash
   sudo apt-get install logstash
   ```

2. **Configure Logstash:**
   - Create a configuration file for Logstash (e.g., `logstash-simple.conf`):
     ```bash
     sudo nano /etc/logstash/conf.d/logstash-simple.conf
     ```
   - Add the following basic configuration:
     ```plaintext
     input {
       beats {
         port => 5044
       }
     }

     filter {
       # Add filters here if needed
     }

     output {
       elasticsearch {
         hosts => ["localhost:9200"]
         index => "logstash-%{+YYYY.MM.dd}"
       }
     }
     ```

3. **Start and Enable Logstash:**
   ```bash
   sudo systemctl start logstash
   sudo systemctl enable logstash
   ```

### Step 4: Install Kibana

1. **Install Kibana:**
   ```bash
   sudo apt-get install kibana
   ```

2. **Configure Kibana:**
   - Open the configuration file:
     ```bash
     sudo nano /etc/kibana/kibana.yml
     ```
   - Set `server.port: 5601`.
   - Set `server.host` to `localhost` or your server IP address.
   - Set `elasticsearch.hosts` to point to your Elasticsearch instance (e.g., `http://localhost:9200`).

3. **Start and Enable Kibana:**
   ```bash
   sudo systemctl start kibana
   sudo systemctl enable kibana
   ```

4. **Access Kibana:**
   - Open a web browser and go to `http://localhost:5601` (or your server's IP address).

### Step 5: Install and Configure Beats (Filebeat as an Example)

1. **Install Filebeat:**
   ```bash
   sudo apt-get install filebeat
   ```

2. **Configure Filebeat:**
   - Open the configuration file:
     ```bash
     sudo nano /etc/filebeat/filebeat.yml
     ```
   - Set the paths to your log files:
     ```yaml
     filebeat.inputs:
     - type: log
       enabled: true
       paths:
         - /var/log/*.log
     ```

   - Configure output to Logstash:
     ```yaml
     output.logstash:
       hosts: ["localhost:5044"]
     ```

3. **Start and Enable Filebeat:**
   ```bash
   sudo systemctl start filebeat
   sudo systemctl enable filebeat
   ```

### Step 6: Visualize Data in Kibana

1. **Load Filebeat Dashboards:**
   ```bash
   sudo filebeat setup --dashboards
   ```

2. **Access Kibana:**
   - Open a web browser and go to `http://localhost:5601`.
   - Navigate to `Discover` to see your log data.
   - Navigate to `Dashboard` to view pre-built dashboards.

### Step 7: Security Configurations (Optional but Recommended)

1. **Set up HTTPS and Basic Authentication in Elasticsearch:**
   - Install X-Pack for Elasticsearch if not included:
     ```bash
     sudo /usr/share/elasticsearch/bin/elasticsearch-plugin install x-pack
     ```
   - Generate certificates and enable security features as per the Elastic documentation.

2. **Secure Kibana:**
   - Configure Kibana to use HTTPS and enable authentication.

### Step 8: Monitor and Maintain

1. **Monitor Logs:**
   - Regularly check logs for Elasticsearch, Logstash, and Kibana for any errors or warnings.
   - Use Kibana's monitoring features to track the health and performance of your ELK stack.

2. **Update and Upgrade:**
   - Keep your ELK stack components up to date with the latest releases and security patches.

By following these steps, you will have a fully functional ELK Stack setup for cybersecurity monitoring. For more advanced configurations and optimizations, refer to the official documentation of each component: [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html), [Logstash](https://www.elastic.co/guide/en/logstash/current/index.html), and [Kibana](https://www.elastic.co/guide/en/kibana/current/index.html).