# Cómo se contribuye acá

<!-- PLANTILLA. Al copiarla a un repo se reemplaza TODO lo que va entre << >>.
     Un CONTRIBUTING con marcadores sin resolver es peor que no tenerlo: dice que
     nadie lo leyó desde que se copió. -->

Las reglas de la casa están en `CLAUDE.md` y `AGENTS.md` — los dos dicen lo mismo y se generan de
la misma fuente. **Acá va solo lo que es cierto de este repo.**

## Qué es este repo

<<Una frase. Qué hace, quién lo usa, qué se rompe si se cae.>>

**Dueño técnico:** <<nombre>> · **Dueño de negocio:** <<área>> · **Tier:** <<0–4>>

## Antes de escribir código

Todo trabajo pertenece a un proyecto y a una tarea. El commit lleva su token entre corchetes:
`[PROYECTO#Tn]`. **Sin el token, el avance no existe** para el tablero ni para el histórico.

## Cómo se corre

```bash
<<instalación>>
<<cómo levantarlo>>
<<cómo correr las pruebas>>
```

## Lo que la CI verifica

<<Listar los gates de .github/workflows/ y qué hace fallar cada uno.>>

**Un gate rojo no se salta.** Si está mal el gate, se corrige el gate — no se pasa por encima.

## Lo que NO se toca sin hablar

<<Módulos de facturación, cartera, billetera, transportadoras. Y en este repo, además: ...>>

Regla 5.2 del núcleo: sin blindaje de tests no se tocan. Y sin migración versionada no hay DDL.

## Ramas y despliegue

<<Rama por defecto. Convención de nombres. Y sobre todo: QUÉ DESPLIEGA. En varios repos de
AveOnline un merge a la rama principal ES un despliegue a producción — si acá pasa eso, decirlo
en mayúsculas, porque es lo que más caro cuesta averiguar tarde.>>

## Antes de abrir el PR

La plantilla (`.github/pull_request_template.md`) tiene la lista completa. Los cuatro que más se
olvidan:

1. **Timeout** en toda llamada nueva a un tercero.
2. **`WHERE` o `LIMIT`** en toda lectura nueva.
3. **Idempotencia** si la operación crea algo con valor.
4. **Qué NO se verificó** — se dice, no se omite.

## Si una regla estorba

No se discute en el PR ni se ignora: se deja un archivo en `.harness/mejoras/` con la regla, el caso
real, la propuesta y qué se rompe si se aplica. Lo revisan Juan o Alejandro, y **también responden
cuando rechazan**.
