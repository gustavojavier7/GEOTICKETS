# 🤖 AGENTS — Guía para Agentes y Revisores (GEOTICKETS)

Este documento define cómo deben comportarse los agentes automáticos y humanos al trabajar con los tickets.

## Reglas Generales para Agentes

1. **Siempre respetar el prefijo GEO-XXXX** en el título del issue.
2. **No modificar el ID una vez asignado**.
3. **Usar labels canónicos** (prioridad:, estado:, sistema:, etc.).
4. **Mantener claridad y brevedad** en comentarios.
5. **Cualquier comentario humano pausa los recordatorios automáticos por 7 días**.

## Flujo recomendado para Agentes

### Cuando revisás un ticket (Codex Review / Agente IA)

- Verificar que tenga:
  - ID GEO-XXXX
  - Labels de prioridad y sistema
  - Descripción clara + ubicación
- Si falta información crítica → comentar pidiendo aclaración.
- Si todo está completo → agregar label `estado:en-curso` y asignarte si corresponde.

### Al cerrar un ticket

- Agregar label `estado:cerrado`
- Dejar un comentario breve de resolución (qué se hizo, causa raíz si aplica).
- El workflow de inactividad ignorará tickets cerrados.

## Comandos útiles para Agentes

- **Actualizar prioridad**: Agregar/quitar label `prioridad:xxx`
- **Escalar**: Agregar label `escalamiento:xxx`
- **Pausar notificaciones**: Solo dejar un comentario humano (cualquier texto).

## Notas para Gustavo / Administrador

- Ejecutar periódicamente:  
  `bash scripts/sync_labels.sh`
- Revisar workflows en **Actions** tab si algo no funciona.
- El sistema está diseñado para ser **mínimo mantenimiento** una vez configurado.

---

**Referencia original**: Adaptado de TICKETSPP → GEOTICKETS
