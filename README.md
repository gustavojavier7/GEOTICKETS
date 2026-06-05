# 🎫 GEOTICKETS — Sistema de Tickets Operativos (CCTV / CA)

Repositorio para la gestión de tickets de infraestructura de videovigilancia, control de acceso y sistemas asociados en planta.

## Flujo de trabajo

1. **Abrir un ticket** usando el template [Registrar ticket rápido](https://github.com/gustavojavier7/GEOTICKETS/issues/new?template=registro-ticket-rapido.yml)
2. El workflow `assign-geo-ticket-id` asigna automáticamente un ID `GEO-XXXX` al título
3. El workflow `inactivity-reminders` monitorea tickets abiertos y envía recordatorios según prioridad

## Labels

| Prefijo          | Labels principales                                      | Descripción |
|------------------|---------------------------------------------------------|-----------|
| tipo:            | registrar-ticket                                        | Tipo de issue |
| prioridad:       | baja, media, alta, urgente                              | Impacto del incidente |
| estado:          | abierto, en-curso, esperando-respuesta, cerrado        | Ciclo de vida del ticket |
| **sistema:**     | **ccure**, **hikvision-230**, **hikvision-185**, **hikvision-70**, **hikvision-14**, **hikvision-11**, **redes**, **pc-windows** | **Sistema / Planta afectada** |
| solicitante:     | evelin-sosa, jennifer-castilla, jesus-martin, gustavo-lopez | Quién reporta |
| escalamiento:    | respuesta-proveedor-recibida, requiere-reemplazos, visita-en-sitio, capex, bloqueado-tercero | Acciones requeridas |

## Automatización

| Workflow                  | Disparador          | Acción |
|---------------------------|---------------------|--------|
| assign-geo-ticket-id      | Nuevo issue         | Asigna ID GEO-XXXX y agrega comentario |
| inactivity-reminders      | Cada 8 horas        | Notifica issues inactivos según prioridad (con pausa de 7 días tras respuesta humana) |

## Scripts

| Script                          | Uso |
|---------------------------------|-----|
| `scripts/sync_labels.sh`        | Sincroniza labels canónicos en el repo |
| `scripts/normalize_legacy_labels.sh` | (Opcional) Migra labels legacy → canónicos |

### Cómo sincronizar labels

Ejecutá en tu terminal (con GitHub CLI instalado y autenticado):

```bash
bash scripts/sync_labels.sh
