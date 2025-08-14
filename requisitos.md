# Documento de Requisitos del Proceso – Validación de Nota de Entrega (ePOD Fourkites)

## 1 - Reglas de Negocio

- **Programación de ejecución**: el robot se ejecuta semanalmente los domingos a las 20h (hora CDMX) y debe finalizar antes de las 00h.
- **Fuente de datos**: el archivo “Seguimiento Unidades T&T Ene-Dic <AA>” debe estar disponible en la carpeta especificada de SharePoint antes de la ejecución, con el mismo nombre y estructura.
- **Filtrado inicial**: procesar únicamente entregas con el campo “ePOD Cargado SI/NO” vacío y con número de entrega válido (numérico).
- **Consulta en Fourkites**: acceder con credenciales del robot, buscar entrega en “Shipments” y validar documentos asociados.
- **Regla de documento ausente**: si no se encuentra documento en la primera ejecución, reintentar en la siguiente semana; si persiste, marcar como “no cargado”.
- **Validación documental**: documento debe cumplir con layout predefinido y contener campos obligatorios del sello: “NOMBRE”, “APELLIDO”, “PUESTO”, “FIRMA”, “FECHA” y “HORA”.
- **Procesamiento por IA**: utilizar tecnología de reconocimiento para verificar contenido y legibilidad del documento.
- **Registro y trazabilidad**: generar LOGs en todas las etapas de excepción o error.
- **Actualización de resultados**: escribir en el archivo de SharePoint sin alterar el nombre ni la ubicación del archivo.
- **Resguardo de datos**: los archivos descargados se eliminan al finalizar la ejecución.
- **Generación de reportes**: producir Reporte Sintético y Reporte Analítico, organizados por año y mes en SharePoint.
- **Comunicación**: envío de notificaciones por correo electrónico a lista predefinida con el resumen del procesamiento.

---

## 2 - Validaciones Necesarias

- **Disponibilidad de SharePoint** y acceso al archivo antes de iniciar el procesamiento.
- **Integridad del archivo de origen**: verificar que contenga datos y que el formato sea conforme a la especificación.
- **Formato y validez de números de entrega**: solo procesar valores numéricos válidos.
- **Acceso a Fourkites**: credenciales vigentes y acceso sin bloqueos.
- **Correspondencia de la entrega** en Fourkites con la registrada en SharePoint.
- **Existencia y legibilidad del documento**: validar que el archivo descargado sea legible, no esté truncado y contenga todos los campos requeridos.
- **Cumplimiento del layout** predefinido, incluyendo presencia y llenado del sello.
- **Verificación por IA** de coincidencia de número de entrega y datos del sello.
- **Actualización correcta en Excel**: registrar resultados “SÍ” o “NO” en las columnas “ePOD Cargado” y “ePOD Correcto/Incorrecto”.
- **Generación correcta de reportes** con datos consistentes y completos.
- **Envío de notificaciones** con toda la información requerida.

---

## 3 - Salidas Esperadas

- **Archivo de seguimiento actualizado** en SharePoint con las columnas:
  - “ePOD Cargado SI/NO”
  - “ePOD Correcto/Incorrecto”
  - “Nombre Firma ePOD del sello”
  - “Fecha ePOD del sello”
  - “Hora ePOD del sello”
- **Reporte Sintético** con:
  - Fecha y hora de inicio y fin del procesamiento
  - Total de horas de ejecución
  - Cantidad de entregas procesadas
- **Reporte Analítico** con:
  - Número de entrega
  - Estado “ePOD Cargado” y “ePOD Correcto/Incorrecto”
  - Estado de procesamiento
  - Observaciones y detalles de LOG
- **Notificación por correo electrónico** con resumen de la ejecución y enlaces a los reportes.
- **LOGs completos** para auditoría y trazabilidad.

---

## 4 - Criterios de Éxito

- 100% de entregas disponibles en el archivo de SharePoint procesadas según reglas.
- Disponibilidad total de sistemas y accesos (SharePoint y Fourkites) durante la ejecución.
- Documentos validados cumpliendo criterios de layout y datos obligatorios.
- Tasa mínima de errores de validación y excepciones.
- Actualización correcta y sin fallos del archivo de seguimiento en SharePoint.
- Reportes generados y guardados correctamente en la ubicación prevista.
- Notificaciones enviadas con información exacta y completa.
- Cumplimiento del tiempo de ejecución (antes de la medianoche del día programado).


