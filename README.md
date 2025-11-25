```markdown
# Ejemplos: Scraping + API (Ranking FIFA)

Guía rápida para ejecutar el proyecto en Windows (PowerShell).

Requisitos mínimos
- Python 3.8+ (recomendado 3.11)
- Chrome instalado (el scraper usa `webdriver-manager` para el driver)

1) Desde la carpeta del proyecto: crear/activar el entorno virtual

```pwsh
# Crear (si aún no existe)
python -m venv .venv

# Activar el entorno virtual
& .\.venv\Scripts\Activate.ps1
```

2) Instalar dependencias

```pwsh
# (opcional) actualizar pip
python -m pip install --upgrade pip

# instalar paquetes listados
pip install -r requerimeintos.txt
```

3) Ejecutar el scraper (genera `fifa_ranking.json`)

```pwsh
python scraper.py
```

Notas sobre el scraper:
- El proyecto ya usa `webdriver-manager`, por lo que normalmente no necesitas descargar manualmente chromedriver.
- Asegúrate de tener Chrome instalado y actualizado.

4) Iniciar la API (FastAPI)

```pwsh
# opción A: arrancar con el archivo (si api.py contiene el servidor)
python api.py

# opción B: con uvicorn (recomendado en desarrollo)
python -m uvicorn api:app --reload --host 127.0.0.1 --port 8000
```

5) Probar el endpoint

```pwsh
# desde PowerShell
curl http://127.0.0.1:8000/ranking
```

6) Cliente web

Abre `client/index.html` en tu navegador. El cliente hace una petición a `http://127.0.0.1:8000/ranking` y muestra los datos.

Consejos adicionales
- Si PowerShell bloquea la ejecución de scripts, permite ejecución temporalmente:

```pwsh
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
& .\.venv\Scripts\Activate.ps1
```

- No borres `fifa_ranking.json` si quieres mantener datos entre arranques; el scraper lo sobrescribirá cuando lo ejecutes.
- Si vas a subir este proyecto a un nuevo repositorio, recuerda no incluir archivos sensibles y borra/ignora `.env` si existiera.

```
