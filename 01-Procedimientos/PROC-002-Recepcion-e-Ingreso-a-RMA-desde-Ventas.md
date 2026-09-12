# PROC-002 - Recepción e ingreso a RMA desde Ventas

| Campo | Valor |
|-------|-------|
| **Código** | PROC-002 |
| **Categoría** | Procedimiento |
| **Área** | Ventas Online, Ventas Presencial, RMA y Taller |
| **Estado** | <span class="kb-status kb-status--ok">Vigente</span> |
| **Versión** | 1.0 |
| **Fecha de creación** | 2026-09-12 |
| **Última actualización** | 2026-09-12 |

---

# Objetivo

Estandarizar la información y los productos que Ventas debe recibir antes de generar un ingreso por garantía al área de RMA.

El procedimiento busca que Taller pueda reproducir la falla en el primer ingreso, reducir pedidos posteriores de componentes, evitar traslados adicionales para el cliente y disminuir tiempos improductivos para Ventas y RMA.

---

# Alcance

Se aplica a la recepción presencial y online de:

- Computadoras completas armadas y entregadas por la empresa.
- Notebooks.
- Componentes vendidos individualmente.
- Conjuntos de componentes adquiridos para formar un mismo equipo, aunque hayan sido armados por el cliente o por un tercero.
- Productos revisados previamente por un técnico externo.

Este procedimiento determina el **alcance inicial del ingreso** y los datos mínimos que deben acompañarlo. La confirmación de la falla y la resolución de la garantía corresponden al diagnóstico del área de RMA.

---

# Principio obligatorio

!!! warning "Síntoma informado no equivale a componente diagnosticado"

    La afirmación del cliente o de un técnico externo debe registrarse como antecedente, pero no debe utilizarse como única razón para ingresar solamente un componente cuando la falla puede depender de la interacción entre varias partes.

Ventas debe registrar:

- **Síntoma:** qué hace o deja de hacer el equipo.
- **Diagnóstico informado:** qué componente cree el cliente o su técnico que falla.
- **Origen del diagnóstico:** cliente, técnico externo, software, mensaje de error u otra fuente.

Ejemplo correcto:

> El equipo enciende, pero no muestra imagen. El cliente informa que un técnico externo atribuyó la falla a la memoria RAM. El diagnóstico no fue validado por RMA. Se reciben los componentes principales utilizados durante la falla.

Ejemplo incorrecto:

> Memoria RAM fallada.

La segunda descripción convierte una hipótesis externa en una conclusión y puede hacer que se reciba un producto que luego funciona normalmente fuera de su configuración original.

---

# Criterio general de recepción

El orden de prioridad es:

1. **Equipo completo en la configuración que presenta la falla.**
2. **Todos los componentes comprados para el mismo armado**, cuando el equipo no fue armado por la empresa o no puede trasladarse completo.
3. **Conjunto mínimo relacionado con el síntoma**, únicamente cuando no sea posible recibir el sistema completo.
4. **Componente aislado**, sólo cuando pueda probarse de manera independiente o el alcance haya sido validado previamente por RMA.

Cuanto más dependa el síntoma de compatibilidad, alimentación, carga, temperatura o interacción entre componentes, mayor debe ser el alcance del ingreso.

!!! danger "No reducir el ingreso por una suposición"

    Si el cliente compró varios componentes para el mismo equipo, Ventas no debe pedir únicamente RAM, CPU, motherboard o GPU basándose sólo en la conclusión del cliente o de un técnico externo. Ante dudas, debe consultar a RMA antes de indicarle qué trasladar o enviar.

---

# Alcance según el tipo de compra

## PC completa armada por la empresa

- Recibir el equipo completo, sin pedir al cliente que desarme o retire componentes.
- Mantener instalada, cuando sea posible, la configuración exacta que presenta la falla.
- Incluir los accesorios directamente relacionados con el síntoma.
- Si la falla depende de un monitor, cable, adaptador, dispositivo USB o periférico particular, recibirlo o registrar el modelo y la prueba que lo relaciona.
- Registrar cualquier modificación realizada después de la entrega: ampliaciones, cambios de GPU, almacenamiento, fuente, refrigeración, BIOS o sistema operativo.

## Notebook

