# API Firma PDF — Plan International v3.1

## Deploy en Render.com (5 minutos)

1. Sube esta carpeta a un repo GitHub
2. render.com → **New Web Service** → conecta el repo
3. Configuración:
   - Runtime: `Python 3`
   - Build: `pip install -r requirements.txt`
   - Start: `uvicorn main:app --host 0.0.0.0 --port $PORT`
   - Plan: `Free`
4. Variable de entorno: `API_KEY` = tu clave secreta
5. URL: `https://firma-pdf-planint.onrender.com`

---

## Payload (lo que envía Power Automate)

**POST** `/firmar` · Header: `x-api-key: tu-clave`

```json
{
  "pdf_base64":          "JVBERi0xLjQ...",

  "nombre_supervisor":   "Jhumers Mauricio",
  "cargo_supervisor":    "Analista de TI",
  "user_id":             "abc123-entra-object-id",

  "realizado_por":       "Carlos Mendoza",
  "cargo_realizado_por": "Responsable de compras"
}
```

**Respuesta:**
```json
{
  "success": true,
  "pdf_firmado_base64": "JVBERi0xLjQ...",
  "firma_id": "A3F72603",
  "paginas_firmadas": 2,
  "paginas_marcadas": 1,
  "mensaje": "OK. Firmadas:2 | Sin datos:1 | ID:A3F72603"
}
```

## Notas
- Sello Plan International embebido en la API — no se envía en el request
- Fecha y hora registradas automáticamente por el sistema
- Todo en RAM — sin archivos en disco, sin riesgo de llenar el tier gratuito
- Docs interactivas: `https://tu-api.onrender.com/docs`
