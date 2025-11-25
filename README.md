# Ejemplos: Scraping + API (Ranking FIFA)

Instrucciones rápidas para la práctica final.

1) Activar el entorno virtual (PowerShell)

```pwsh
# desde la carpeta del proyecto
&C:\Users\Ryzen\Desktop\Proyectos\ejemploscrapingtuya\.venv\Scripts\Activate.ps1
```

2) Instalar dependencias (si no lo hiciste ya)

```pwsh
python -m pip install --upgrade pip
pip install -r requerimeintos.txt
```

3) Ejecutar el scraper (abre Chrome y genera `fifa_ranking.json`)

```pwsh
python scraper.py
```

4) Iniciar la API (levanta FastAPI en `http://127.0.0.1:8000`)

```pwsh
# opción A: con reload (desarrollo)
python api.py

# opción B: uvicorn directamente
python -m uvicorn api:app --reload --host 127.0.0.1 --port 8000
```

5) Probar endpoint

Abrir en el navegador o usar `curl`:

```pwsh
curl http://127.0.0.1:8000/ranking
```

6) Abrir cliente

Abrir `client/index.html` en el navegador (p. ej. hacer doble clic). El cliente hace una petición a `http://127.0.0.1:8000/ranking` y muestra los 20 países.

Notas:
- Si la API no encuentra `fifa_ranking.json`, arranca vacía. Ejecuta el scraper antes para precargar datos.
- Si tienes problemas con la ejecución de `scraper.py` por permisos de PowerShell, permite ejecución temporalmente:

```pwsh
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
& .\.venv\Scripts\Activate.ps1
```