- Recibir la notebook completa.
- Recibir su cargador cuando exista una falla de encendido, carga, batería, rendimiento alimentado o apagados.
- Recibir docks, adaptadores o periféricos únicamente cuando formen parte del problema.
- Registrar golpes, líquidos, roturas, faltantes y estado general mediante observación y fotografías de recepción.
- No solicitar ni anotar contraseñas personales en campos de observación de libre acceso. Utilizar el mecanismo interno autorizado cuando el diagnóstico requiera acceso al sistema.

## Componentes comprados para un mismo armado

Cuando el cliente adquirió varios componentes para formar una computadora y el armado fue realizado por el cliente o por un tercero:

- Priorizar el ingreso de todos los componentes utilizados durante la falla.
- No asumir que el componente señalado por el armador es el único responsable.
- Registrar marca y modelo de los componentes no comprados a la empresa que formen parte de la configuración.
- Solicitar fotografías del armado antes del desarme cuando puedan aportar información sobre conexiones, slots, alimentación o montaje.
- Si no es posible recibir todo, definir con RMA el conjunto mínimo necesario antes de cerrar la recepción.

## Componente individual utilizado en otro equipo

Puede recibirse de manera aislada cuando:

- La falla sea propia del producto y pueda reproducirse con equipamiento estándar.
- Se disponga de información suficiente sobre el sistema donde ocurrió.
- No exista una dependencia evidente con otros componentes.
- RMA no haya solicitado expresamente la configuración completa.

Aunque se reciba un único producto, el ingreso debe incluir la configuración del equipo donde se utilizó y una descripción reproducible de la falla.

## Diagnóstico de un técnico externo

- Registrar el diagnóstico textual y, si existe, el informe o las pruebas realizadas.
- No presentarlo como diagnóstico confirmado por la empresa.
- Preguntar qué metodología se utilizó: reemplazo cruzado, prueba en otro equipo, software, medición o inspección.
- Si no existen datos suficientes o la falla puede ser causada por varios componentes, recibir el conjunto completo o consultar a RMA.

---

# Información obligatoria

Antes de finalizar el ingreso, Ventas debe poder responder:

| Dato | Información requerida |
|------|------------------------|
| Producto | Equipo completo o productos exactos que ingresan |
| Compra | Factura, pedido u operación asociada según el sistema interno |
| Síntoma | Descripción de lo que ocurre, sin convertirlo en un diagnóstico |
| Momento | Desde cuándo ocurre y si comenzó después de un cambio |
| Condición | Durante qué acción, programa, juego, carga o estado aparece |
| Frecuencia | Siempre, varias veces por día, una vez por semana, aleatoria, etc. |
| Reproducción | Pasos necesarios para provocar o reconocer la falla |
| Duración | Cuánto tiempo tarda en aparecer y cuánto dura |
| Mensaje | Texto exacto, código de error, LED, pitido, pantalla o código POST |
| Configuración | CPU, motherboard, RAM, GPU, fuente, almacenamiento y sistema operativo cuando corresponda |
| Cambios previos | Hardware, BIOS, drivers, Windows, limpieza, armado o reparación reciente |
| Pruebas realizadas | Qué se cambió, dónde se probó y cuál fue el resultado |
| Diagnóstico externo | Quién lo emitió y en qué evidencia se basó |
| Evidencia | Existencia y ubicación de fotos, videos, capturas, informes o registros |
| Intermitencia | Última vez que ocurrió y cantidad aproximada de eventos |

No es suficiente escribir únicamente expresiones como:

- «No funciona».
- «Está fallado».
- «Problema de video».
- «La RAM está mal».
- «El técnico dijo que es la placa».

---

# Registro de fotografías, videos y otros archivos

Si el cliente envió evidencia por chat, correo, formulario o durante la atención presencial:

1. Revisar que el archivo corresponda al producto y al síntoma informado.
2. Adjuntarlo al ingreso cuando el sistema lo permita.
3. Si no puede adjuntarse, registrar dónde se encuentra, fecha aproximada, canal utilizado y nombre o descripción del archivo.
4. Escribir expresamente en las observaciones que existe evidencia disponible.
5. Indicar qué momento del archivo muestra la falla si el video es extenso.
6. No copiar ni publicar información personal que no sea necesaria para el diagnóstico.

Ejemplo:

