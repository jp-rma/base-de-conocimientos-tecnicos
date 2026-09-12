# RMA-002 - Sin POST con memorias KLEVV FIT V en Intel LGA1851

| Campo | Valor |
|-------|-------|
| **Código** | RMA-002 |
| **Categoría** | Caso RMA |
| **Área** | RMA, Taller de Armado, Soporte Técnico Virtual y Ventas |
| **Estado** | En análisis |
| **Versión** | 1.1 |
| **Fecha de las pruebas** | No registrada |
| **Fecha de creación** | 2026-09-12 |
| **Última actualización** | 2026-09-12 |

---

# Resumen ejecutivo

Se comprobó de forma repetida que tres productos de memoria **DDR5 KLEVV FIT V de 6000 MT/s** impiden que equipos Intel LGA1851 completen el POST. El comportamiento se observó utilizando procesadores Intel Core Ultra 5 225, Core Ultra 7 265K y Core Ultra 7 265F, además de motherboards ASUS y ASRock con chipsets Z890 y B860.

La falla se mantiene con un módulo, con dos módulos y al mezclar una memoria KLEVV con otra marca. En cambio, las mismas memorias KLEVV funcionan en plataformas AMD AM5 e Intel LGA1700, mientras que los equipos LGA1851 probados completan el POST con memorias de otras marcas. Las actualizaciones de BIOS disponibles durante las pruebas no corrigieron el comportamiento.

La evidencia valida una **incompatibilidad operacional reproducible** entre los productos KLEVV FIT V relevados y las configuraciones LGA1851 probadas. No permite identificar todavía el mecanismo causal exacto. Las hipótesis principales son una interacción del BIOS/Intel Memory Reference Code con la información SPD, el SPD Hub o el PMIC de los módulos, o una falla durante el entrenamiento eléctrico de la memoria.

!!! danger "Criterio operativo vigente"

    No instalar, mezclar, ofrecer ni utilizar como reemplazo los códigos internos **21783**, **21664** o **21782** en equipos Intel LGA1851. La acción correctiva validada es retirar todos los módulos KLEVV involucrados y utilizar memoria DDR5 de otra marca comprobada con el modelo exacto de motherboard y CPU.

---

# Síntoma informado

- El equipo recibe alimentación y enciende, pero no completa el POST.
- No se obtiene imagen.
- El comportamiento aparece siempre que exista al menos un módulo KLEVV FIT V relevado en el sistema.
- La falla no cambia al utilizar un solo módulo o dos módulos.
- La instalación simultánea de una memoria de otra marca no permite iniciar mientras permanezca instalada la KLEVV.
- La actualización del BIOS no resolvió el caso.

La ausencia de imagen es una consecuencia de que el equipo no alcanza el POST; por sí sola no demuestra una falla de GPU, cable o monitor.

---

# Alcance del caso

## Memorias involucradas

