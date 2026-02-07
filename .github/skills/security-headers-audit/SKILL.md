---
name: security-headers-audit
description: Realiza una auditoría automatizada de cabeceras HTTP de seguridad utilizando herramientas de análisis pasivo como shcheck.
---

# Security Headers Audit (shcheck & nmap)

Este skill automatiza la detección de cabeceras faltantes analizando la respuesta del servidor contra los estándares de seguridad actuales.

## How to use

Cuando detectes una URL o un endpoint de API en el código o se solicite una revisión de seguridad, utiliza la siguiente lógica:

### 1. Ejecución de herramientas
El agente debe sugerir o simular la salida de estas herramientas:

* **shcheck (Recomendado):**
    `shcheck https://{{URL}}`
    *Ventaja:* Enumera específicamente las cabeceras presentes, las faltantes y las que están mal configuradas de forma clara.

### 2. Formato de Reporte de Salida
El skill debe generar una tabla comparativa basada en los resultados de `shcheck`:

"""
### 📊 Resultado de Auditoría (vía shcheck)

| Cabecera | Estado | Riesgo Asociado |
| :--- | :--- | :--- |
| **Content-Security-Policy** | ❌ Faltante | XSS e Inyección de datos. |
| **Strict-Transport-Security** | ❌ Faltante | Ataques de Man-in-the-Middle (MITM). |
| **X-Content-Type-Options** | ✅ Presente | N/A |
| **X-Frame-Options** | ⚠️ Mal configurada | Clickjacking (se recomienda DENY). |
"""