> Cliente envió por el chat de Ventas dos videos el 10/09. En `video_2`, desde 00:18, se observan artefactos y cierre del juego. Evidencia pendiente de revisión por RMA.

!!! warning "La evidencia debe ser localizable"

    Escribir solamente «cliente mandó video» no resulta suficiente. RMA debe poder encontrar el archivo sin volver a contactar al cliente ni buscar en conversaciones sin referencia.

---

# Matriz de recepción según el síntoma

La tabla indica el alcance recomendado. RMA puede ampliarlo o reducirlo según el caso.

| Síntoma | Ingreso preferido | Conjunto mínimo si no puede ingresar completo | Información adicional |
|---------|-------------------|-----------------------------------------------|----------------------|
| No da imagen / no completa POST | Equipo completo | Motherboard, CPU, RAM y GPU cuando sea necesaria | LEDs o códigos POST, pitidos, ventiladores, salida utilizada y video del intento |
| No enciende | Equipo completo con fuente | Motherboard, CPU y fuente; agregar RAM/GPU según configuración | Señales de alimentación, comportamiento al presionar encendido y conexiones utilizadas |
| Se reinicia o apaga | Equipo completo | Motherboard, CPU, RAM, fuente y GPU si ocurre bajo carga gráfica | Carga que lo provoca, tiempo, temperaturas y frecuencia |
| Pantallazo azul, congelamiento o error aleatorio | Equipo completo | CPU, motherboard, RAM y almacenamiento relacionado; agregar GPU/fuente según el síntoma | Código exacto, momento, frecuencia, sistema y cambios recientes |
| Artefactos, pérdida de señal o cierre en juegos | Equipo completo | GPU y, cuando sea posible, fuente; registrar el resto de la plataforma | Juego/programa, escena, API, resolución, calidad, driver, temperatura y evidencia |
| Sospecha de memoria RAM | Equipo completo o conjunto del armado | Kit completo de RAM, CPU y motherboard | Slot, cantidad de módulos, perfil XMP/EXPO, frecuencia, prueba utilizada y errores |
| Problemas de almacenamiento | Equipo completo si afecta el arranque | Unidad afectada; agregar motherboard/cables cuando corresponda | Mensajes, SMART, velocidad, desconexiones y puerto utilizado |
| Temperatura o bajo rendimiento | Equipo completo con su refrigeración | CPU/GPU y refrigeración relacionada sólo por acuerdo con RMA | Carga, temperatura, frecuencia, consumo, ambiente y tiempo hasta la falla |
| Puerto o periférico no reconocido | Equipo y dispositivo relacionado | Producto, cable, adaptador o receptor involucrado | Puerto exacto, sistema operativo y resultado en otro equipo |
| Notebook no carga o se apaga | Notebook completa con cargador | No corresponde desarmar para reducir el ingreso | LED de carga, porcentaje, cargador utilizado y condición de batería |

## Caso específico: no da imagen

Ante «no da imagen», Ventas debe preguntar:

1. ¿El equipo enciende y giran los ventiladores?
2. ¿El teclado, mouse o LEDs cambian durante el arranque?
3. ¿La motherboard muestra un LED de CPU, DRAM, VGA o BOOT?
4. ¿Existe un código numérico de diagnóstico o una secuencia de pitidos?
5. ¿El monitor se probó con otro dispositivo?
6. ¿Qué cable, entrada y salida de video se utilizaron?
7. ¿El cable está conectado al motherboard o a la placa de video?
8. ¿El procesador posee gráficos integrados?
9. ¿La falla apareció después de cambiar RAM, GPU, CPU, BIOS o conexiones?
10. ¿Se obtiene imagen después de varios intentos o nunca?

El ingreso preferido es el **equipo completo**. Si esto no es posible y los productos fueron comprados para el mismo armado, deben recibirse como mínimo:

- Motherboard.
- Procesador.
- Kit completo de memoria RAM.
- Placa de video cuando el procesador no tenga gráficos integrados o la falla dependa de ella.

También debe incluirse la fuente cuando haya sido utilizada en la configuración, se haya comprado junto con el armado o existan síntomas de alimentación, reinicios o pérdida de señal bajo carga.

---

# Caso específico: placa de video con fallas en juegos

Antes de recibir una GPU por fallas que aparecen durante juegos o programas, registrar:

