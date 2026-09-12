# COMP-003 - Memorias KLEVV FIT V con plataforma Intel LGA1851

| Campo | Valor |
|-------|-------|
| **Código** | COMP-003 |
| **Categoría** | Compatibilidad / Incompatibilidad |
| **Área** | Ventas, Taller de Armado, RMA y Soporte Técnico Virtual |
| **Estado** | <span class="kb-status kb-status--ok">Vigente</span> |
| **Versión** | 1.1 |
| **Fecha de creación** | 2026-09-12 |
| **Última actualización** | 2026-09-12 |

---

# Objetivo

Documentar la incompatibilidad comprobada internamente entre las memorias **DDR5 KLEVV FIT V relevadas** y la plataforma **Intel LGA1851**, y evitar que estas combinaciones se ofrezcan, armen o utilicen como reemplazo hasta que exista una solución validada.

---

# Resumen de la incompatibilidad

Los equipos probados no completan el **POST** ni entregan imagen cuando se instala al menos un módulo KLEVV FIT V de los modelos indicados. El comportamiento se reproduce con diferentes procesadores Intel Core Ultra, motherboards con chipsets Z890 y B860 y configuraciones de memoria.

!!! danger "Combinación no autorizada para ventas ni armados"

    No utilizar las memorias KLEVV FIT V relevadas en equipos con socket Intel LGA1851. La restricción se mantiene aunque se instale un solo módulo, un kit de dos módulos o una memoria KLEVV junto con otra marca.

---

# Componentes involucrados

## Memorias KLEVV probadas

| Código interno | Descripción | Configuración |
|----------------|-------------|---------------|
| 21783 | DDR5 32 GB 6000 MT/s KLEVV FIT V Black CL28 | Kit 2 × 16 GB |
| 21664 | DDR5 32 GB 6000 MT/s KLEVV FIT V Black CL30 | Kit 2 × 16 GB |
| 21782 | DDR5 16 GB 6000 MT/s KLEVV FIT V White CL30 | Módulo 1 × 16 GB |

## Procesadores probados

- Intel Core Ultra 5 225.
- Intel Core Ultra 7 265K.
- Intel Core Ultra 7 265F.

## Motherboards probados

- ASUS ROG Strix Z890-A Gaming WiFi.
- ASRock Phantom Gaming Z890 Nova WiFi.
- ASUS ROG Strix B860-A Gaming WiFi.

---

# Resultado de las pruebas

## Matriz de aislamiento

| Prueba | Resultado | Interpretación |
|--------|-----------|----------------|
| Memorias KLEVV relevadas en plataforma AMD AM5 | Funcionamiento normal | Los módulos no presentan una falla general reproducible. |
| Memorias KLEVV relevadas en plataforma Intel LGA1700 | Funcionamiento normal | La incompatibilidad no afecta a todas las plataformas Intel DDR5. |
| Procesadores Intel Core Ultra LGA1851 con memorias de otras marcas | Funcionamiento normal | Los procesadores y equipos LGA1851 probados pueden completar el POST con otra memoria. |
| Un módulo KLEVV en LGA1851 | Sin POST y sin imagen | La falla no depende del uso de dos módulos. |
| Dos módulos KLEVV en LGA1851 | Sin POST y sin imagen | La falla también se reproduce en configuración dual channel. |
| Un módulo KLEVV junto con un módulo de otra marca en LGA1851 | Sin POST y sin imagen | La presencia de otro módulo compatible no evita la falla. |
| Actualización de BIOS | Sin cambios | Las versiones de BIOS disponibles durante las pruebas no resolvieron el problema. |

La repetición del síntoma al cambiar CPU, motherboard, chipset y cantidad de módulos, junto con las pruebas de control satisfactorias, permite clasificar el caso como una **incompatibilidad específica y reproducible entre las memorias KLEVV FIT V relevadas y la plataforma LGA1851 probada**.

No se determinó la causa eléctrica o de firmware exacta. Por lo tanto, esta entrada no atribuye el problema exclusivamente al módulo, al controlador de memoria del CPU o al BIOS del motherboard.

---

# Síntoma y criterio de identificación

El síntoma principal es:

- El equipo enciende, pero no completa el POST y no entrega imagen.

Debe sospecharse este caso cuando se cumplan todas las condiciones siguientes:

1. El equipo utiliza un procesador Intel Core Ultra para socket LGA1851.
2. Hay instalada al menos una memoria KLEVV FIT V de los códigos internos relevados.
3. El equipo completa el POST al reemplazar todas las memorias KLEVV por módulos DDR5 de otra marca ya validados.
4. Las memorias KLEVV funcionan al probarlas en una plataforma AMD AM5 o Intel LGA1700 compatible.

!!! warning "No confundir ausencia de imagen con una falla de video"

    El sistema no alcanza el POST. Cambiar el cable, el monitor o instalar una placa de video no corrige una falla producida durante la inicialización de la memoria.

---

# Acción requerida

## Para Ventas

- No ofrecer ni facturar los códigos internos **21783**, **21664** o **21782** junto con un CPU o motherboard para socket Intel LGA1851.
- Seleccionar memoria DDR5 de otra marca que haya sido validada con el modelo exacto de motherboard y CPU.
- Revisar esta entrada antes de proponer reemplazos de memoria para una plataforma LGA1851.

