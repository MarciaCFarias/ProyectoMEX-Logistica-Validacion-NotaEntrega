# 📄 Mapeo de Procesos – Validación de Nota de Entrega

## Diagrama de Flujo – Visión Macro del Proceso

<img width="1054" height="429" alt="image" src="https://github.com/user-attachments/assets/6b413036-0407-4c1e-8cd9-d33ab1bdc3f6" />


## 1 - Flujo TO BE

1. **Capturar Entregas para Validación**
   - Acceder a SharePoint y abrir el archivo del control.
   - Filtrar registros de acuerdo con la columna.
   - Capturar solo números de entrega válidos; si no hay registros, generar LOG y finalizar.

2. **Acceder a Fourkites**
   - Iniciar sesión con las credenciales del robot.
   - Acceder a la otra pestaña y buscar la entrega.
   - Si no se encuentra, generar LOG y continuar con la siguiente.

3. **Verificar Documento de Entrega**
   - Expandir detalles y confirmar si el número de entrega corresponde.
   - Si hay múltiples documentos o secciones, validar cada una.
   - Si no existe documento, esperar hasta la segunda ejecución antes de generar la información.

4. **Descarga y Análisis del Documento**
   - Descargar todos los archivos relacionados.
   - Procesar con IA para verificar que el layout y la información obligatoria estén presentes.
   - Validar campos “NOMBRE”, “APELLIDO”, “PUESTO”, “FIRMA”, “FECHA” y “HORA”.
   - Actualizar las columnas.

5. **Captura de Datos**
   - Extraer datos del archivo para los campos definidos.

6. **Actualización en SharePoint**
   - Ingresar resultados en las columnas correspondientes en Excel.
   - Guardar el archivo en la misma ubicación y con el mismo nombre.

7. **Generación de Reportes**
   - Crear Reporte Sintético (datos agregados de ejecución) y Analítico (detalle por entrega).
   - Guardar en SharePoint, organizando por año/mes.

8. **Envío de Notificaciones**
   - Enviar correo a la lista definida con resumen de la ejecución y enlaces a los reportes.

---

## 2 - Mejoras Implementadas en el Proceso

- **Automatización RPA** para eliminar la necesidad de búsquedas y validaciones manuales.
- **Integración con IA** para reconocimiento y validación de documentos digitalizados, reduciendo el error humano.
- **Control de intentos** para entregas sin documento, con verificación en la siguiente ejecución antes de actualizar las informaciones.
- **Centralización de información** en SharePoint, garantizando fácil acceso y trazabilidad.
- **Estandarización de reportes** Sintético y Analítico para seguimiento y auditoría.
- **Generación automática de LOGs** para todas las excepciones, mejorando trazabilidad y soporte.

---

## 3 - Tratamiento en Caso de Excepciones

- **Archivo de SharePoint no disponible**: generar LOG, no continuar a Fourkites.
- **Entrega no encontrada en Fourkites**: registrar en LOG y pasar a la siguiente.
- **Documento ausente**: verificar nuevamente en la siguiente ejecución.
- **Layout o campos diferentes**: generar LOG y marcar como “excepciones”.
- **Error de acceso** (contraseña expirada o cambios en el sistema): notificar a soporte y registrar LOG.
- **Falla en la actualización de Excel**: intentar hasta 3 veces; si persiste, registrar LOG.

---

## 4 - KPI (Indicadores de Desempeño)

- **Tasa de Procesamiento** = (Entregas procesadas / Entregas previstas) × 100.
- **% de Notas cargadas** = (Entregas con documento / Total de entregas) × 100.
- **% de Notas correctas** = (Documentos validados / Documentos cargados) × 100.
- **Tiempo Medio de Procesamiento** por entrega.
- **Tasa de Errores** = (Excepciones registradas / Total de procesamientos) × 100.
- **Tiempo de Resolución de Excepciones**.

---

## 5 - Observaciones o Destacados

- La calidad de los documentos impacta directamente el éxito de la validación por IA.
- Cambios en el layout de los archivos o en la plataforma Fourkites requieren ajuste inmediato en el robot.
- El robot no maneja devoluciones por correo ni validaciones manuales; estas quedan a cargo del equipo operativo.
- La ejecución semanal está programada.
- Es importante mantener credenciales y accesos siempre actualizados para evitar fallos.

---
🚨 Aviso Importante: Todas as informações contidas nos projetos deste repositório são fictícias e foram criadas exclusivamente para fins de demonstração ou simulação. Nenhuma das empresas, organizações, pessoas ou eventos mencionados nos arquivos deste projeto são reais ou exigem dados autênticos. Quaisquer semelhanças com nomes, lugares ou entidades existentes são puramente coincidentes. Este repositório foi desenvolvido com o objetivo de demonstrar habilidades técnicas, práticas de projetos e experiência em desenvolvimento e mapeamento de sistemas. Todas as referências a empresas, produtos, serviços ou indivíduos são meramente fictícias e não devem ser interpretadas como representações precisas da realidade. Fique à vontade para explorar os projetos disponíveis aqui, mas lembre-se sempre de que todas as informações são fictícias e não devem ser utilizadas para qualquer fim além de fins educacionais, de demonstração ou simulação. Obrigada pela compreensão!
