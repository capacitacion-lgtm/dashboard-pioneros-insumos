# Dashboard Pioneros AVIVA · Insumos y gestión comercial

Dashboard interno para seguimiento comercial y operativo de los Pioneros de **Walmart, Sam's Club y Super Bodega Aurrera (SBA)**. Integra metas, ventas, productividad, cobertura de tiendas, Mesa de Riesgos, reconocimientos y análisis ejecutivo.

**Sitio:** https://capacitacion-lgtm.github.io/dashboard-pioneros-insumos/  
**Repositorio:** https://github.com/capacitacion-lgtm/dashboard-pioneros-insumos  
**Última actualización de documentación:** 12 de octubre de 2026.

> Herramienta interna de seguimiento. Las proyecciones son estimaciones basadas en los cortes disponibles y no equivalen a ventas de cierre definitivas.

## Módulos actuales

- **Resumen operativo e insumos:** panorama general de tiendas, inventario, cobertura y pendientes.
- **Métricas comerciales:** venta acumulada, objetivos, ritmo, proyección, avance y desglose por vertical/tienda.
- **Seguimiento de productividad:** solicitudes, aprobaciones, desembolsos y objetivos operativos.
- **Mesa de Riesgos:** detección de promotores con proyección inferior al 80%, seguimiento y recuperación.
- **Resultados de recuperación:** comparativos entre proyección inicial y posterior, filtros por semana y fecha de corte, variación en puntos porcentuales y seguimiento por colaborador.
- **Reconocimientos:** mensajes personalizados que se pueden copiar y pegar en Slack.
- **Reporte ejecutivo mensual:** comparativo de casos inicialmente en riesgo frente a su resultado real al cierre, por formato.
- **AVIVA BRAIN / historial:** vistas de seguimiento incluidas en la interfaz.

## Metas: dos conceptos distintos

1. **Meta formal o global asignada:** objetivo oficial fijo. Para octubre de 2026 es **MX$ 4,690,000**. No se modifica automáticamente por vacantes, bajas ni redistribuciones.
2. **Meta general ajustada:** suma de objetivos operativos de tiendas; sí cambia cuando se agregan, retiran o modifican metas por cobertura. Después de retirar Jiutepec, la referencia operativa de octubre es **MX$ 5,460,000**.

Nunca sustituir la meta formal por la ajustada ni mezclar sus porcentajes de avance.

### Corte comercial validado

Al **11 de octubre de 2026, cierre del día**, el desglose validado de **39 tiendas con venta** suma **MX$ 2,349,100**:

| Vertical | Venta acumulada |
| --- | ---: |
| Walmart | MX$ 816,000 |
| Sam's | MX$ 330,100 |
| SBA | MX$ 1,203,000 |
| **Total** | **MX$ 2,349,100** |

El cálculo debe incluir todas las tiendas del desglose, incluida **0412 Periférico Mérida (MX$ 12,000)**. San Martín Texmelucan WM (0365) registra **MX$ 91,600** en este corte.

### Cobertura y vacantes

- **Jiutepec (0407):** Oscar Luna, baja el 12/10/2026; nunca inició operaciones en tienda. Se retira su meta operativa de **MX$ 102,000** de octubre, sin afectar la meta formal asignada. Mantener la tienda como vacante, sin venta ni solicitudes atribuidas.
- **Santín (0443):** Emmanuel, baja el 09/10/2026; seguimiento como vacante.
- Conservar los movimientos e historial comercial previos sin atribuir ventas futuras a personas que ya no están activas.

## Mesa de Riesgos: reglas de negocio

**Umbral:** una proyección de cierre **inferior al 80%** identifica un caso activo en riesgo. Alcanzar **80% o más** implica salir del listado de pendientes; alcanzar **100% o más** merece reconocimiento especial.

### Continuidad semanal

