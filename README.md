# HackingEtico

Proyecto de **ciberseguridad y hacking ético**. Alcance por definir.

## Posibles líneas de trabajo

- **Laboratorio de prácticas:** máquinas vulnerables, retos y CTF en red aislada.
- **Gestión de auditorías:** alcance, hallazgos, evidencias y reportes.
- **Dashboard de vulnerabilidades:** inventario, severidad y seguimiento.
- **Formación:** guías, ejercicios y material de concienciación.
- **Automatización defensiva:** comprobaciones y reportes programados.

> Solo se trabaja contra sistemas propios o con autorización escrita. Nada de
> malware real, datos de terceros ni ataques a infraestructura ajena.

## Stack

Por definir. Si termina siendo una plataforma web, se reutiliza el stack de EVAS:

- SvelteKit 3 + TypeScript + Tailwind v4.
- FastAPI + SQLAlchemy + Alembic + PostgreSQL.
- Docker Compose + Cloudflare Tunnel.

Si es un laboratorio, los objetivos vulnerables van en una red Docker **aislada**
y nunca se publican directamente a Internet.

## Estado

Documentación inicial. **Sin código todavía.**

- [`AGENTS.md`](./AGENTS.md) — reglas para el agente.
- [`ACCESOS.md`](./ACCESOS.md) — servidor, BD, Docker, GitHub, Cloudflare, R2 y SMB.

## Puertos previstos

- Web: `127.0.0.1:8085`
- Dominio: `hackingetico.hapmed.qzz.io`
- Base: `hackingetico` en el PostgreSQL existente