- Nombre exacto de cada juego o aplicación.
- Momento o acción que produce la falla.
- Si ocurre al iniciar, cargar una partida, después de cierto tiempo o bajo una función específica.
- Frecuencia y tiempo aproximado hasta que ocurre.
- Descripción exacta: artefactos, pantalla negra, pérdida de señal, cierre, congelamiento, reinicio o error del controlador.
- Resolución, calidad gráfica y API cuando el cliente pueda informarlas.
- Versión del sistema operativo y del controlador gráfico.
- CPU, motherboard, RAM y fuente del equipo.
- Modelo, potencia y antigüedad de la fuente.
- Temperaturas observadas, si fueron medidas.
- Resultado en otros juegos, programas o benchmarks.
- Cambios de drivers, cables, fuente, BIOS o configuración ya realizados.
- Disponibilidad y ubicación de fotos o videos.

Ejemplo de observación útil:

> En Cyberpunk 2077, después de 15 a 25 minutos, aparecen cuadrados de colores y luego el juego se cierra. Ocurre en aproximadamente 3 de cada 5 intentos. Cliente informa Windows 11, driver gráfico 000.00 y fuente marca/modelo de 650 W. Envió video por el chat de Ventas; la falla se observa desde 00:32.

Ejemplo insuficiente:

> La placa falla en juegos.

---

# Procedimiento para Ventas presencial

## 1. Identificar la compra

1. Localizar la operación en el sistema.
2. Determinar si se vendió un equipo completo, una notebook, un componente aislado o varios componentes para un mismo armado.
3. Identificar cuáles de esos productos participaron en la configuración que presentó la falla.

## 2. Registrar el relato sin diagnosticar

1. Preguntar qué ocurrió y anotarlo como síntoma.
2. Separar las observaciones del cliente de las conclusiones de terceros.
3. Completar los datos obligatorios y las preguntas específicas aplicables.

## 3. Definir qué productos recibir

1. Priorizar el equipo completo.
2. Si se trata de un armado externo con varias piezas compradas, priorizar todos los componentes utilizados.
3. Aplicar la matriz por síntoma.
4. Consultar a RMA antes de reducir el ingreso cuando exista duda.

## 4. Revisar y documentar la recepción

1. Verificar productos, cantidades y accesorios recibidos.
2. Registrar números de serie en el sistema interno cuando corresponda.
3. Documentar el estado físico y cualquier faltante.
4. Tomar fotografías cuando existan golpes, marcas, pines, conectores o condiciones relevantes.
5. Entregar la constancia de recepción prevista por el proceso interno.

## 5. Verificar la derivación

1. Confirmar que la observación sea comprensible sin consultar nuevamente a quien atendió.
2. Confirmar que fotos y videos estén adjuntos o localizables.
3. Confirmar que los productos recibidos coincidan con la descripción.
4. Señalar expresamente cualquier producto relacionado que no haya ingresado.

---

# Procedimiento para Ventas online

## 1. Realizar la preclasificación

1. Identificar la compra y la configuración completa por chat, formulario o canal autorizado.
2. Solicitar la descripción del síntoma mediante preguntas concretas.
3. Solicitar fotos, videos, capturas o códigos cuando puedan mostrar la falla.
4. No indicar el envío de un único componente basándose solamente en el diagnóstico del cliente.

## 2. Definir el alcance antes del envío

1. Priorizar el envío del equipo completo o del conjunto de componentes relacionados.
2. Consultar a RMA si el traslado completo es complejo, costoso o riesgoso.
3. Informar por escrito qué productos y accesorios deben enviarse.
4. Evitar modificar el alcance después de que el cliente ya preparó o despachó el paquete, salvo nueva información relevante.

## 3. Conservar la información

1. Trasladar al ingreso la descripción completa recopilada durante la conversación.
2. Adjuntar la evidencia o dejar una referencia precisa para localizarla.
3. Registrar pruebas y diagnósticos externos como antecedentes.
4. Mantener asociadas las conversaciones, archivos y número de gestión conforme al sistema interno.

## 4. Confirmar antes de cerrar

Enviar al cliente un resumen con:

- Síntoma registrado.
- Productos que debe remitir.
- Accesorios requeridos.
- Evidencias recibidas.
- Elementos que no debe enviar.

---

# Lista de control antes de derivar a RMA

