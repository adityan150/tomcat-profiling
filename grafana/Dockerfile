FROM grafana/grafana:latest

COPY prometheus.yml /etc/grafana/provisioning/datasources/

EXPOSE 3000

CMD ["grafana-server", "--config=/etc/grafana/grafana.ini"]
