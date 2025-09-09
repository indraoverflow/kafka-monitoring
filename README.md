# Monitoring Stack with Prometheus, Loki, Grafana, and Promtail

## Overview / Ringkasan

This project uses Docker Compose to run a monitoring and observability stack with Prometheus, Loki, Grafana, and Promtail. Configuration is provided to collect, store, and visualize metrics and logs from various sources.

Proyek ini menggunakan Docker Compose untuk menjalankan stack monitoring dan observability dengan Prometheus, Loki, Grafana, dan Promtail. Konfigurasi sudah disiapkan untuk mengumpulkan, menyimpan, dan menampilkan metrik serta log dari berbagai sumber.

## Services / Layanan

- **Prometheus**: Monitoring and alerting for metrics.  
  Monitoring dan alerting untuk metrik.
- **Loki**: Log storage and search.  
  Penyimpanan dan pencarian log.
- **Promtail**: Log collector agent for Loki.  
  Agen pengumpul log untuk Loki.
- **Grafana**: Visualization for metrics and logs.  
  Visualisasi data metrik dan log.

## Directory Structure / Struktur Direktori

```
docker-compose.yml
config/
  grafana-datasources.yml
  grafana/
    datasources/
      grafana.yaml
    plugins/
      app.yaml
  loki/
    loki.yaml
  prometheus/
    prometheus.yml
  promtail/
    promtail.yaml
```

## How to Run / Cara Menjalankan

1. **Make sure Docker and Docker Compose are installed.**  
   Pastikan Docker dan Docker Compose sudah terpasang.
2. **Run the following command in the root folder:**  
   Jalankan perintah berikut di folder utama:

   ```sh
   docker-compose up -d
   ```

3. **Access the services:**  
   Akses layanan:
   - Grafana: [http://localhost:3000](http://localhost:3000) (user: `admin`, password: `your_secure_password`)
   - Prometheus: [http://localhost:9090](http://localhost:9090)
   - Loki: [http://localhost:3100](http://localhost:3100)

## Configuration / Konfigurasi

- **Prometheus**: [`config/prometheus/prometheus.yml`](config/prometheus/prometheus.yml)
- **Loki**: [`config/loki/loki.yaml`](config/loki/loki.yaml)
- **Promtail**: [`config/promtail/promtail.yaml`](config/promtail/promtail.yaml)
- **Grafana**: [`config/grafana/datasources/grafana.yaml`](config/grafana/datasources/grafana.yaml), [`config/grafana/plugins/app.yaml`](config/grafana/plugins/app.yaml)

## Volumes

- `grafana_data`: Grafana persistent data
- `prometheus_data`: Prometheus persistent data
- `mongo_logs`, `result_logs`: External volumes for MongoDB and application logs

## Notes / Catatan

- Change the Grafana password in [`docker-compose.yml`](docker-compose.yml) before using in production.  
  Ubah password Grafana di [`docker-compose.yml`](docker-compose.yml) sebelum digunakan di production.
- Make sure external volumes (`mongo_logs`, `result_logs`) are available on the host.  
  Pastikan volume eksternal (`mongo_logs`, `result_logs`) sudah tersedia di host.

##