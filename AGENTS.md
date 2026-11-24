# .github — Guía operativa

> Idioma: el equipo trabaja en **español**.
> ⚠️ **Las reglas de la casa viven en `app-v2/.ai/nucleo/NUCLEO.md`** y se escriben acá
> automáticamente. **No las edites en este archivo** — un gate de la CI lo caza. Lo de *este* repo
> sí se edita acá.

---

<!-- NUCLEO-AVEONLINE:INICIO — generado por `php spark harness:nucleo`. No editar acá. -->

## Reglas de AveOnline (núcleo compartido)

Valen en **todos** los repos, sin importar el stack. Lo propio de este repo va fuera de este bloque.
Este bloque es compacto a propósito: sus reglas son de cumplimiento obligatorio; el **detalle** (por
qué, casos, tablas completas) está en `app-v2/.ai/nucleo/detalle/`. Fuera de app-v2 se lee con
`gh api repos/Development-Aveonline/app-v2/contents/.ai/nucleo/detalle/<archivo> -H "Accept: application/vnd.github.raw"`.
Léelo **cuando la tarea toque esa sección**, no por rutina. **Si no puedes leerlo** (sin `gh`
autenticado o sin acceso a app-v2, que es privado): las reglas de este bloque se cumplen igual,
porque el detalle explica y no agrega obligaciones; dilo en tu reporte y, si la tarea es de riesgo
alto (secciones 2 y 5), pide el detalle a una persona del equipo antes de seguir. No lo reconstruyas de memoria.

### 0. La regla de oro — detalle: `00-regla-de-oro.md`

- **Si algo no está en el código o en el harness, NO lo asumas: verifícalo o pregúntalo.** Varias
  bases de datos son de producción y compartidas; asumir un esquema o una columna rompe cosas reales.
- **Inicio ágil:** acepta instrucciones breves; busca tú el issue de Linear, el proyecto, el SPEC y
  los archivos; lee solo lo necesario. Pregunta solo si falta una decisión que cambie la solución,
  con una opción propuesta. Si es verificable y cumple las puertas de seguridad, ejecuta.
- **Autoasistencia primero:** nunca le pidas a una persona lo que puedes resolver tú. Antes de pedirle
  un dato, una consulta, una verificación, una tarea o una decisión técnica a alguien, agota lo que
  alcanzas con tus herramientas: leer el código y los repos a los que tienes acceso, consultar datos,
  flujos y APIs en solo lectura, buscar en Linear, Drive, el SPEC y las investigaciones. Si aun así
  debes pedirlo, el mensaje dice qué intentaste, con qué herramienta y por qué no bastó. Pedir es
  legítimo solo para lo que únicamente una persona puede dar: una decisión de negocio, una
  autorización de gasto o de acceso, una credencial, o una acción que exige su identidad.
- **Comunicación breve:** avisa solo hallazgos, bloqueos, decisiones o tareas largas. Respuesta
  final de 2–4 líneas: resultado, verificación (categoría de la sección 4) y próximo paso o bloqueo.
- **Modelo:** el más capaz para lo complejo o de alto riesgo; uno económico para subtareas acotadas.
  No delegues por rutina; reutiliza el contexto ya leído y no repitas búsquedas sin motivo.
- **Memoria viva:** en el mismo turno registra toda corrección del usuario (supuesto corregido,
  decisión vigente, alcance, issue/PR): lo de la tarea en su issue/PR, lo estable en el SPEC o docs,
  lo que cambie una regla compartida en `.harness/mejoras/`. Actualiza en vez de duplicar. Nunca
  guardes secretos, datos personales, transcripciones ni suposiciones sin verificar.
- **Toda solicitud a terceros queda en Linear en el mismo turno** en que se entrega el texto: a quién
  (nombre de trabajo y organización o rol, nunca teléfono ni correo), qué, canal y estado
  (`redactado — envío sin confirmar`, `enviado`, `respondido`, `cerrado`). Un issue nuevo se crea
  **sin responsable**. Sin secretos ni datos de clientes.
- **Todo mensaje de trabajo enviado abre un seguimiento** hasta integrar la respuesta (canal, qué se
  espera, responsable, criterio de cierre). Una respuesta parcial no lo cierra. Nunca prometas un
  seguimiento que no configuraste y comprobaste; no envíes recordatorios sin autorización.
- **Recuperación verificable de aprendizajes y QA.** Al iniciar, retomar o compactar, recupera SPEC,
  decisiones vigentes, bitácora y evidencia. Al rediseñar, contrasta código y recorridos actuales
  antes de declarar paridad. Al cerrar, concilia pedidos, cambios, pruebas y bloqueos. Vincula la
  evidencia a versión, corte y población; prueba fallos esperados e invalida resultados obsoletos.
  Los hooks solo recuerdan esto; no prueban cumplimiento. No afirmes propagación a otros repos sin
  versión, PR y prueba. Distingue DEMO, local, QA y producción.

### 1. Secretos

