# 🧪 API Testing Project – Restful Booker

QA Engineer Portfolio Project | Iván Suárez


🧾 Proyecto: Testing de API – Restful Booker
1. Contexto

Restful Booker es una API pública utilizada para practicar pruebas de servicios REST. Permite gestionar reservas (bookings) mediante diferentes endpoints como autenticación, creación, consulta y eliminación.

El objetivo de este proyecto fue validar el comportamiento de los endpoints principales mediante pruebas positivas y negativas, simulando un flujo real de testing.

2. Herramientas utilizadas
Postman
API REST (Restful Booker)
JSON
3. Alcance de pruebas

Se probaron los siguientes endpoints:

POST /auth → autenticación
GET /booking → consulta de bookings
POST /booking → creación de booking
DELETE /booking/{id} → eliminación de booking
4. Casos de prueba ejecutados

CP-01: Autenticación válida

Entrada: credenciales correctas (admin / password123)
Resultado esperado: status 200 + token
Resultado obtenido: ✔️ 200 OK, token generado

CP-02: Obtener lista de bookings

Entrada: request GET
Resultado esperado: status 200 + lista
Resultado obtenido: ✔️ 200 OK

CP-03: Crear booking con datos válidos

Entrada: JSON completo con datos del cliente
Resultado esperado: status 200 + bookingid
Resultado obtenido: ✔️ 200 OK, booking creado correctamente

CP-04: Crear booking con datos incompletos (prueba negativa)

Entrada: JSON con solo firstname
Resultado esperado: error controlado (400 Bad Request)
Resultado obtenido: ❌ 500 Internal Server Error

CP-05: Eliminar booking

Entrada: DELETE con token
Resultado esperado: status 200/201
Resultado obtenido: ❌ 403 Forbidden / 405 Method Not Allowed
5. Resultados y hallazgos

Durante la ejecución de pruebas se identificaron comportamientos importantes:

🐞 Bug 1: Manejo incorrecto de errores en creación de booking

Descripción: La API permite enviar datos incompletos pero responde con error 500
Esperado: error controlado (400 Bad Request)
Severidad: Alta
Impacto: afecta la estabilidad del sistema

🐞 Bug 2: Inconsistencia en autenticación para DELETE

Descripción: El endpoint requiere token y adicionalmente Basic Auth no documentado
Severidad: Media-Alta
Impacto: dificulta el uso correcto del endpoint

🐞 Bug 3: Método DELETE no permitido en endpoint válido

Descripción: Se recibe error 405 aun utilizando método correcto
Severidad: Media
Impacto: comportamiento inconsistente de la API
6. Conclusión

Se validó el funcionamiento general de la API Restful Booker mediante pruebas funcionales y negativas.

Aunque los endpoints principales responden correctamente en escenarios positivos, se detectaron múltiples inconsistencias en el manejo de errores y autenticación, lo cual evidencia áreas de mejora en la validación de datos y configuración del backend.

Este proyecto permitió aplicar principios de testing como validación de respuestas, pruebas negativas y análisis de comportamiento inesperado en APIs.
