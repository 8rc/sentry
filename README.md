# Sentry

## Overview

This advanced network monitoring and DDoS protection tool is designed to provide real-time insights into your system's network activity and automatically mitigate potential DDoS attacks. It offers a comprehensive set of features for network administrators and security professionals to safeguard their systems against malicious traffic.

## Key Features

* Real-time network traffic monitoring
* Automatic DDoS attack detection and mitigation
* Configurable rate limiting and protection levels
* System resource usage tracking (CPU, RAM, Disk)
* Detailed attack statistics and logging
* PCAP file generation for in-depth analysis
* Discord webhook integration for instant notifications
* Customizable display options for system dashboard

## Installation

1. Clone this repository:
- git clone https://github.com/8rc/sentry (PYTHON 3.10 IS RECCOMENDED)
2. Install the required dependencies:
- pip install -r requirements.txt
3. Run the script:
- python3 main.py
4. Configuration:
- Configure the `config.json` file (see Configuration section below)


## Configuration

The `config.json` file allows you to customize various aspects of the tool. Here's a detailed explanation of all configuration options:

### General Settings

* `discord_webhook_url`: URL for Discord webhook notifications
* `send_webhook_notifications`: Enable/disable Discord notifications (boolean)
* `network_interface`: Network interface to monitor (e.g., "eth0")
* `pcap_attacks`: Enable/disable PCAP file generation during attacks (boolean)

### Display Options

* `packet_threshold`: Packet count threshold for detecting potential attacks
* `cpu_usage`: Display CPU usage percentage
* `cpu_cores`: Show number of CPU cores
* `ram_usage`: Display RAM usage percentage
* `ram_used`: Show used RAM
* `ram_total`: Display total RAM
* `disk_usage`: Show disk usage percentage
* `disk_used`: Display used disk space
* `disk_total`: Show total disk space
* `uptime`: Display system uptime
* `incoming_bandwidth`: Show incoming network bandwidth
* `outgoing_bandwidth`: Display outgoing network bandwidth
* `incoming_packets`: Show incoming packet count
* `outgoing_packets`: Display outgoing packet count
* `current_tcp_connections`: Show current TCP connections
* `webhook_notifications`: Display webhook notification status
* `last_attack_source_ip`: Show source IP of the last attack
* `last_attack_dest_ip`: Display destination IP of the last attack
* `last_attack_source_port`: Show source port of the last attack
* `last_attack_dest_port`: Display destination port of the last attack
* `last_attack_time`: Show timestamp of the last attack
* `last_attack_pcap_location`: Display location of the last attack's PCAP file
* `last_attack_protocol_info`: Show protocol information of the last attack
* `metric_column_color`: Color for metric column in the dashboard
* `value_column_color`: Color for value column in the dashboard
* `border_style`: Border style for the dashboard panel
* `panel_title`: Title of the dashboard panel
* `protection_status`: Display protection status
* `protection_ports`: Show protected ports
* `ratelimit_level_1`: Display level 1 rate limit
* `ratelimit_level_2`: Show level 2 rate limit
* `ratelimit_level_3`: Display level 3 rate limit
* `current_ratelimit_level`: Show current rate limit level

### Protection Settings

* `status`: Enable/disable the protection feature (string: "true" or "false")
* `port`: List of ports to apply rate limiting
* `ratelimit_level_1`: Packets/second limit for level 1 protection
* `ratelimit_level_2`: Packets/second limit for level 2 protection
* `ratelimit_level_3`: Packets/second limit for level 3 protection
* `monitor_duration`: Duration (in seconds) for each monitoring cycle
* `ratelimit_interval`: Time interval between rate limit level changes

### Attack Alert Settings

* `content`: Custom content for the Discord webhook message
* `embeds`: Embed configuration for the Discord webhook message, including title, description, and color
* (json content from https://discohook.org/ works too)

## How It Works

1. The tool continuously monitors network traffic on the specified interface.
2. It collects system information (CPU, RAM, disk usage) and network statistics.
3. If the packet count exceeds the configured threshold, it triggers the protection mechanism.
4. The protection system applies rate limiting rules using iptables, with three levels of increasing strictness. After the attack has ended the rate limiting rules are deleted.
5. Attack statistics are logged and can be sent via Discord webhook.
6. PCAP files can be generated for further analysis of attack patterns.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.