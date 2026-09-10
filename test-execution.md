# Ejecución de pruebas

## Información de la ronda

| Campo | Detalle |
| --- | --- |
| Fecha | 2026-09-10 |
| Entorno | SauceDemo · Chromium |
| Alcance | Login, catálogo y carrito |
| Estado general | Aprobado |

## Resumen de resultados

| Planificados | Ejecutados | Aprobados | Fallidos | Bloqueados |
| ---: | ---: | ---: | ---: | ---: |
| 3 | 3 | 3 | 0 | 0 |

## Detalle de ejecución

| ID | Resultado esperado | Resultado observado | Estado |
| --- | --- | --- | --- |
| TC-LOGIN-001 | Abrir el catálogo después de un acceso válido. | El acceso con `standard_user` abrió el catálogo en `/inventory.html`. | ✅ Aprobado |
| TC-LOGIN-002 | Rechazar el acceso y mostrar un error con datos inválidos. | La pantalla de login se mantuvo y mostró un mensaje de credenciales incorrectas. | ✅ Aprobado |
| TC-CART-001 | Añadir un producto y actualizar el contador. | Al añadir `Sauce Labs Backpack`, apareció el contador `1` y el botón cambió a **Remove**. | ✅ Aprobado |

## Conclusión

Los flujos críticos incluidos en el alcance funcionaron conforme a lo esperado. No se identificaron defectos durante esta ronda inicial.