- **NUNCA commitear `.env`** ni archivos con credenciales, llaves o tokens.
- **No reproducir secretos** en respuestas, commits, logs ni capturas, ni siquiera parcialmente.
- Si un secreto quedó expuesto, **dilo de inmediato**. Rotarlo es del dueño; callarlo no es opción.

### 2. Proyecto y SPEC — detalle: `02-proyecto-y-spec.md`

- **Antes de escribir código se declara a qué proyecto pertenece el trabajo** (un arreglo reactivo
  también). Búscalo tú; si no hay correspondencia clara, registra el issue en Triage con evidencia.
- **2.1 · Contexto del Brain** (recomendado): trae el estado vivo (`brain_load_context`) antes de
  declarar el proyecto; si no responde, sigue con el catálogo del repo **y dilo explícito**.
- **2.2 · Todo proyecto apunta a un SPEC en `app-v2/proyectos/<nodo>/<proyecto>/spec.md`** (con su
  `bitacora.md`), sea cual sea el repo del código. Guía: `app-v2/proyectos/_plantilla/GUIA-SPEC.md`.
- **2.3 · El SPEC se publica y revisa antes del código productivo.** Antes de editar código de producto, el SPEC debe:
  - estar validado contra la guía, sin placeholders ni secciones obligatorias vacías;
  - tener un PR propio en `app-v2`, separado del PR de implementación, y estar enlazado desde la
    incidencia canónica de Linear;
  - reconciliar trabajo previo en Linear, Azure, GitHub y producción, declarando solo la brecha residual;
  - estar revisado antes de empezar implementación cuando el riesgo sea alto o crítico.
- Un merge del SPEC no autoriza un despliegue. Única excepción al orden: incidente productivo activo
  (incidencia, alcance provisional y rollback primero; el SPEC se publica en el mismo ciclo).

### 3. Commits

- **En español**, con prefijo `Feat:`, `Fix:`, `Docs:` o `Chore:`. Sin token de tarea. Explica el **por qué**.
- **Doble co-autor**: el Brain y el modelo que **de verdad** corrió la sesión (no un nombre fijo),
  con el correo **de su proveedor**; si el proveedor no publica uno, `noreply@aveonline.co`. Nunca
  atribuyas un modelo a un proveedor que no es el suyo. Un commit que hace un script, sin modelo,
  lleva solo al Brain.
  ```
  Co-authored-by: Aveonline Brain <brain@aveonline.co>
  Co-authored-by: <modelo real de la sesión> <correo noreply de su proveedor>
  # ejemplo, sesión de un modelo de Anthropic: Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
  ```
- **Nada de `git add -A` a ciegas.** Se agrega solo lo cambiado a propósito.

### 4. Reporte de avance — detalle: `04-reporte-de-avance.md`

- **Prohibido "listo", "funcional" o "asegurado" a secas.** La etapa se declara como **CÓDIGO
  LISTO** (pasa lint y pruebas) · **DESPLEGADO** (en producción, deploy verificado) · **VERIFICADO
  END-TO-END** (alguien con el rol real lo usó desde la interfaz real).
- Y aparte, el **nivel de evidencia**: **N1** demo · **N2** datos reales que persisten y se
  **releen del backend** con una consulta reproducible · **N3** persona con el rol real firmó.
  Declara siempre el nivel y **qué no se probó**, y por qué.
- Antes de VERIFICADO END-TO-END confirma: (a) el frontend invoca el endpoint; (b) la migración
  corrió en el ambiente real; (c) sesión, rol y permiso confirmados. Esa etiqueta se deriva de una
  prueba por rol que pasó; no se escribe a mano. Un traspaso entre roles (A actúa → B lo ve) se prueba completo.
- **El verde del CI no es evidencia** si el gate nunca se vio fallar cuando debía.

### 5. Seguridad y QA — detalle: `05-seguridad-y-qa.md`

1. **Sin migración versionada no hay DDL**, ni con confirmación del usuario.
2. **Sin blindaje de tests no se toca facturación, cartera, billetera ni transportadoras.**
3. **Mapa de dependencias (con herramienta) antes de tocar un módulo core.** Si el cambio toca una tabla,
   un endpoint o una variable que otro repo usa, lee antes la ficha del repo: `gh api
   repos/Development-Aveonline/app-v2/contents/.ai/grafos/impacto/<repo>.md -H "Accept: application/vnd.github.raw"`.
4. **Gates de CI/CD bloqueantes**, sin excepción "por esta vez".
5. **Human-in-the-loop** en módulos core y prueba de rollback antes de un cambio de esquema en producción.
6. **Un mismo hecho de negocio no tiene valores distintos en tablas distintas**: todo dato replicado
   tiene prueba de reconciliación.
7. **Errores nunca silenciosos:** prohibido un `catch` vacío o `return null` mudo en una escritura de red;
   el QA de navegador falla ante `pageerror` o `unhandledrejection`. Si la base rechaza una escritura
   dentro de una transacción, la respuesta nunca es de éxito: se verifica que la capa de datos lance
   el error o se revisa el estado de la transacción y las filas afectadas antes de confirmar.
