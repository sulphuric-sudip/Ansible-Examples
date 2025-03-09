# Kafka, Zookeeper, and Redpanda Cluster Setup

This directory contains Ansible playbooks and configuration files for setting up a distributed Kafka-Zookeeper cluster, along with the Redpanda Console.
* The playbook has been tested on RHEL-based servers. Adjustments is needed for other distributions.
* Review the inventory file, playbook, and configuration files before running, as some parameters may hardcoded.
* Number of servers for cluster can be adjusted by adding/removing hosts on inventory file.

## Architecture Overview
1.  **Common Configurations:**
    *   `/etc/hosts`: DNS records for Kafka and Zookeeper are added to all servers.
    *   SELINUX is disabled on all servers.
    *   Systemd unit files: `kafka.service`, `zookeeper.service`, and `redpanda-console.service` are created.
    *   **Firewall**: Ensure the following ports are open and reachable between servers:
        *   Zookeeper: 2181, 2888, 3888
        *   Kafka: 9091
        *   Redpanda Console: 8080

2.  **Kafka Cluster:**
    *   Logs are stored in `/var/log/kafka-logs`.
    *   Source files are located in `/opt/kafka/`.

3.  **Zookeeper Cluster:**
    *   Data is stored in `/data/zookeeper`.
    *   Source files are located in `/opt/zook/`.

4.  **Redpanda Console:**
    *   Access the Redpanda Console via a web browser at `http://[redpanda_server_ip]:8080/`.


## Playbook
*   **`kafka-redpanda-setup.yml`**:
    *   Adds DNS entries for Kafka and Zookeeper in /etc/hosts
    *   Installs Java 17 on the Kafka and Zookeeper servers.
    *   Disables SELinux.
    *   Installs, configures, and setup the Redpanda Console,  Zookeeper and  Kafka.

## Configuration Files (includes)
*   **`zook-zookeeper.properties.j2`**: Jinja2 template for the Zookeeper configuration file.
*   **`zookeeper.service`**: Systemd unit file for managing the Zookeeper service.
*   **`kafka-server.properties.j2`**: Jinja2 template for the Kafka broker configuration file.
*   **`kafka.service`**: Systemd unit file for managing the Kafka service.
*   **`redpanda-console-config.yaml.j2`**: Configuration file for the Redpanda Console.
