# AGENTS.md — HackingEtico

Guía para el agente que programe este proyecto.

## Regla de oro

- Trabaja **solo** dentro de `/proyectos/HackingEtico`.
- No toques otros proyectos ni las bases `hapmed` / `evas_admin`.
- Los secretos están en [`ACCESOS.md`](./ACCESOS.md): úsalos, **no los versiones**,
  no los pegues en logs ni en el chat.
- GitHub: cuenta **`hapmed`** (credencial en `/root/.git-credentials`).
  `hector1516` es solo para consultas de lectura.
- **Ética y legalidad:** solo se prueba contra sistemas propios o con autorización
  escrita. Nada de ataques a infraestructura ajena, malware real ni datos de
  terceros.

## Estado

El alcance **no está definido todavía**. Antes de escribir código, confirmar con
el usuario:

1. ¿Laboratorio de prácticas, plataforma de auditorías, formación o dashboard?
2. ¿Web, CLI o ambas?
3. ¿Stack? Si es web, reutilizar SvelteKit 3 + FastAPI + PostgreSQL.
4. ¿Dónde se despliega: HomeLab o VPS?

No inventar funcionalidades ni asumir que es una herramienta ofensiva.

## Reglas técnicas

- El laboratorio, si existe, va en una red Docker **interna** (`hackingetico-lab`),
  sin puertos públicos y sin acceso a la LAN.
- Nada de `privileged`, `network_mode: host` ni montar el socket de Docker en la
  aplicación.
- Contenedores vulnerables solo para prácticas; documentar su propósito y aislarlos.
- Autenticación obligatoria si la plataforma se publica.
- Evidencias y reportes con datos minimizados.
- Backups y logs sin secretos.
- `.env` y `ACCESOS.md` en `.gitignore`.

## Estructura prevista (si es web)

```
HackingEtico/
├─ ACCESOS.md
├─ AGENTS.md
├─ README.md
├─ .gitignore
├─ backend/        # FastAPI
├─ frontend/       # SvelteKit
├─ ops/            # compose + Caddy
├─ lab/            # objetivos vulnerables (red aislada)
└─ docs/
```

## Verificación

```bash
# Backend
cd backend && uv sync && uv run ruff check . && uv run mypy app && uv run pytest

# Frontend
cd frontend && npm install && npm run check && npm run lint && npm run test && npm run build

# Compose
docker compose -f ops/compose.yaml config
```

Si el entorno no tiene Node/Python, usar Docker o el servidor. No reportar como
verificado lo que no se ejecutó.

## Reporte

1. Qué se implementó y qué no.
2. Archivos creados/modificados.
3. Comandos ejecutados y salida real.
4. Riesgos de seguridad y aislamiento.
5. Bloqueos y siguiente paso.
