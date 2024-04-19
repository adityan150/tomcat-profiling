# Tomcat Profiling

Profiling metrics of a tomcat web server using JMX exporter, Prometheus and Grafana.

# Containers

1. Tomcat container: runs a tomcat server at port 8080 and jmx exporter exports metrics at port 8088
2. Prometheus container: runs prometheus server at port 9090 that takes inputs from the tomcat container's 8088
3. Grafana container: runs a grafana server at port 3000 and accesses prometheus

# Run

command: `docker-compose up -d --build`
