# Portafolio QA — Pruebas manuales de SauceDemo

![Estado](https://img.shields.io/badge/estado-completado-success) ![Tipo](https://img.shields.io/badge/pruebas-manuales-blue) ![Casos](https://img.shields.io/badge/casos%20ejecutados-3-informational)

## Descripción

Pruebas funcionales manuales realizadas sobre [SauceDemo](https://www.saucedemo.com/), una tienda de demostración pública. Este proyecto muestra el ciclo básico de QA: definición de alcance, diseño de casos, ejecución y registro de resultados.

## Objetivo

Validar los flujos críticos de acceso y compra inicial: autenticación, visualización del catálogo y agregado de un producto al carrito.

## Alcance

| Incluido | Fuera de alcance en esta ronda |
| --- | --- |
| Inicio de sesión | Checkout completo |
| Catálogo de productos | Pruebas de rendimiento |
| Carrito de compras | Pruebas de seguridad |

## Resultados destacados

| Métrica | Resultado |
| --- | --- |
| Casos planificados | 3 |
| Casos ejecutados | 3 |
| Aprobados | 3 |
| Fallidos | 0 |
| Defectos encontrados | 0 |

## Documentación

| Documento | Propósito |
| --- | --- |
| [Casos de prueba](test-cases.md) | Escenarios, datos, pasos y resultados esperados. |
| [Ejecución de pruebas](test-execution.md) | Resultado observado y estado de cada caso. |
| [Plantilla de bug](bug-report-template.md) | Formato reutilizable para documentar defectos. |

## Entorno de prueba

| Campo | Detalle |
| --- | --- |
| Aplicación | SauceDemo |
| URL | https://www.saucedemo.com/ |
| Fecha de ejecución | 2026-09-10 |
| Navegador | Chromium |

> Las credenciales documentadas pertenecen a una aplicación pública de demostración. Nunca incluyas credenciales reales, tokens ni archivos `.env` en GitHub.