| Control | Obligatorio |
|---------|:-----------:|
| Compra y productos identificados | Sí |
| Síntoma descrito sin diagnóstico asumido | Sí |
| Momento, frecuencia y pasos de reproducción | Sí |
| Configuración del equipo registrada | Sí |
| Cambios y pruebas previas registrados | Sí |
| Diagnóstico externo marcado como antecedente | Cuando exista |
| Equipo completo o alcance justificado | Sí |
| Todos los productos y accesorios recibidos enumerados | Sí |
| Evidencia adjunta o ubicación registrada | Cuando exista |
| Estado físico documentado | Sí |
| Componentes relacionados que no ingresaron señalados | Cuando corresponda |
| Consulta a RMA realizada | Cuando el alcance sea dudoso |

Si falta un dato esencial o el conjunto recibido no permite reproducir razonablemente la falla, el ingreso no debe derivarse como completo sin dejar constancia y consultar a RMA.

---

# Responsabilidades

## Ventas

- Recopilar información suficiente.
- Diferenciar síntoma, hipótesis y diagnóstico externo.
- Solicitar el alcance correcto de productos.
- Preservar y referenciar la evidencia.
- No prometer una causa, reparación, cambio o cobertura antes del diagnóstico de RMA.

## RMA

- Asistir a Ventas cuando el alcance no resulte claro.
- Informar qué combinación mínima permite una prueba concluyente.
- Registrar si el ingreso fue insuficiente y qué elemento faltó.
- Retroalimentar este procedimiento cuando aparezcan patrones repetitivos.

## Cliente

- Describir el comportamiento y entregar la configuración solicitada.
- Informar modificaciones y pruebas previas.
- Facilitar evidencia disponible.
- Proteger o respaldar su información personal conforme a las indicaciones del proceso de garantía.

---

# Puntos críticos

- Un componente puede funcionar correctamente por separado y fallar únicamente al interactuar con CPU, motherboard, RAM, GPU, fuente, firmware o software específicos.
- Una prueba externa sin metodología documentada no permite conocer qué variables fueron controladas.
- Recibir sólo el componente señalado puede duplicar traslados y reiniciar el diagnóstico desde cero.
- Una falla intermitente requiere más detalle que una falla permanente: frecuencia, tiempo y condición son esenciales.
- Fotos y videos pierden utilidad si RMA no sabe que existen o no puede encontrarlos.
- En un kit de memoria debe recibirse el kit completo, no sólo el módulo que el cliente considera defectuoso.
- Un equipo que «no da imagen» puede estar detenido en CPU, DRAM, VGA, alimentación o POST; no debe clasificarse automáticamente como falla de GPU.

---

# Desvíos de procedimiento

Se consideran desvíos:

- Ingresar un único componente de un armado relacionado basándose sólo en la opinión del cliente o de un técnico externo.
- Registrar un diagnóstico como confirmado sin validación de RMA.
- Utilizar descripciones genéricas que no indiquen cómo se manifiesta la falla.
- Omitir la configuración donde ocurrió el problema.
- No informar que existen fotos, videos, capturas o informes enviados previamente.
- Dejar evidencia en un chat sin adjuntarla ni indicar cómo localizarla.
- Recibir una PC completa armada por la empresa como componentes separados sin indicación de RMA.
- Omitir cargador o accesorios directamente relacionados con la falla.
- Prometer un cambio o atribuir responsabilidades antes del diagnóstico técnico.

---

# Documentos relacionados

- [RMA-002 - Sin POST con memorias KLEVV FIT V en Intel LGA1851](../03-Casos-RMA/RMA-002-Sin-POST-con-memorias-KLEVV-FIT-V-en-Intel-LGA1851.md), como ejemplo de una falla que sólo pudo delimitarse mediante pruebas cruzadas de varios componentes.
- [COMP-003 - Memorias KLEVV FIT V con plataforma Intel LGA1851](../05-Compatibilidades/COMP-003-Memorias-KLEVV-FIT-V-con-Intel-LGA1851.md), como ejemplo de incompatibilidad entre componentes que funcionan en otras plataformas.

---

# Historial de cambios

| Versión | Fecha | Descripción |
|---------|-------|-------------|
| 1.0 | 2026-09-12 | Creación del procedimiento de recepción presencial y online, matriz por síntomas y requisitos de información y evidencia. |