- Al iniciar una semana nueva, arrastrar únicamente a los promotores que **seguían por debajo del 80% al último corte de la semana anterior**.
- Si aún no existe un corte nuevo, mostrar explícitamente que se usa el **último corte disponible**; no presentar esos datos como ventas del nuevo día.
- Los recuperados de la semana anterior permanecen en su historial y reconocimientos, pero no en la lista de pendientes de la semana actual.
- **N.º de caídas:** episodios separados de entrada/reingreso a riesgo, después de haber salido. Permanecer en riesgo dos semanas seguidas **no** significa dos caídas.
- **Semanas consecutivas en riesgo:** número de semanas seguidas por debajo del 80%. Se reinicia tras recuperarse. Es una columna distinta de N.º de caídas.
- Registrar fechas de ingreso, mensaje y salida cuando estén disponibles. Preservar el historial de reincidencias.

**Nota técnica:** el conteo de semanas consecutivas depende de los cortes históricos registrados; se debe validar con semanas futuras y evitar deducir eventos que no existan en los datos.

### Resultados de recuperación

Se muestra la evolución por colaborador, kiosco y formato: proyección inicial, proyección actual, diferencia en **puntos porcentuales (pp)**, N.º de caída, semanas consecutivas y resultado.

El desglose semanal por **Walmart / Sam's / SBA** permite revisar comparados, mejoraron, recuperados del 80 al 99.9%, quienes proyectan 100% o más y quienes retrocedieron.

Distinguir siempre:
- **Mejoró, pero sigue debajo del 80%:** avance positivo; requiere acompañamiento, sin marcarlo como recuperado.
- **Recuperado entre 80% y 99.9%:** salió de riesgo; mensaje de impulso para sostener el ritmo y llegar al 100%.
- **Proyecta 100% o más:** felicitación especial por la recuperación y proyección de cumplimiento o superación.

Los botones **Copiar mensaje** preparan texto personalizado para Slack. **No envían mensajes automáticamente** ni confirman su entrega.

### Cierre mensual e historias de recuperación

Al finalizar el mes, comparar la **primera proyección en riesgo** con el **resultado real de cierre** y presentar por formato:
- Total de personas inicialmente en riesgo, sin duplicar reincidencias.
- Superaron el 100%, mejoraron, quedaron sin cambio o retrocedieron.
- Historias destacadas de quienes comenzaron proyectando un cierre bajo y terminaron cumpliendo o superando la meta.

Antes del último día del mes, el informe definitivo permanece **pendiente de cierre**. Las recuperaciones semanales y proyecciones no deben presentarse como resultados reales finales.

## Datos y persistencia

La aplicación se sirve desde GitHub Pages y contiene lógica del dashboard en `index.html`. Parte del estado de métricas, seguimientos y eventos de riesgo se conserva en **localStorage del navegador**, separado por mes. Esto implica que:

- Los datos guardados localmente pueden variar entre navegadores, equipos o perfiles.
- Publicar cambios en GitHub **no sincroniza automáticamente** esos registros locales.
- Los cortes incorporados directamente en el código y los registros guardados en el navegador deben distinguirse claramente.
- Para un historial auditable compartido, queda pendiente una fuente de datos centralizada y persistente.

## Estado y próximos controles de calidad

- [x] Metas formal y ajustada diferenciadas.
- [x] Corte comercial del 11/oct incorporado y total corregido.
- [x] Jiutepec excluido de la meta operativa.
- [x] Seguimiento de Mesa de Riesgos y filtros semanales.
- [x] Tabla de resultados por formato y mensajes de reconocimiento por nivel.
- [x] Columna de semanas consecutivas separada de caídas.
- [x] Estructura del reporte ejecutivo de cierre mensual.
- [ ] Validar con cortes futuros el arrastre semanal, reincidencias y semanas consecutivas.
- [ ] Verificar consistencia de datos entre dispositivos y considerar persistencia centralizada.
- [ ] Confirmar al cierre del mes los resultados reales e historias de éxito.
- [ ] Validar la visualización pública tras cada despliegue.

## Desarrollo y publicación

La rama `main` alimenta el sitio de GitHub Pages. Los cambios pueden tardar unos minutos en publicarse. Para revisar una actualización, abrir el sitio y, si es necesario, forzar recarga del navegador.

No incluir en el repositorio datos sensibles, credenciales o tokens de Slack.
