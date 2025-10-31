# Lab 4 WebSocket -- Project Report
# Práctica 4 - David Borrel Seral 871643

## Description of Changes
En esta cuarta sesión de laboratorio, se han completado los tests para el servidor Web de Eliza implementado con WebSockets.
Los cambios realizados son los siguientes:
- En la función `onMessage` del cliente se espera a que haya 3 mensajes en la lista para enviar el texto `always`, se ha elegido este texto ya que viendo el código del cliente de Eliza, para ese texto la respuesta de Eliza es siempre la misma.
- En la función `onChat` de los tests del servidor:
    - Captura del tamaño de la lista en una variable local (`size = list.size`) para evitar condiciones de carrera.
    - Verificación mediante `assertTrue` del rango esperado de mensajes (4 o 5) tras las pruebas realizadas en el laboratorio que había ocasiones que recibía 4 mensajes y otras 5.
    - Verificar que después de enviar la cadena "always" la respuesta va a ser la esperada ("Can you think of a specific example?").

## Technical Decisions
- Se optó por usar `assertTrue(size in 4..5)` en lugar de `assertEquals` debido a la naturaleza no determinista de las comunicaciones WebSocket. El número exacto de mensajes puede variar dependiendo del timing de red y procesamiento.
- Se decidió enviar el mensaje "always" cuando `list.size == 3`, lo que garantiza que se envía después de recibir los tres mensajes iniciales del servidor y además la respuesta a este mensaje va a ser siempre la misma.

## Learning Outcomes
- Comprender el funcionamiento de **WebSockets** y su modelo de comunicación bidireccional en tiempo real.
- Aprender a manejar **problemas de concurrencia** en tests de sistemas distribuidos, concretamente:
  - La importancia de capturar valores en variables locales para evitar "race conditions".
  - Por qué no se pueden usar aserciones exactas en sistemas concurrentes.
- Observar cómo las características del hardware (velocidad del procesador, latencia de red) afectan el comportamiento de aplicaciones concurrentes.

## AI Disclosure
### AI Tools Used
- Para la realización de esta práctica no se ha utilizado ninguna herramienta de IA, todo el trabajo fue completado durante la sesión de laboratorio. Cabe destacar que fueron de gran ayuda todas las explicaciones y análisis realizados por el profesor de la asignatura.

### AI-Assisted Work
- 0% IA <-> 100% David Borrel
- Todo el trabajo ha sido desarrollado durante la sesión de prácticas presencial.

### Original Work
- Comprensión completa de la estructura del proyecto y del servidor WebSocket ELIZA.
- Implementación de los 6 puntos requeridos en los tests.
- Análisis del comportamiento concurrente.
- Redacción de todos los comentarios con explicaciones en el código.
- Esta sesión de laboratorio ha sido muy interesante y de gran ayuda para comprender:
  - El protocolo WebSocket y su implementación en Spring Boot.
  - Los desafíos de hacer tests en aplicaciones concurrentes y distribuidas.
  - Cómo las características del ordenador (CPU, red) afectan el comportamiento de aplicaciones en tiempo real.
  