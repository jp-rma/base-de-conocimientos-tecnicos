# PROC-001 - Uso de Debloat by JP en Windows

| Campo | Valor |
|-------|-------|
| **Código** | PROC-001 |
| **Categoría** | Procedimiento |
| **Área** | Taller de Armado, RMA y Soporte Técnico |
| **Estado** | <span class="kb-status kb-status--ok">Vigente</span> |
| **Versión** | 1.1 |
| **Fecha de creación** | 2026-09-12 |
| **Última actualización** | 2026-09-12 |

---

# Objetivo

Estandarizar el uso de **[Debloat by JP](https://github.com/jp-rma/Debloat-by-JP)** para retirar aplicaciones preinstaladas que no sean necesarias y aplicar únicamente los ajustes aprobados para una instalación de Windows, sin comprometer las funciones requeridas por el usuario ni la posibilidad de diagnosticar el equipo.

---

# Alcance

Este procedimiento se aplica a equipos con Windows compatibles con la versión aprobada de Debloat by JP que sean preparados o revisados por Taller de Armado, RMA o Soporte Técnico.

No se debe aplicar de forma automática en equipos administrados por una organización, unidos a un dominio o sujetos a políticas corporativas. Tampoco corresponde utilizarlo cuando el cliente necesite aplicaciones o componentes que la configuración seleccionada pueda retirar o modificar.

---

# Requisitos previos

Antes de comenzar:

- Confirmar que Windows haya finalizado la instalación y pueda iniciar sesión con normalidad.
- Completar las actualizaciones y los controladores necesarios para poder distinguir una falla previa de un efecto posterior al procedimiento.
- Verificar los requisitos particulares del usuario, especialmente sincronización, Microsoft Store, Xbox, impresión, cámara, Bluetooth, biometría y funciones corporativas.
- Cerrar aplicaciones y guardar cualquier trabajo abierto.
- Utilizar exclusivamente una copia de Debloat by JP obtenida del canal aprobado y comprobar su versión.
- Contar con privilegios de administrador.
- Confirmar que la protección del sistema de Windows pueda utilizarse. Debloat by JP genera automáticamente el punto de restauración requerido, por lo que no es necesario crear otro de forma manual antes de ejecutarlo.

---

# Procedimiento

## 1. Registrar el estado inicial

1. Anotar la edición y versión de Windows.
2. Confirmar que no existan fallas pendientes en el Administrador de dispositivos.
3. Probar las funciones esenciales para el destino del equipo.
4. Registrar cualquier anomalía detectada antes de ejecutar la herramienta.

## 2. Iniciar Debloat by JP

1. Ejecutar la versión aprobada de **Debloat by JP** con privilegios de administrador.
2. Leer las advertencias y comprobar que la herramienta identifique correctamente el entorno.
3. Confirmar que la generación automática del punto de restauración finalice correctamente antes de permitir que continúen los demás cambios.
4. Si la herramienta informa una incompatibilidad, un error al crear el punto de restauración, un error de preparación o una versión de Windows no contemplada, cancelar el procedimiento y registrar el resultado.

## 3. Revisar los cambios

1. Revisar cada opción antes de seleccionarla.
2. Aplicar solamente el perfil o las acciones autorizadas para el tipo de equipo.
3. Conservar cualquier aplicación, servicio o función requerida por el usuario.
4. No seleccionar opciones adicionales con el único objetivo de reducir la cantidad de procesos o el consumo de memoria.
5. Guardar o registrar el resumen de acciones cuando la versión utilizada lo permita.

Las opciones disponibles pueden cambiar entre versiones. Este procedimiento no reemplaza las advertencias ni la descripción mostrada por la propia herramienta.

## 4. Ejecutar y reiniciar

1. Confirmar que la selección coincida con lo planificado.
2. Iniciar el proceso y no apagar ni reiniciar el equipo durante la ejecución.
3. Registrar cualquier advertencia o acción que no pueda completarse.
4. Cuando la herramienta finalice, reiniciar Windows aunque no lo solicite expresamente.

## 5. Validar el equipo

Después del reinicio, comprobar como mínimo:

| Control | Resultado esperado |
|---------|--------------------|
| Inicio de sesión y escritorio | Windows inicia sin errores ni demoras anormales. |
| Red | Ethernet y Wi-Fi funcionan cuando están disponibles. |
| Administrador de dispositivos | No aparecen nuevos dispositivos con error. |
| Windows Update | Puede buscar actualizaciones sin errores. |
| Microsoft Store | Abre y descarga aplicaciones si el usuario la requiere. |
| Audio, Bluetooth y cámara | Funcionan cuando el equipo dispone de ellos. |
| Impresión y biometría | Funcionan cuando forman parte del uso previsto. |
| Aplicaciones requeridas | Continúan instaladas y pueden iniciarse. |

Si una validación falla, no entregar el equipo hasta determinar si el problema existía previamente, revertir el cambio correspondiente o recuperar el sistema.

## 6. Registrar el resultado

Documentar:

- Fecha de ejecución.
- Versión de Debloat by JP.
- Edición y versión de Windows.
- Perfil u opciones aplicadas.
- Advertencias o errores informados.
- Resultado de las verificaciones posteriores.
- Acción de reversión realizada, si correspondiera.

---

# Puntos críticos

- Un proceso de debloat modifica la instalación de Windows y puede afectar dependencias que no resulten evidentes durante la selección.
- No se debe asumir que una aplicación es innecesaria solo porque el usuario no la abre directamente; otras funciones pueden depender de ella.
- Debloat by JP no reemplaza el diagnóstico de fallas, la instalación correcta de controladores ni la aplicación de actualizaciones.
- La configuración más agresiva no es necesariamente la más adecuada. Debe priorizarse la estabilidad y el uso previsto del equipo.
- No se deben utilizar versiones modificadas por terceros ni copias cuya procedencia no pueda verificarse.

---

# Buenas prácticas

- Ejecutar el procedimiento sobre una instalación estable y antes de cargar información personal del usuario, siempre que sea posible.
- Aplicar el conjunto mínimo de cambios necesario.
- Realizar una sola intervención controlada antes de validar, para facilitar la identificación de problemas.
- Mantener disponible el instalador o mecanismo de recuperación de las aplicaciones requeridas.
- Volver a validar el procedimiento cuando cambie de forma relevante Windows o Debloat by JP.

---

# Desvíos de procedimiento

Se consideran desvíos:

- Ejecutar una versión no aprobada o de origen desconocido.
- Aplicar opciones sin revisar su impacto.
- Omitir la identificación de las necesidades del usuario.
- Ejecutar la herramienta para intentar ocultar una falla sin diagnosticar.
- Entregar el equipo sin reiniciar y completar las verificaciones posteriores.
- No registrar la versión ni las acciones aplicadas.

---

# Referencias

- [Repositorio oficial de Debloat by JP](https://github.com/jp-rma/Debloat-by-JP)
- Documentación y advertencias incluidas en la versión aprobada de Debloat by JP.
- [Microsoft - Opciones de recuperación en Windows](https://support.microsoft.com/es-es/windows/experience/backup-recovery/recovery-options-in-windows)
- [Microsoft - Protección del sistema y creación de puntos de restauración](https://support.microsoft.com/es-es/windows/experience/backup-recovery/system-protection)

---

# Historial de cambios

| Versión | Fecha | Descripción |
|---------|-------|-------------|
| 1.1 | 2026-09-12 | Incorporación del repositorio oficial y aclaración sobre la generación automática del punto de restauración. |
| 1.0 | 2026-09-12 | Creación del procedimiento para el uso controlado de Debloat by JP. |
