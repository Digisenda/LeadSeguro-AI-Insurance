# LeadSeguro AI – Módulo 001: Captura + Orquestador IA
**Versión:** 1.0 – 2025-06-03  
**Autor:** Juan + Arquitectura Técnica ChatGPT


## 🎯 Objetivo del Módulo  
Capturar datos provenientes de formularios (Meta Ads o webhook externo) y enviarlos a un Agente Orquestador IA, quien decidirá el flujo de asignación de agente humano.  
El flujo realiza validaciones iniciales, logging, integración con GA4 y conexión a submódulos como Registro (M002) y, próximamente, Live Transfer (M003).


## 🧩 Estructura del Canvas

1. **último_formulario1** – Captura de datos desde formulario provisional (será reemplazado por webhook Make o Facebook).
2. **Colocar estructura campos iniciales** – Reestructura y limpia el JSON entrante.
3. **Validación de campos y estructura** – Revisa que nombre, estado, número móvil y código postal estén presentes y válidos.
4. **IF Validación** – Rama TRUE/FALSE según paso anterior.
5. **Establecer credenciales GA4** – Nodo de configuración de Analytics.
6. **Enviar evento GA4** – Registro de evento `lead_captured`.
7. **Nodo Set Final – Normalizar para IA** – Renombre y normalización para el agente.
8. **Hoja de cálculo de Google Sheets** – Log del evento recibido.
9. **Punto de control captura_validada** – Checkpoint para debugging.
10. **Copia datos estructurados** – Prepara JSON para el agente.
11. **Agente IA Orquestador (ChatGPT)** – Decide siguiente módulo (actualmente M002).
12. **Memoria de Chat** – (si aplica) mantiene contexto conversacional.
13. **Llamada a subworkflow M002 – Registro y Asignación**
14. **(Pendiente) Nodo de llamada a subworkflow M003 – Live Transfer (a integrar después)**


## 🔧 Pendientes
- Reemplazar nodo `último_formulario1` por uno de estas dos opciones reales:
  - Webhook desde Make (Meta Ads → Make → Webhook n8n)
  - Webhook directo desde Facebook (si se valida LLC)
- Añadir campos `source`, `estado_lead`, `utm_campaign`, etc., en el flujo si llegan desde el formulario.
- Documentar prompt final del Agente Orquestador tras el Módulo 003.