## Para Taller de Armado

- No iniciar armados LGA1851 con las memorias KLEVV FIT V relevadas.
- Si un equipo no completa el POST, retirar todos los módulos KLEVV y probar únicamente con una memoria de otra marca validada, instalada en el slot recomendado por el manual del motherboard.
- No mezclar una memoria KLEVV con otra marca como intento de solución: la falla se reproduce mientras haya un módulo KLEVV instalado.
- Registrar el modelo completo de cada módulo, CPU y motherboard, además de la versión de BIOS, si se realizan nuevas pruebas.

## Para RMA y Soporte

- Tratar el caso como incompatibilidad conocida antes de reemplazar CPU, motherboard, placa de video o fuente.
- Verificar por separado las memorias KLEVV en una plataforma AM5 o LGA1700 compatible y el equipo LGA1851 con otra memoria.
- Escalar cualquier combinación que complete el POST, indicando códigos de producto, versión de BIOS, slots utilizados y configuración aplicada, para revisar el alcance de esta entrada.

## Explicación sugerida para el cliente

> Esta memoria funciona correctamente en otras plataformas DDR5, pero en las configuraciones Intel LGA1851 probadas impide que el equipo complete el arranque inicial. La actualización de BIOS y las distintas configuraciones de módulos no resolvieron el comportamiento. Para asegurar el funcionamiento del equipo, corresponde utilizar otra memoria DDR5 validada para esta plataforma.

---

# Alcance y limitaciones

- La incompatibilidad está comprobada para los tres códigos internos, los tres procesadores y las tres motherboards detallados en esta entrada.
- El resultado no demuestra que todos los productos KLEVV ni todas las plataformas DDR5 sean incompatibles entre sí.
- Por prevención operativa, la restricción se aplica a estos modelos KLEVV FIT V con LGA1851 hasta que una nueva combinación o actualización sea probada y documentada como funcional.
- Un perfil XMP o EXPO indica parámetros de funcionamiento y overclocking; no garantiza por sí solo que un módulo complete el entrenamiento de memoria y el POST en cualquier motherboard.
- La inclusión de una familia de memorias en material comercial o en una lista QVL no reemplaza la validación del número de parte exacto con el modelo de motherboard, CPU y BIOS utilizados.
- Una futura revisión de hardware o firmware puede modificar el resultado y deberá probarse antes de retirar la restricción.

---

# Información del fabricante

La ficha oficial de KLEVV para la familia FIT V informa soporte para tecnologías de overclocking de Intel y AMD y publica las variantes de capacidad, velocidad y latencia. Sin embargo, la revisión oficial consultada limita expresamente su declaración de compatibilidad a procesadores **Intel de 14.ª generación y anteriores**; no declara compatibilidad específica con Intel Core Ultra para socket LGA1851.

KLEVV también señala que la familia fue sometida a pruebas para listas QVL de fabricantes de motherboards. Esto no permite asumir que todos los números de parte estén aprobados para cada motherboard LGA1851. Debe consultarse la QVL del modelo exacto y verificarse el número de parte impreso en el módulo o kit.

No se encontró, al momento de documentar el caso, una publicación oficial de KLEVV que describa esta falla de ausencia de POST en LGA1851 o una corrección aplicable.

---

# Referencias

- [KLEVV - FIT V DDR5](https://www.klevv.com/ken/products_details/memory/Klevv_FITV)
- [KLEVV - Ficha técnica oficial de FIT V DDR5](https://www.klevv.com/HyAdmin/upload/goodFile/KLEVV_Product%20Sheet_MEMORY_FIT%20V_v5_EN.pdf?2026010501=)
- [ASUS - Especificaciones de ROG Strix Z890-A Gaming WiFi](https://rog.asus.com/motherboards/rog-strix/rog-strix-z890-a-gaming-wifi/spec/)
- [ASUS - Manual de ROG Strix B860-A Gaming WiFi](https://dlcdnets.asus.com/pub/ASUS/mb/LGA1851/ROG_STRIX_B860-A_GAMING_WIFI/E25226_ROG_STRIX_B860-A_GAMING_WIFI_EM_WEB.pdf?model=ROG+STRIX+B860-A+GAMING+WIFI)
- [ASRock - Z890 Nova WiFi](https://www.asrock.com/mb/Intel/Z890%20Nova%20WiFi/index.asp)
- Pruebas internas con los componentes y configuraciones indicados.

Referencias consultadas el **2026-09-12**.

---

# Historial de cambios

| Versión | Fecha | Descripción |
|---------|-------|-------------|
| 1.1 | 2026-09-12 | Incorporación del vínculo al análisis técnico RMA-002. |
| 1.0 | 2026-09-12 | Creación del documento con la matriz de pruebas y la restricción preventiva para ventas, armados y soporte. |

---

# Caso RMA relacionado

- [RMA-002 - Sin POST con memorias KLEVV FIT V en Intel LGA1851](../03-Casos-RMA/RMA-002-Sin-POST-con-memorias-KLEVV-FIT-V-en-Intel-LGA1851.md): análisis técnico del incidente, hipótesis causales, metodología de confirmación y referencias oficiales.