8. **Toda escritura con identidad se relee** (autor y fecha, con el usuario del token de sesión,
   nunca del cuerpo de la petición). Un `200` no es evidencia.
9. **Un gate no se acepta sin su rojo, y el rojo queda registrado** (mutación inyectada, prueba de
   que quedó aplicada, código de salida y corrida). Una mutación sin diff no es un resultado.
10. **Un hallazgo de un agente de IA es un candidato:** lleva "reproducido en vivo: sí/no"; solo "sí"
    cierra. Toda regla por patrones declara cómo se midió su cobertura forzando la condición en vivo.

### 6. Dónde vive cada cosa

- Investigación y el "por qué" → `Brain_Avemetrics_Aveonline`. Estado operativo → junto a su código.
- Toda tarea = issue en el repo real, por fase lógica, sin fechas. Antes de abrirla, verifica que no exista.

### 7. Documentación

Se actualiza **en el mismo flujo** que el cambio (el changelog del repo, en el formato que ese repo
declare; doc del área; estado del proyecto).
Un doc **no puede afirmar cifras o estados que el código desmiente**; si es verificable, que lo vigile un gate.

### 8. Interfaz y datos — detalle: `08-interfaz-y-datos.md`

- Estándar único: `ESTANDARES-AVEONLINE.md`. **Tokens de [AveDS](https://github.com/Development-Aveonline/AveDS)**,
  nada hardcodeado; si falta un token, no se inventa: se toma de AveDS.
- Tablas ordenables, con filtro por columna, TOTAL real, export y drill. KPIs que abren su detalle,
  comparan con el período anterior y traen semáforo. Período por defecto = mes en curso.
- Todo KPI, alerta o elemento de gráfica abre el conjunto exacto que lo sustenta, con «Volver» que
  conserva el contexto. Filtro activo visible y removible. Antirregresión al portar una pantalla.
- **Ningún dato de demostración es presentable como real**; un dato de ejemplo se marca junto al número.
- Lo que la interfaz ofrece coincide con la matriz de permisos del rol.

### 9. Mejoras al harness — detalle: `09-mejoras-al-harness.md`

**El núcleo no se edita donde lo lees** (se regenera y el gate lo marca en rojo). Para proponer un
cambio: `.harness/mejoras/mejora_harness_AAAAMMDD.md` en el repo donde surgió, con qué regla, qué
pasó (caso real), qué propones y qué se rompe. Proponer no es aplicar.

### 10. Paridad `CLAUDE.md` / `AGENTS.md`

Los dos se generan del mismo fuente con texto idéntico; por eso este núcleo no nombra ninguna
herramienta. Lo específico de una herramienta va en la parte local de cada archivo.

### 11. Superficie de integración — detalle: `11-superficie-de-integracion.md`

- **Toda funcionalidad o servicio nuevo declara su superficie de integración antes del código**, en
  el SPEC: **portal de desarrolladores, API (contrato OpenAPI), MCP y SDK**, cada una como *aplica*
  o *no aplica con su razón*. Una fila en blanco es un hueco, no un «no hacía falta».
- **Lo que aplica es criterio de aceptación.** El trabajo no se cierra ni se declara VERIFICADO
  END-TO-END hasta que la capacidad quede incluida en cada superficie marcada, con evidencia (PR,
  versión o URL). Si la superficie todavía no puede recibirla, queda su issue enlazado en el
  proyecto dueño y el reporte lo dice como pendiente; nunca se omite.
- **Por defecto aplica** a todo lo que un cliente, un integrador o un agente externo pueda usar. Lo
  interno (back office, operación, harness) se marca *no aplica* y no se publica.
- **El core financiero es la excepción.** Facturación, recibos de caja, cartera, notas crédito y
  débito, recaudos, compras, egresos y billetera no se exponen en ninguna superficie (MCP, SDK,
  portal de desarrolladores ni API pública) sin aprobación explícita del CTO. El SPEC marca cada
  fila «no aplica: core financiero, requiere aprobación del CTO». Si se aprueba, pasa a «aplica» y
  la evidencia enlaza esa aprobación. Ningún agente ni PR la da por supuesta. Las reglas y procesos
  internos que fijan precios (tarifas, negociaciones, anexos, guías para no cobrar) son internos:
  no aplican en ninguna superficie. Ante la duda, se trata como financiero.
- **Las superficies anuncian solo capacidades verificadas** en el ambiente que declaran. El proyecto
  dueño de cada superficie decide cómo y cuándo se expone; no decide si se registra.

<!-- NUCLEO-AVEONLINE:FIN -->

---

# Lo que es cierto SOLO de este repo

> **Por escribir.** Este arnés base lo propuso el empuje del núcleo de app-v2 sin leer el
> repo: no afirma nada de él. Esta sección la escribe quien conoce el sistema. Es la más valiosa
> del harness —cada cosa que ya mordió a alguien, con el síntoma y la causa real— y no se puede
> deducir leyendo el código.

## Qué es y de qué depende

## Base de datos

## Deploy

## Cómo se prueba

## Convenciones propias

## Trampas conocidas
