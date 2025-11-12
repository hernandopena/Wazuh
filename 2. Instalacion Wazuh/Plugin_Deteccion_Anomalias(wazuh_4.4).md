# Habilitación del plugin de detección de anomalías en Wazuh 4.4  

Este repositorio contiene la guía paso a paso para instalar y configurar el plugin de Anomaly Detection en Wazuh 4.4 integrado con OpenSearch / OpenSearch Dashboards.  

## 📌 Prerrequisitos  
- Tener instalado Wazuh 4.4 (o superior) con sus componentes: Wazuh Manager, Wazuh Indexer y Wazuh Dashboard — según la documentación oficial. :contentReference[oaicite:4]{index=4}  
- Verificar que la versión de OpenSearch / OpenSearch Dashboards es compatible con el plugin (ejemplo: OpenSearch 2.6.0 según blog de Wazuh) :contentReference[oaicite:5]{index=5}  
- Verificar que los índices de Wazuh (“wazuh-alerts-*”, etc.) están recibiendo datos y tienen volumen suficiente para que el modelo de anomalías pueda entrenar. :contentReference[oaicite:6]{index=6}  
- Asegurar que los servicios del cluster (indexer, dash­boards) están operativos, y que los permisos de los usuarios del dashboard permiten instalar plugins.  

## 🛠️ Pasos de instalación y configuración  

### 1. Verificar versiones  
```
bash
# Comprueba versión de OpenSearch
curl -XGET https://<tu-host>:9200

# Comprueba versión de OpenSearch Dashboards en el nodo del dashboard
sudo -u wazuh-dashboard /usr/share/wazuh-dashboard/bin/opensearch-dashboards-plugin list
```

Asegúrate que la versión listada es compatible con el plugin de anomalías.

###  2. Instalar el plugin “Anomaly Detection”
En el nodo donde reside el Wazuh Dashboard (o la instancia de OpenSearch Dashboards):

# Instalar plugin (como usuario root o equivalente)
```
sudo /usr/share/wazuh-dashboard/bin/opensearch-dashboards-plugin install anomalyDetectionDashboards --allow-root
```

# Si ya existe una versión previa o incompatible, primero remover:
```
sudo /usr/share/wazuh-dashboard/bin/opensearch-dashboards-plugin remove anomalyDetectionDashboards --allow-root
```

# Ajustar los permisos del directorio del plugin
```
sudo chown -R wazuh-dashboard:wazuh-dashboard /usr/share/wazuh-dashboard/plugins/anomalyDetectionDashboards/
sudo find /usr/share/wazuh-dashboard/plugins/anomalyDetectionDashboards/ -type d -exec chmod 750 {} \;
sudo find /usr/share/wazuh-dashboard/plugins/anomalyDetectionDashboards/ -type f -exec chmod 640 {} \;
```

Estos pasos están basados en experiencias de la comunidad que reportaron errores de compatibilidad de versiones.

### 3. Reiniciar el servicio del Dashboard

```
sudo systemctl restart wazuh-dashboard
# o el servicio equivalente según tu distribución
```

Verifica los logs (journalctl -u wazuh-dashboard o /var/log/…) para asegurarte de que no hay errores relacionados con la instalación del plugin.

### 4. Verificar la instalación del plugin

```
sudo -u wazuh-dashboard /usr/share/wazuh-dashboard/bin/opensearch-dashboards-plugin list
```

Busca entre los plugins listados algo como:

```
anomalyDetectionDashboards@<versión>
```

Esto confirma que el plugin está correctamente instalado.


### 5. Crear un detector de anomalías

En la interfaz del Dashboard de Wazuh → sección Anomaly Detection (o equivalente en OpenSearch Dashboards):

Haz clic en Create detector.

Define:
-Nombre del detector y descripción.
-Índice de datos como fuente (por ejemplo: wazuh-alerts-*, wazuh-archives-*, etc.).
-Campo de timestamp (por ejemplo: @timestamp).
-Intervalo del detector (por ejemplo cada 10 minutos) y ventana de retraso (“window delay”) si los datos no son en tiempo real.

Configura el modelo:
-Agrega features que quieras monitorizar (por ejemplo: número de eventos por agente, número de reglas por tipo, etc.).
-Selecciona el tipo de agregación (count(), average(), etc.).

Haz clic en Review & Create.
-Si aparece mensaje tipo “Not enough data to train model”, revisa que el índice elegido tenga datos suficientes, que no esté filtrado drásticamente, y que el rango de tiempo usado para el entrenamiento sea adecuado.

Una vez creado y en estado “running”, el detector generará resultados que puedes revisar (grado, confianza, anomalías detectadas).

### 6. Ajustes recomendados para producción

-Verifica que los índices de sistema requeridos por el plugin de Anomaly Detection estén habilitados (por ejemplo: .plugins-ml-model, .plugins-ml-task, etc.).

-Documenta el inicio del detector (qué índice, qué intervalo, qué características) para auditoría institucional.

-Integra los resultados de anomalías con tu flujo de respuesta de incidentes (por ejemplo, que se genere un ticket en tu CSIRT al detectarse anomalía).

-Monitorea el rendimiento del cluster, ya que los modelos de anomalías pueden consumir CPU/memoria adicional.



