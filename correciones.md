# Correcciones

** Integrantes **
- David Parra
- Diego Aristizabal

## Error 1
- **Archivo:** app.py
- **Problema:** El puerto estaba en 5001 en vez de 5000
- **Solución:** Cambié `port=5001` por `port=5000`
  
## Error 2
- **Archivo:** app.py
- **Problema:** El endpoint /metrics estaba mal escrito, estaba /metric
- **Solución:** Cambie `/metric` a `/metrics`

## Error 3
- **Archivo:** test_app.py
- **Problema:** El primer test esta esperando `assert data["status"] == "running"` pero el endpoint espera un `{"status": "ok", "service": "devops-api"}`
- **Solución:** cambiar linea que dice `assert data["status"] == "running"` por `assert data["status"] == "ok"`

## Error 4
- **Archivo:** app.py
- **Problema:** El segundo test dice que /health debe retornar CPU, memoria, uptime, status, pero no esta retornando el uptime 
- **Solución:** importar la libreria time `import time`,  crear una variable que inicie el tiempo con la libreria time, añadir el uptime en el endpoint /health `uptime = time.time() - start_time`, y en la respuesta de el json añadir el uptime `"uptime_seconds": uptime`
  
## Error 5
- **Archivo:** docker-compose.yml
- **Problema:** El puerto de docker trata de acceder al 5001, pero deberia acceder al 5000
- **Solución:** Cambié `5000:5001` por `5000:5000`

## Error 6
- **Archivo:** prometheus.yml
- **Problema:** la variable metrics_path tiene el endpoints /metric
- **Solución:** Cambié `/metric` por `/metrics`

## Error 7
- **Archivo:** prometheus.yml
- **Problema:** el servicio definido en el docker compose se llama api y no localhost
- **Solución:** Cambié ` - targets: ['localhost:5000']` por ` - targets: ['api:5000']`

## Error 8
- **Archivo:** requirements.txt
- **Problema:** no esta instalado pytest en github actions 
- **Solución:** agregar pytest a el requirements.txt `pytest==9.0.3`