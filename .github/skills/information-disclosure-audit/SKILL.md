---
name: information-disclosure-audit
description: Escanea y analiza cabeceras HTTP en busca de fugas de información (Information Disclosure). Identifica versiones de software, tecnologías del backend y sistemas operativos que facilitan el fingerprinting durante un pentest.
---

# Information Disclosure Audit

Este skill se enfoca en extraer inteligencia de las cabeceras que el servidor expone, permitiendo identificar vectores de ataque específicos basados en versiones de software.

## How to use

Utiliza este skill durante la fase de **Reconocimiento** o cuando analices tráfico capturado de una API o sitio web.

### Vectores de Inspección
El agente debe buscar minimamente las siguientes cabeceras para identificar posibles fugas de información:

* **Server:** Revela el software del servidor web (ej. `Server: Apache/2.4.41 (Ubuntu)`).
* **X-Powered-By:** Indica lenguajes o frameworks (ej. `X-Powered-By: PHP/7.4.3`).
* **X-AspNet-Version / X-AspNetMvc-Version:** Revela versiones específicas de .NET.
* **Via / X-Cache:** Indica el uso de Proxies, Balanceadores o CDNs (ej. `Varnish`, `Cloudfront`).
* **X-Generator:** Común en CMS como WordPress (ej. `WordPress 6.4.1`).