La siguiente correspondencia entre código interno y número de parte se obtuvo comparando capacidad, color, velocidad y latencia con el [catálogo oficial vigente de KLEVV](https://www.klevv.com/ken/products_details/memory/Klevv_FITV). Debe confirmarse con la etiqueta física antes de remitir el caso al fabricante.

| Código interno | Descripción interna | Número de parte KLEVV esperado | EAN esperado | Configuración |
|----------------|---------------------|--------------------------------|--------------|---------------|
| 21783 | DDR5 32 GB 6000 MT/s KLEVV FIT V Black CL28 | `KD5AGU880-60B280L` | `4895194969037` | Kit 2 × 16 GB |
| 21664 | DDR5 32 GB 6000 MT/s KLEVV FIT V Black CL30 | `KD5AGU880-60A300L` | `4895194968795` | Kit 2 × 16 GB |
| 21782 | DDR5 16 GB 6000 MT/s KLEVV FIT V White CL30 | `KD5AGU880-60A300Q` | `4895194968337` | Módulo 1 × 16 GB |

KLEVV especifica en la [página oficial de FIT V](https://www.klevv.com/ken/products_details/memory/Klevv_FITV) los siguientes parámetros:

| Parámetro | Especificación oficial |
|-----------|------------------------|
| Formato | DDR5 UDIMM sin búfer, 288 pines |
| Velocidad SPD de arranque | 4800 MT/s |
| Temporización SPD | 40-40-40-77 |
| Voltaje SPD | 1,1 V |
| Velocidad probada de los productos relevados | 6000 MT/s |
| Perfiles publicados | Intel XMP y AMD EXPO |
| Gestión de energía | PMIC integrado en el módulo |

Los 6000 MT/s y las latencias CL28/CL30 corresponden a parámetros probados de overclocking. No son los parámetros SPD conservadores con los que el módulo debería realizar su primer arranque.

## Procesadores probados

| Procesador | Plataforma | Gráficos integrados según Intel | Resultado con KLEVV relevada |
|------------|------------|---------------------------------|-------------------------------|
| Intel Core Ultra 5 225 | Core Ultra 200S, LGA1851 | Sí | Sin POST y sin imagen |
| Intel Core Ultra 7 265K | Core Ultra 200S, LGA1851 | Sí | Sin POST y sin imagen |
| Intel Core Ultra 7 265F | Core Ultra 200S, LGA1851 | No | Sin POST; la validación de video requiere GPU dedicada |

Intel incluye los tres modelos dentro de la familia Core Ultra 200S y publica DDR5-6400 como velocidad máxima de memoria de la familia, sujeta a la configuración concreta ([Intel Core Ultra Desktop Processors Series 2](https://www.intel.com/content/www/us/en/products/docs/processors/core-ultra/core-ultra-desktop-processors-series-2-brief.html)). El sufijo `F` identifica al Core Ultra 7 265F sin gráficos integrados; esta condición puede explicar una ausencia de imagen si se utiliza una salida del motherboard, pero no explica la incompatibilidad general porque el caso también se reproduce con el Core Ultra 5 225 y el Core Ultra 7 265K, ni porque los mismos equipos inician con otra memoria.

## Motherboards probados

| Fabricante | Modelo | Chipset | Slots DDR5 | Resultado con KLEVV relevada |
|------------|--------|---------|-------------|-------------------------------|
| ASUS | ROG Strix Z890-A Gaming WiFi | Intel Z890 | 4 | Sin POST y sin imagen |
| ASRock | Phantom Gaming Z890 Nova WiFi | Intel Z890 | 4 | Sin POST y sin imagen |
| ASUS | ROG Strix B860-A Gaming WiFi | Intel B860 | 4 | Sin POST y sin imagen |

ASUS y ASRock declaran soporte para procesadores Intel Core Ultra Series 2 y memorias DDR5 en la [ROG Strix B860-A Gaming WiFi](https://dlcdnets.asus.com/pub/ASUS/mb/LGA1851/ROG_STRIX_B860-A_GAMING_WIFI/E25226_ROG_STRIX_B860-A_GAMING_WIFI_EM_WEB.pdf?model=ROG+STRIX+B860-A+GAMING+WIFI), la [ROG Strix Z890-A Gaming WiFi](https://rog.asus.com/motherboards/rog-strix/rog-strix-z890-a-gaming-wifi/spec/) y la [ASRock Z890 Nova WiFi](https://pg.asrock.com/mb/Intel/Z890%20Nova%20WiFi/index.asp). Esta compatibilidad general de interfaz no garantiza el funcionamiento de todos los números de parte de memoria.

## Datos de configuración todavía no registrados

- Cantidad de unidades físicas probadas por cada código interno.
- Matriz individual de cada combinación CPU × motherboard × memoria.
- Número de serie, lote y código de fecha de cada módulo.
- Número de parte leído directamente desde cada etiqueta.
- Revisión exacta de PCB, chips DRAM, SPD Hub y PMIC.
- Versión exacta de BIOS, Intel MRC, microcódigo e Intel ME utilizada en cada prueba.
- Slots utilizados en cada combinación.
- Estado de XMP, AEMP, Memory Fast Boot/MRC Fast Boot y demás ajustes de memoria.
- Realización de Clear CMOS antes de cada prueba.
- Código Dr. Debug o secuencia de Q-LED observada.
- Modelos exactos utilizados como memoria de control, plataforma AM5 y plataforma LGA1700.

Estos datos faltantes no invalidan la incompatibilidad operacional observada, pero impiden atribuir con certeza la causa raíz.

---

# Evidencia experimental consolidada

## Pruebas informadas

| Prueba | Variable de control | Resultado | Conclusión respaldada |
|--------|---------------------|-----------|-----------------------|
| KLEVV relevada en AMD AM5 | Se cambia la plataforma | Funcionamiento normal | No existe una falla general que impida utilizar el módulo en toda plataforma DDR5. |
| KLEVV relevada en Intel LGA1700 | Se cambia la plataforma Intel | Funcionamiento normal | La incompatibilidad no afecta a todas las plataformas Intel DDR5. |
| Memoria de otra marca en equipos LGA1851 | Se cambia la memoria | POST normal | Los CPUs y motherboards LGA1851 probados pueden inicializar memoria DDR5. |
| Una KLEVV en LGA1851 | Se minimiza la población | Sin POST | La falla no requiere dual channel ni dos módulos. |
| Dos KLEVV en LGA1851 | Se utiliza el kit | Sin POST | La instalación del kit completo no resuelve la inicialización. |
| KLEVV + otra marca en LGA1851 | Se agrega un módulo funcional | Sin POST | Un módulo funcional no puede compensar la falla provocada por la presencia de la KLEVV. |
| BIOS actualizado | Se cambia el firmware disponible | Sin cambios | Las revisiones utilizadas no contienen una corrección efectiva para el caso. |
| Distintos CPUs LGA1851 | Se cambia el controlador de memoria físico | Mismo síntoma | Reduce la probabilidad de un IMC defectuoso en una unidad particular. |
| ASUS Z890, ASRock Z890 y ASUS B860 | Se cambia fabricante y chipset | Mismo síntoma | Reduce la probabilidad de una falla exclusiva de un modelo de motherboard. |

!!! note "Alcance de la matriz"

    La información disponible confirma que se utilizaron los componentes enumerados, pero no registra que se haya ejecutado el producto cartesiano completo de todas las combinaciones. No corresponde afirmar que se realizaron 27 configuraciones independientes sin una planilla de prueba que lo demuestre.

---

# Marco técnico

## Qué ocurre antes del POST

El controlador de memoria está integrado en el procesador Core Ultra 200S. Intel documenta dos instancias independientes de controlador, una por cada *memory slice*, capaces de administrar canales DDR5 ([Intel - Memory Controller](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/007/memory-controller-mc/)). Antes de que el sistema pueda mostrar el BIOS o iniciar video, el firmware debe detectar los DIMM, obtener su configuración y entrenar el enlace entre el controlador y la DRAM.

DDR5 agrega componentes activos al módulo. El **SPD Hub** conserva la información SPD y funciona como interfaz entre el host y otros componentes del DIMM mediante el bus lateral compatible con I3C/I²C. El **PMIC** realiza la regulación local y permite configurar secuencias y niveles de alimentación ([Micron - DDR5 Key Module Features](https://www.micron.com/content/dam/micron/global/public/products/white-paper/ddr5-key-module-features-wp-client.pdf)). Una falla en cualquiera de esas etapas puede detener la inicialización antes del POST, aunque los chips DRAM no estén físicamente dañados.

Intel confirma que el BIOS ejecuta el **Memory Reference Code (MRC)** durante el entrenamiento. Entre otras tareas, el MRC ajusta terminaciones ODT, fuerza de los drivers y parámetros del controlador y la DRAM para buscar un margen operativo válido ([Intel - Power Training](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/power-training/)).

Una representación simplificada es:

```text
Encendido
   ↓
Detección del DIMM y comunicación con el SPD Hub
   ↓
Lectura de geometría, perfiles JEDEC y datos del módulo
   ↓
Inicialización del PMIC y de los chips DRAM
   ↓
Configuración del IMC por BIOS/MRC
   ↓
Entrenamiento de comandos, reloj y señales de datos
   ↓
Prueba inicial de memoria
   ↓
POST y posterior inicialización de video
```

El caso sólo permite ubicar la falla de manera general antes del POST. Sin códigos de diagnóstico o trazas de firmware no es posible determinar en cuál de estas etapas se detiene.

## Parámetros SPD frente a XMP/EXPO

KLEVV publica un SPD base de **DDR5-4800, 40-40-40-77 y 1,1 V** en las [especificaciones de FIT V](https://www.klevv.com/ken/products_details/memory/Klevv_FITV), mientras que los 6000 MT/s CL28/CL30 utilizan perfiles de rendimiento con voltajes superiores. Intel indica que un módulo XMP debe realizar el primer arranque con parámetros JEDEC predeterminados antes de que el usuario active el perfil de overclocking ([Intel Extreme Memory Profile](https://www.intel.com/content/www/us/en/gaming/extreme-memory-profile-xmp.html)).

El controlador Core Ultra 200S contempla DDR5-4800 con CAS 40 dentro de su [tabla oficial de temporizaciones](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/005/system-memory-timing-support/). Por lo tanto, no existe una contradicción evidente entre la velocidad y el CAS SPD publicados por KLEVV y los valores base aceptados por Intel.

Esta comparación hace menos probable que el problema sea simplemente «6000 MT/s es demasiado». Si el BIOS fue restablecido y XMP permaneció desactivado, deben investigarse otros campos SPD, la identificación del módulo, la revisión del SPD Hub/PMIC, la geometría de los chips y el entrenamiento eléctrico.

## UDIMM, CUDIMM y topología de slots

FIT V es un **UDIMM convencional**, no un CUDIMM con controlador de reloj. Intel admite UDIMM y CUDIMM de 288 pines en procesadores de escritorio Core Ultra 200S, pero establece límites distintos según el tipo de módulo y la topología 1DPC/2DPC ([Intel - Processor SKU Support Matrix](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/processor-sku-support-matrix/)).

Las tres motherboards probadas poseen cuatro slots, es decir, hasta dos DIMM físicos por canal. La matriz detallada de Intel contempla para una placa 2DPC velocidades base inferiores a las máximas comerciales cuando aumenta la población. Esto afecta la velocidad garantizada, pero no explica que un único FIT V no pueda arrancar a su SPD de 4800 MT/s.

## Qué significa realmente la QVL

Una QVL registra combinaciones que pasaron el proceso de validación del fabricante; no constituye una garantía genérica por marca o familia. ASUS recomienda comprobar el número de parte exacto y, si una memoria incluida presenta problemas, actualizar el BIOS y contactar soporte ([ASUS - Cómo consultar la QVL](https://www.asus.com/support/FAQ/1043883)).

La documentación vigente de KLEVV aporta tres precisiones importantes:

1. [FIT V soporta perfiles Intel XMP y AMD EXPO](https://www.klevv.com/ken/products_details/memory/Klevv_FITV), pero esa característica describe el formato de los perfiles de overclocking.
2. La [ficha técnica actual](https://www.klevv.com/HyAdmin/upload/goodFile/KLEVV_Product%20Sheet_MEMORY_FIT%20V_v5_EN.pdf?2026010501=) limita su nota de compatibilidad a Ryzen 9000 y anteriores e **Intel de 14.ª generación y anteriores**; no declara Core Ultra 200S ni LGA1851.
3. La [lista oficial FIT V actualizada en agosto de 2026](https://www.klevv.com/HyAdmin/upload/goodFile/KLEVV%20FIT%20V%20DDR5%20Memory%20Compatibility%20List_Aug26.pdf) contiene únicamente plataformas AMD. No incluye Intel, Z890, B860 ni ninguno de los tres motherboards de este caso.

En consecuencia, la frase «soporta Intel XMP» no debe interpretarse como «validada con Intel LGA1851». Tampoco se encontró una publicación oficial de KLEVV que describa este síntoma o anuncie una corrección.

---

# Hipótesis causales

| Prioridad | Hipótesis | Evidencia a favor | Evidencia faltante o en contra |
|-----------|-----------|------------------|--------------------------------|
| Alta | Interacción entre Intel MRC/BIOS y datos SPD de FIT V | La falla aparece antes del POST, atraviesa ASUS/ASRock y desaparece al retirar KLEVV. | Falta leer y comparar el SPD binario de cada lote. |
| Media-alta | Revisión común de SPD Hub o programación del bus lateral | DDR5 depende del SPD Hub para exponer datos y acceder a componentes; distintos productos FIT V pueden compartir componentes o firmware. | No se identificó el fabricante ni la revisión del hub de las unidades. |
| Media | Inicialización o configuración del PMIC | FIT V utiliza PMIC integrado y el problema ocurre antes de disponer de memoria operativa. | Los módulos funcionan en AM5 y LGA1700; sería una interacción específica, no un PMIC totalmente defectuoso. |
| Media | Falla de entrenamiento eléctrico con el diseño común del DIMM | Intel MRC ajusta ODT, drivers y márgenes; un diseño puede entrenar en LGA1700/AM5 y fallar con otro IMC. | Falta código de etapa, telemetría de entrenamiento y datos de PCB/chips. |
| Baja-media | Estado residual de XMP/AEMP o datos de entrenamiento almacenados | Un perfil previo puede alterar frecuencia, voltajes o reentrenamiento. | La repetición en varias placas reduce la probabilidad; falta confirmar Clear CMOS antes de cada prueba. |
| Baja | Límite de 6000 MT/s | 6000 MT/s es un perfil de overclocking en estos UDIMM. | El SPD base es 4800 MT/s y XMP debería arrancar primero en modo JEDEC. |
| Muy baja | Falla física general de las memorias | Explicaría la falta de POST. | Funcionan en AM5 y LGA1700. |
| Muy baja | CPU o motherboard individual defectuosos | Una unidad defectuosa puede fallar al entrenar DRAM. | Se reprodujo con múltiples CPUs, dos fabricantes de motherboard y dos chipsets; otras memorias funcionan. |
| Descartada como causa general | Ausencia de iGPU | El Core Ultra 7 265F no tiene gráficos integrados. | No explica el POST fallido ni las pruebas con 225/265K; el 265F debe probarse con GPU dedicada. |

## Hipótesis principal: interpretación SPD o selección de parámetros

El SPD no contiene únicamente la velocidad comercial y el CAS. Describe organización, densidad, ranks, temporizaciones, revisiones, identificación del fabricante, perfiles y otros datos que el BIOS utiliza para construir la configuración inicial. [Intel XMP 3.0](https://www.intel.com/content/www/us/en/gaming/extreme-memory-profile-xmp.html) permite además campos y perfiles ampliados en DDR5.

Un campo válido pero no contemplado, una relación de temporizaciones que active una ruta defectuosa del MRC, una revisión distinta del módulo o un problema de lectura pueden producir un fallo antes del POST. El hecho de que CL28, CL30, kit doble y módulo individual compartan el síntoma sugiere buscar primero aquello que comparten: familia de PCB, DRAM, SPD Hub, PMIC o plantilla de programación SPD.

Esta hipótesis no implica necesariamente que el SPD incumpla una especificación. También puede existir un defecto en la forma en que una versión del MRC interpreta una combinación válida.

## Hipótesis SPD Hub / bus lateral

En DDR5, el host no trata al SPD como una memoria pasiva aislada. El SPD Hub administra la comunicación lateral y puede dar acceso local a componentes como el PMIC ([Micron - DDR5 Key Module Features](https://www.micron.com/content/dam/micron/global/public/products/white-paper/ddr5-key-module-features-wp-client.pdf)). Una diferencia de revisión, temporización de respuesta, direccionamiento o inicialización podría impedir la detección correcta del DIMM en LGA1851.

La falla con un único módulo es compatible con esta hipótesis. El fallo al mezclar KLEVV con otra marca también lo es: el BIOS necesita completar la detección e inicialización de todos los DIMM instalados antes de construir una configuración utilizable. Un módulo funcional no neutraliza a otro que detiene esa etapa.

## Hipótesis PMIC

El PMIC de DDR5 recibe alimentación desde la placa y genera localmente los rieles que utiliza la DRAM. Su configuración incluye niveles, rampas, protecciones y secuencias de encendido ([Micron - DDR5 Key Module Features](https://www.micron.com/content/dam/micron/global/public/products/white-paper/ddr5-key-module-features-wp-client.pdf)). Una interacción entre una revisión de PMIC y la secuencia aplicada por el firmware LGA1851 puede impedir que la DRAM quede lista para entrenamiento.

Como FIT V funciona en otras plataformas, la hipótesis sería una incompatibilidad de secuencia o programación, no una ausencia total de alimentación ni una falla universal del PMIC.

## Hipótesis de entrenamiento eléctrico

El entrenamiento ajusta parámetros del controlador y de la DRAM para encontrar ventanas de lectura/escritura estables. Intel documenta que el MRC modifica terminaciones ODT, fuerza de drivers y buffers buscando equilibrio entre consumo y margen operativo ([Intel - Power Training](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/power-training/)).

Un PCB, una organización de ranks/chips o una combinación de características eléctricas puede tener margen suficiente con los IMC de AM5 y LGA1700, pero no con la ruta de entrenamiento utilizada por Core Ultra 200S. El uso de dos fabricantes de motherboard reduce la probabilidad de un defecto exclusivo del trazado de una placa; no elimina una interacción común entre FIT V, el IMC LGA1851 y el MRC compartido por el ecosistema.

## Papel del BIOS, MRC, microcódigo e Intel ME

Los fabricantes publican regularmente cambios de compatibilidad de memoria. ASUS actualizó MRC y compatibilidad DDR5 en el [historial de BIOS de la ROG Strix B860-A Gaming WiFi](https://www.asus.com/au/supportonly/rog%20strix%20b860-a%20gaming%20wifi/helpdesk_bios/); ASRock publicó varias revisiones para mejorar compatibilidad de memoria en el [historial de BIOS de la Z890 Nova WiFi](https://pg.asrock.com/mb/intel/Z890%20Nova%20WiFi/bios.html).

Esto demuestra que la compatibilidad no depende únicamente del hardware. Sin embargo, que «el BIOS esté actualizado» no prueba que incluya una corrección para estos números de parte. Para hacer reproducible el caso deben registrarse la versión exacta, fecha, MRC, microcódigo e Intel ME de cada ensayo.

---

# Diagnóstico

**Diagnóstico operacional validado:** incompatibilidad reproducible entre las memorias DDR5 KLEVV FIT V correspondientes a los códigos internos 21783, 21664 y 21782 y las configuraciones Intel LGA1851 probadas.

**Clasificación:** incompatibilidad de plataforma durante la inicialización de memoria; no se observa evidencia suficiente para clasificar los módulos como físicamente defectuosos.

**Causa raíz técnica:** pendiente. La evidencia actual favorece una interacción entre el diseño o datos de los DIMM y el BIOS/Intel MRC durante detección o entrenamiento.

**Componentes descartados como causa única:** una unidad particular de CPU, un único modelo de motherboard, un único chipset, la utilización de dual channel y el subsistema de video general.

**Solución comprobada:** retirar todos los módulos KLEVV involucrados e instalar memoria DDR5 de otra marca validada con la plataforma.

---

# Metodología recomendada para cerrar la causa raíz

## Preparación y trazabilidad

1. Fotografiar las etiquetas sin publicar números de serie en el repositorio público.
2. Registrar código interno, P/N, EAN, número de serie, lote y código de fecha en el sistema interno de RMA.
3. Registrar modelo y revisión completa del motherboard.
4. Registrar CPU, BIOS, MRC, microcódigo e Intel ME.
5. Registrar fuente, GPU utilizada y método de salida de video.
6. Identificar cada módulo físicamente como `K1`, `K2`, etcétera para no perder trazabilidad.

## Configuración mínima

1. Desconectar el equipo de la red eléctrica.
2. Realizar Clear CMOS conforme al manual.
3. Utilizar CPU, cooler, motherboard, fuente, GPU cuando el CPU no posea iGPU, teclado y un único monitor.
4. Retirar almacenamiento y periféricos no necesarios.
5. Arrancar primero con una memoria de control validada.
6. Cargar valores predeterminados del BIOS y dejar XMP/AEMP y overclocking desactivados.
7. Apagar, desconectar y sustituir únicamente la memoria.

## Secuencia de pruebas por módulo

| Paso | Configuración | Registro obligatorio | Criterio |
|------|---------------|----------------------|----------|
| 1 | Un módulo de control en A2 | Tiempo hasta POST, Q-LED/Dr. Debug | Confirma plataforma base |
| 2 | Una KLEVV en A2 | Código final, secuencia de LEDs, tiempo observado | Reproducción principal |
| 3 | La misma KLEVV en B2 | Código final y tiempo | Diferencia por canal/slot |
| 4 | Cada módulo del kit probado por separado en A2 | Identidad del módulo y resultado | Descarta una única unidad del kit |
| 5 | Kit KLEVV en A2/B2 | Código y tiempo | Validación de dos módulos |
| 6 | KLEVV + control | Identidad y posición de cada módulo | Confirma efecto de mezcla |
| 7 | Módulo de control nuevamente | POST y estabilidad | Confirma que la plataforma continúa funcional |
| 8 | KLEVV en LGA1700 y AM5 | Placa, CPU, BIOS y slot | Control positivo del DIMM |

El [manual de ASUS ROG Strix B860-A Gaming WiFi](https://dlcdnets.asus.com/pub/ASUS/mb/LGA1851/ROG_STRIX_B860-A_GAMING_WIFI/E25226_ROG_STRIX_B860-A_GAMING_WIFI_EM_WEB.pdf?model=ROG+STRIX+B860-A+GAMING+WIFI) indica A2 para un DIMM y A2/B2 para dos, y aclara que el Q-LED amarillo identifica DRAM como causa probable, no definitiva. En ASRock, deben registrarse los valores del Dr. Debug: los códigos 53 y 54 corresponden a errores de inicialización de memoria, mientras que 55 indica memoria no instalada ([ASRock - Debug LED Troubleshooting Checklist](https://asrock.com/support/index.asp?cat=Debug)).

## Lectura técnica del SPD

Desde una plataforma donde la KLEVV complete el POST, conservar una exportación íntegra del SPD y, si la herramienta lo permite, el binario original. Registrar como mínimo:

- P/N y fabricante informados.
- Revisión de SPD y estado de CRC.
- Capacidad, ranks, ancho de dispositivo y densidad de los chips.
- Revisión de raw card o diseño de referencia.
- Fabricante y revisión de DRAM.
- Fabricante, modelo y revisión del SPD Hub.
- Fabricante, modelo, revisión y modo del PMIC.
- Todos los perfiles JEDEC.
- Perfiles XMP y EXPO, incluyendo frecuencia, voltajes y temporizaciones.
- Campos específicos del fabricante.

El resultado debe compararse entre:

- CL28 frente a CL30.
- Black frente a White.
- Módulo individual frente a los dos integrantes de cada kit.
- Dos unidades del mismo código interno pero de lotes diferentes.
- Un lote que falle frente a cualquier futura unidad que complete el POST.

No se debe reprogramar el SPD como parte del diagnóstico ordinario. Una escritura incorrecta puede inutilizar el módulo, alterar la garantía y crear una configuración no validada.

## Pruebas que discriminan las hipótesis

| Resultado futuro | Interpretación más probable |
|------------------|-----------------------------|
| Otro lote con el mismo P/N funciona | Cambio de BOM, revisión de DRAM, SPD Hub, PMIC o programación SPD entre lotes |
| Todos los lotes fallan y un BIOS futuro los corrige | Defecto o limitación de BIOS/MRC |
| SPD corregido oficialmente por KLEVV permite iniciar | Problema en contenido SPD o interacción con su interpretación |
| Falla en código 53/54 o DRAM LED fijo | Detención en detección/inicialización de memoria; todavía no identifica SPD, PMIC o entrenamiento por separado |
| Falla sólo con XMP y arranca en JEDEC | Problema de perfil de overclocking, voltaje o margen a 6000 MT/s |
| Falla también con CMOS limpio a SPD 4800 | Descarta que la frecuencia XMP sea la explicación principal |
| Falla cambia al utilizar A2 frente a B2 | Posible canal, socket, contacto, trazado o margen eléctrico |
| La misma KLEVV deja de funcionar también en las plataformas de control | Posible daño o degradación física del módulo |

---

# Acción correctiva

- Retirar **todos** los módulos KLEVV FIT V involucrados del equipo LGA1851.
- Instalar un kit DDR5 de otra marca incluido en la QVL o validado internamente con el P/N exacto.
- Utilizar un solo kit homogéneo; no mezclar KLEVV con otro fabricante.
- Cargar valores predeterminados del BIOS antes de la primera prueba.
- Confirmar POST, capacidad detectada y funcionamiento en los slots recomendados.
- Ejecutar una prueba de memoria completa y varios ciclos de arranque en frío y reinicio.
- Registrar el kit finalmente instalado y la versión de BIOS.

La actualización de BIOS puede volver a probarse cuando el changelog mencione compatibilidad de memoria, pero no debe utilizarse como promesa de solución sin validación interna del P/N afectado.

---

# Acción preventiva

## Ventas

- Bloquear las combinaciones de los códigos 21783, 21664 y 21782 con CPUs o motherboards LGA1851.
- No interpretar los logotipos XMP/EXPO como compatibilidad universal.
- Verificar P/N exacto, QVL del motherboard y validación interna antes de ofrecer una alternativa.

## Taller de Armado

- Consultar [COMP-003](../05-Compatibilidades/COMP-003-Memorias-KLEVV-FIT-V-con-Intel-LGA1851.md) antes de iniciar un armado LGA1851.
- Registrar Q-LED o Dr. Debug y no limitar el informe a «no da imagen».
- Realizar Clear CMOS, utilizar el slot recomendado y probar cada módulo por separado.
- Verificar especialmente la presencia de GPU dedicada cuando se utilice un procesador con sufijo `F`.

## RMA y Soporte

- Aplicar primero el cambio cruzado de memoria, porque diferencia rápidamente una incompatibilidad de una falla general del equipo.
- No reemplazar CPU, motherboard, fuente o GPU sin comprobar la plataforma con memoria de control.
- Conservar trazabilidad de lotes y P/N para detectar cambios de BOM.
- Adjuntar nuevos resultados a este caso y revisar el estado cuando aparezca una solución reproducible.

---

# Información requerida para escalar a KLEVV, ASUS, ASRock o Intel

El paquete técnico debe incluir:

- Resumen del síntoma y confirmación de que no se alcanza el POST.
- Matriz CPU × motherboard × DIMM con resultado individual.
- P/N, EAN, serial, lote y código de fecha de cada módulo.
- Fotografías de ambas caras y etiquetas.
- Dump SPD binario y reporte legible.
- Identificación de DRAM, raw card, SPD Hub y PMIC.
- BIOS, MRC, microcódigo e Intel ME.
- Slots utilizados y estado de XMP/AEMP.
- Confirmación de Clear CMOS.
- Código Dr. Debug, Q-LED y duración de cada intento.
- Resultado con memoria de control.
- Resultado del mismo módulo en AM5 y LGA1700.
- Identidad del lote de cualquier unidad equivalente que sí funcione.

Preguntas concretas para KLEVV:

1. ¿Los P/N afectados fueron validados con Core Ultra 200S, Z890 o B860?
2. ¿Existen revisiones de BOM o SPD diferentes bajo el mismo P/N?
3. ¿Qué DRAM, SPD Hub y PMIC corresponden a cada lote?
4. ¿Existe una actualización oficial de SPD o un lote revisado para LGA1851?
5. ¿Puede KLEVV reproducir la falla con los dumps y versiones de BIOS entregados?

---

# Limitaciones

- No se dispone de dumps SPD ni identificación de los componentes activos de los módulos.
- No se registraron las versiones exactas de firmware de cada prueba.
- No se registró la matriz completa de combinaciones ni la cantidad de unidades por lote.
- No se conservaron códigos Q-LED/Dr. Debug ni mediciones eléctricas.
- El funcionamiento en AM5 y LGA1700 se informó como normal, pero faltan modelos y condiciones exactas.
- No puede determinarse si todos los productos comparten la misma revisión de hardware únicamente por su denominación comercial.
- Las hipótesis SPD, SPD Hub, PMIC y entrenamiento son inferencias técnicas coherentes con la evidencia, no causas confirmadas por el fabricante.
- La ausencia de un P/N en una QVL significa que no existe validación pública documentada en esa lista; no demuestra por sí sola una incompatibilidad universal.
- Una revisión futura de BIOS, MRC, hardware o SPD puede cambiar el resultado.

---

# Documentos relacionados

- [COMP-003 - Memorias KLEVV FIT V con plataforma Intel LGA1851](../05-Compatibilidades/COMP-003-Memorias-KLEVV-FIT-V-con-Intel-LGA1851.md)

---

# Referencias

1. KLEVV. [FIT V DDR5: especificaciones, perfiles SPD y números de parte](https://www.klevv.com/ken/products_details/memory/Klevv_FITV).
2. KLEVV. [Ficha técnica oficial de FIT V DDR5](https://www.klevv.com/HyAdmin/upload/goodFile/KLEVV_Product%20Sheet_MEMORY_FIT%20V_v5_EN.pdf?2026010501=).
3. KLEVV. [FIT V DDR5 Memory Compatibility List, agosto de 2026](https://www.klevv.com/HyAdmin/upload/goodFile/KLEVV%20FIT%20V%20DDR5%20Memory%20Compatibility%20List_Aug26.pdf).
4. Intel. [Intel Core Ultra Desktop Processors (Series 2) Product Brief](https://www.intel.com/content/www/us/en/products/docs/processors/core-ultra/core-ultra-desktop-processors-series-2-brief.html).
5. Intel. [Core Ultra 200S Datasheet: Memory Controller](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/007/memory-controller-mc/).
6. Intel. [Core Ultra 200S Datasheet: Power Training](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/power-training/).
7. Intel. [Core Ultra 200S Datasheet: System Memory Timing Support](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/005/system-memory-timing-support/).
8. Intel. [Core Ultra 200S Datasheet: Processor SKU Support Matrix](https://edc.intel.com/content/www/us/en/design/products/platforms/details/arrow-lake-s/core-ultra-200s-series-processors-datasheet-volume-1-of-2/processor-sku-support-matrix/).
9. Intel. [Intel Extreme Memory Profile (XMP)](https://www.intel.com/content/www/us/en/gaming/extreme-memory-profile-xmp.html).
10. Micron. [DDR5 Key Module Features](https://www.micron.com/content/dam/micron/global/public/products/white-paper/ddr5-key-module-features-wp-client.pdf).
11. ASUS. [Manual de ROG Strix B860-A Gaming WiFi](https://dlcdnets.asus.com/pub/ASUS/mb/LGA1851/ROG_STRIX_B860-A_GAMING_WIFI/E25226_ROG_STRIX_B860-A_GAMING_WIFI_EM_WEB.pdf?model=ROG+STRIX+B860-A+GAMING+WIFI).
12. ASUS. [Especificaciones de ROG Strix Z890-A Gaming WiFi](https://rog.asus.com/motherboards/rog-strix/rog-strix-z890-a-gaming-wifi/spec/).
13. ASUS. [Cómo consultar la lista QVL de CPU y memoria](https://www.asus.com/support/FAQ/1043883).
14. ASUS. [BIOS y firmware de ROG Strix B860-A Gaming WiFi](https://www.asus.com/au/supportonly/rog%20strix%20b860-a%20gaming%20wifi/helpdesk_bios/).
15. ASRock. [Z890 Nova WiFi: especificaciones](https://pg.asrock.com/mb/Intel/Z890%20Nova%20WiFi/index.asp).
16. ASRock. [BIOS de Z890 Nova WiFi](https://pg.asrock.com/mb/intel/Z890%20Nova%20WiFi/bios.html).
17. ASRock. [Debug LED Troubleshooting Checklist](https://asrock.com/support/index.asp?cat=Debug).

Referencias consultadas el **2026-09-12**.

---

# Historial de cambios

| Versión | Fecha | Descripción |
|---------|-------|-------------|
| 1.1 | 2026-09-12 | Reemplazo de las notas al pie por referencias visibles y enlaces directos dentro del análisis. |
| 1.0 | 2026-09-12 | Creación del análisis técnico, consolidación de pruebas, hipótesis causales, metodología de confirmación y fuentes oficiales. |
