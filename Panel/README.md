![Grafana](./Panel.PNG)
```
CPU Usage
Add Panel: Singlestat
Unit: percent(0-100)
Query: sum (rate (container_cpu_usage_seconds_total{id="/"}[1m])) / sum (machine_cpu_cores) * 100
```
```
CPU Core
Add Panel: Singlestat
Query: machine_cpu_cores
```
```
Memory Usage
Add Panel: Singlestat
Unit: percent(0-100)
Query: (sum(node_memory_MemFree_bytes + node_memory_Buffers_bytes + node_memory_Cached_bytes) ) / sum(node_memory_MemTotal_bytes) * 100
```
```
Used Memory
Add Panel: Singlestat
Unit: gigabytes
Decimals: 2
Query: (sum(node_memory_MemFree_bytes + node_memory_Buffers_bytes + node_memory_Cached_bytes)/(1e+9))
```
```
Used Storaged
Add Panel: Singlestat
Unit: gigabytes
Decimals: 2
Query: node_disk_written_bytes_total/(1e+9)
```
```
Container_CPU_Usage_Seconds
Add Panel: Graph
Query: container_cpu_usage_seconds_total{image="kerberos/kerberos"}
Legend format: {{cpu}}{{\n}}{{name}}
```
```
Container_Memory_Usage
Add Panel: Graph
Query: container_memory_usage_bytes{image="kerberos/kerberos"}
Legend format: {{image}}{{\n}}{{name}}
```
```
Transmitted Network Traffic per Container
Add Panel: Graph
Query: rate(container_network_transmit_bytes_total{image="kerberos/kerberos"}[1m])
Legend format: {{image}}{{/n}}{{name}}
```
```
Received Container Traffic Per Second
Add Panel: Graph
Query: rate(container_network_receive_bytes_total{image="kerberos/kerberos"}[1m])
Legend format: {{image}}{{/n}}{{name}}
```
```
DockerEngine_Daemon_Container_State
Add Panel: Graph
Query: engine_daemon_container_states_containers{state="paused"}
Legend format: paused
Query: engine_daemon_container_states_containers{state="running"}
Legend format: running
Query: engine_daemon_container_states_containers{state="stopped"}
Legend format: stopped
```
