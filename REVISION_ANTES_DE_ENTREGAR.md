# Revisión antes de entregar

## Hallazgo crítico del JSON original

El nodo `Append row in sheet` fue exportado con `parameters.columns.value = {}`. Las capturas muestran los cinco campos y un registro exitoso, pero el archivo exportado **no los incluía**. En `workflow-cafe-central.json` se añadió el mapeo necesario. **El 17/11/2026 se reconfiguraron las cinco columnas en n8n y se probó con éxito la rama DERIVAR:** `Append row in sheet` dio `Success Branch (1 item)` con fecha, teléfono, mensaje, motivo y estado `Pendiente`. Esto valida el workflow activo, aunque la copia pública saneada no se importó/probó de manera separada.

## Verificaciones obligatorias

- [ ] Conectar las credenciales de Sheets, Cohere y Gemini tras importar la copia pública.
- [ ] Seleccionar el documento de Sheets y las dos pestañas correctas.
- [x] Verificar el mapeo de cinco columnas de `Append row in sheet` en n8n (17/11/2026).
- [ ] Ejecutar la ingesta del documento (la base vectorial en memoria se puede vaciar al reiniciar).
- [ ] Probar RESPONDER y guardar captura del resultado HTTP.
- [x] Probar DERIVAR y guardar captura de la salida de escritura exitosa (17/11/2026).
- [ ] Opcional: comprobar directamente en la pestaña Consultas que la fila persiste (la captura disponible confirma salida exitosa del nodo).
- [ ] Probar mensaje vacío y respuesta 400.
- [ ] Confirmar respuesta 503 cuando Sheets no puede registrar (restaurar la hoja luego de la prueba).
- [ ] Consultar trazas del AI Agent para comprobar recuperación RAG real.
- [ ] Comprobar que el repositorio público no contiene credenciales ni datos personales reales.
- [ ] Crear repositorio público en GitHub y pegar URL del repositorio en Ticher.

**No afirmar que el chatbot está conectado con WhatsApp real o que funciona en producción.**

## Evidencia adicional del cierre

- `capturas/08-derivacion-confirmada.png`: clasificación `DERIVAR`, valores escritos y rama exitosa.
- `capturas/09-flujo-derivacion-exitoso.png`: ejecución principal exitosa y camino al Webhook.
