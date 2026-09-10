# Reportes de bugs — SauceDemo

> **Contexto:** SauceDemo es una aplicación de práctica. Los siguientes hallazgos se reprodujeron con sus usuarios de demostración y se documentan para mostrar el proceso de QA.

## Resumen

| ID | Título | Severidad | Prioridad | Estado |
| --- | --- | --- | --- | --- |
| BUG-001 | El carrito se mantiene al cambiar de usuario | Alta | Alta | Nuevo |
| BUG-002 | El catálogo muestra la misma imagen de error para todos los productos | Media | Alta | Nuevo |
| BUG-003 | El apellido se registra en el campo de nombre durante el checkout | Alta | Alta | Nuevo |
| BUG-004 | No se puede agregar Sauce Labs Fleece Jacket al carrito | Alta | Alta | Nuevo |
| BUG-005 | El ordenamiento por precio genera una alerta de error | Media | Media | Nuevo |

---

## BUG-001 — El carrito se mantiene al cambiar de usuario

| Campo | Detalle |
| --- | --- |
| Módulo | Carrito / Autenticación |
| Severidad | Alta |
| Prioridad | Alta |
| Estado | Nuevo |
| Entorno | SauceDemo · Chromium · 2026-09-10 |

**Precondición:** iniciar sesión con `standard_user` y añadir `Sauce Labs Backpack` al carrito.

**Pasos para reproducir**

1. Abrir la pantalla de inicio de sesión e ingresar con `problem_user`.
2. Abrir el carrito.

**Resultado esperado:** el carrito del nuevo usuario debe iniciar vacío o contener únicamente productos agregados por ese usuario.

**Resultado actual:** el carrito muestra `Sauce Labs Backpack`, agregado antes de cambiar de usuario; el indicador del carrito muestra `1`.

**Evidencia:** en `/cart.html`, el producto `Sauce Labs Backpack` aparece con cantidad `1` tras iniciar sesión con `problem_user`.

---

## BUG-002 — El catálogo muestra la misma imagen de error para todos los productos

| Campo | Detalle |
| --- | --- |
| Módulo | Catálogo |
| Severidad | Media |
| Prioridad | Alta |
| Estado | Nuevo |
| Entorno | SauceDemo · Chromium · Usuario `problem_user` · 2026-09-10 |

**Precondición:** iniciar sesión con `problem_user`.

**Pasos para reproducir**

1. Abrir el catálogo de productos.
2. Comparar las imágenes de productos diferentes, por ejemplo `Sauce Labs Backpack` y `Sauce Labs Bike Light`.

**Resultado esperado:** cada producto debe mostrar su propia imagen, coherente con su nombre y descripción.

**Resultado actual:** los seis productos del catálogo usan la misma fuente de imagen `/assets/sl-404-Cq1a9k9X.jpg`.

**Evidencia:** inspección de los elementos de imagen del catálogo: los seis valores `src` son idénticos y apuntan a una imagen de error `sl-404`.

---

## BUG-003 — El apellido se registra en el campo de nombre durante el checkout

| Campo | Detalle |
| --- | --- |
| Módulo | Checkout — datos personales |
| Severidad | Alta |
| Prioridad | Alta |
| Estado | Nuevo |
| Entorno | SauceDemo · Chromium · Usuario `problem_user` · 2026-09-10 |

**Precondición:** iniciar sesión con `problem_user`, tener al menos un producto en el carrito y abrir `/checkout-step-one.html`.

**Pasos para reproducir**

1. Ingresar `Ana` en **First Name**.
2. Ingresar `Pérez` en **Last Name**.
3. Ingresar `8320000` en **Zip/Postal Code**.
4. Seleccionar **Continue**.

**Resultado esperado:** `Ana` debe mantenerse en **First Name**, `Pérez` en **Last Name** y el checkout debe avanzar al siguiente paso.

**Resultado actual:** el valor `Pérez` sobrescribe el campo `first-name`; el campo `last-name` queda vacío y la aplicación muestra `Error: Last Name is required`.

**Evidencia:** valores inspeccionados antes de continuar: `first-name = Pérez`, `last-name = vacío`, `postal-code = 8320000`.

---

## BUG-004 — No se puede agregar Sauce Labs Fleece Jacket al carrito

| Campo | Detalle |
| --- | --- |
| Módulo | Catálogo / Carrito |
| Severidad | Alta |
| Prioridad | Alta |
| Estado | Nuevo |
| Entorno | SauceDemo · Chromium · Usuario `error_user` · 2026-09-10 |

**Precondición:** iniciar sesión con `error_user` y abrir el catálogo.

**Pasos para reproducir**

1. Localizar `Sauce Labs Fleece Jacket`.
2. Seleccionar **Add to cart**.

**Resultado esperado:** el producto debe añadirse al carrito, el botón debe cambiar a **Remove** y el contador del carrito debe incrementarse.

**Resultado actual:** el botón permanece como **Add to cart** y no se produce cambio en el contador ni en el botón.

**Evidencia:** la acción se ejecutó sobre el botón `add-to-cart-sauce-labs-fleece-jacket` sin producir cambio de estado en la pantalla.

---

## BUG-005 — El ordenamiento por precio genera una alerta de error

| Campo | Detalle |
| --- | --- |
| Módulo | Catálogo / Ordenamiento |
| Severidad | Media |
| Prioridad | Media |
| Estado | Nuevo |
| Entorno | SauceDemo · Chromium · Usuario `error_user` · 2026-09-10 |

**Precondición:** iniciar sesión con `error_user` y abrir el catálogo.

**Pasos para reproducir**

1. Abrir el selector de ordenamiento.
2. Elegir **Price (low to high)**.

**Resultado esperado:** los productos deben reordenarse de menor a mayor precio sin mostrar errores.

**Resultado actual:** la aplicación abre una alerta de JavaScript y el ordenamiento no se completa.

**Evidencia:** la alerta muestra el mensaje: `Sorting is broken! This error has been reported to Backtrace.`
