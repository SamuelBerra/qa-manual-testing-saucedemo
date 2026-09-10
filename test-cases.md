# Casos de prueba

## Resumen

| ID | Módulo | Escenario | Prioridad | Tipo |
| --- | --- | --- | --- | --- |
| TC-LOGIN-001 | Inicio de sesión | Acceso con credenciales válidas | Alta | Positiva |
| TC-LOGIN-002 | Inicio de sesión | Rechazo de credenciales inválidas | Alta | Negativa |
| TC-CART-001 | Carrito | Agregar un producto desde el catálogo | Alta | Positiva |

---

## TC-LOGIN-001 — Acceso con credenciales válidas

| Campo | Detalle |
| --- | --- |
| Prioridad | Alta |
| Tipo de prueba | Positiva / funcional |
| Precondición | El usuario se encuentra en la página de inicio de sesión. |
| Datos de prueba | Usuario: `standard_user` · Contraseña: `secret_sauce` |

| # | Paso | Resultado esperado |
| --- | --- | --- |
| 1 | Ingresar un usuario válido. | El campo acepta el valor ingresado. |
| 2 | Ingresar una contraseña válida. | El campo acepta el valor ingresado. |
| 3 | Seleccionar **Login**. | Se muestra el catálogo y la URL contiene `/inventory.html`. |

---

## TC-LOGIN-002 — Rechazo de credenciales inválidas

| Campo | Detalle |
| --- | --- |
| Prioridad | Alta |
| Tipo de prueba | Negativa / funcional |
| Precondición | El usuario se encuentra en la página de inicio de sesión. |
| Datos de prueba | Usuario: `usuario_invalido` · Contraseña: `clave_invalida` |

| # | Paso | Resultado esperado |
| --- | --- | --- |
| 1 | Ingresar un usuario y contraseña inválidos. | Los campos aceptan los valores ingresados. |
| 2 | Seleccionar **Login**. | El acceso es rechazado y se muestra un mensaje de credenciales incorrectas. |

---

## TC-CART-001 — Agregar un producto al carrito

| Campo | Detalle |
| --- | --- |
| Prioridad | Alta |
| Tipo de prueba | Positiva / funcional |
| Precondición | Sesión iniciada con un usuario válido; catálogo visible. |
| Datos de prueba | Producto: `Sauce Labs Backpack` |

| # | Paso | Resultado esperado |
| --- | --- | --- |
| 1 | Localizar `Sauce Labs Backpack`. | Se muestra el producto y el botón **Add to cart**. |
| 2 | Seleccionar **Add to cart**. | El botón cambia a **Remove** y el contador del carrito muestra `1`. |
