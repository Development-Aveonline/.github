<!--
  Plantilla de PR de AveOnline. Contrato: equipo/contrato-desarrollo/CONTRATO-SISTEMA-DE-DESARROLLO.md

  Se llena TACHANDO lo que no aplica, no borrándolo. Una casilla que desaparece no
  deja rastro de que se pensó; una tachada dice "lo miré y no aplica", que es
  información distinta y más útil para quien revisa.
-->

## Qué cambia y por qué

<!-- El POR QUÉ, no solo el qué. Un PR que dice "arregla el bug" obliga a alguien,
     meses después, a reconstruir el razonamiento desde el diff. -->

**Proyecto y tarea:** `[PROYECTO#Tn]`

## Cómo se verificó

<!-- Qué se corrió, con qué datos, y qué devolvió. "Probé local" no es verificación. -->

**Estado:** ☐ CÓDIGO LISTO ☐ DESPLEGADO ☐ VERIFICADO END-TO-END

---

## Datos y consultas

- [ ] No agrega SQL construido pegando `$_GET` / `$_POST` / `$_REQUEST` — **R-1**
- [ ] Toda lectura nueva lleva `WHERE`, `LIMIT` o los dos — **R-2**
- [ ] No agrega `SELECT *`; las columnas van nombradas
- [ ] No introduce una consulta dentro de un bucle (N+1)
- [ ] `EXPLAIN` adjunto si la consulta corre en una ruta de uso frecuente
- [ ] La migración es compatible hacia atrás (`expand → migrate → contract`) — **R-3**
- [ ] Si toca una de las 180 tablas compartidas: **está dicho quién es el dueño**

## Salidas a terceros

- [ ] Toda llamada externa nueva declara timeout de conexión y total — **R-4**
- [ ] No hay una llamada externa dentro de una transacción abierta
- [ ] Si reintenta, la operación es idempotente — **R-5**
- [ ] Si crea algo con valor (guía, pago, recaudo), acepta `Idempotency-Key`

## Tiempo de respuesta

- [ ] Lo que tarda no vive dentro de la petición web — **R-6**
- [ ] Los listados paginan
- [ ] Los reportes analíticos no pegan contra el MySQL operacional

## Rastro

- [ ] Propaga `traceparent` — **R-7**
- [ ] Los logs son estructurados y traen `duration_ms`
- [ ] **No se registra** ninguna contraseña, token, llave, tarjeta ni documento

## Seguridad y reversa

- [ ] No versiona ningún `.env`, llave ni token
- [ ] Los permisos por rol se respetan
- [ ] Hay cómo revertir: rollback o feature flag

---

## Riesgo y qué se rompe si sale mal

<!-- Si la respuesta es "nada", escribirlo. También informa. -->

## Lo que NO se verificó

<!-- Obligatorio. Una superficie que no se pudo probar se dice, no se omite.
     Es la regla 4 del núcleo: nunca "listo" sin decir qué quedó sin verificar. -->
