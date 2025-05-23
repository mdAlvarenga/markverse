# Markverse

**Markverse** es el entorno de orquestación general de **Xarvis Mark I**, un asistente de inteligencia artificial personalizado y modular. Este repositorio centraliza y conecta todos los componentes del sistema, incluyendo la lógica principal (`xarvis-mark-i-core`), la automatización de flujos con n8n, servicios de infraestructura como Caddy, y futuras integraciones como interfaces web o APIs.

---

## 🌐 Rol de Markverse

Markverse no contiene lógica de negocio: su función es integrar, desplegar y mantener **todo el ecosistema Xarvis funcionando en conjunto**, ofreciendo:

- Orquestación completa vía Docker Compose
- Configuración de red, puertos y servicios
- Conexión entre módulos como:
  - `xarvis-mark-i-core`: núcleo de razonamiento
  - `n8n`: automatización y conectores (WhatsApp, Calendar, email, etc.)
  - `Caddy`: servidor reverse proxy con soporte para HTTPS automático
  - Redis, PostgreSQL u otras dependencias (opcionales)
  - Frontends en React, Angular o Next.js

---

## 🚀 Servicios incluidos

| Servicio         | Propósito                              | Acceso local                 |
|------------------|----------------------------------------|------------------------------|
| `n8n`            | Automatización personal y conectores   | `http://agente.localhost`   |
| `xarvis-mark-i-core` | Lógica del asistente (conectado por API) | Interno                    |
| `springboot`     | Backend de prueba (comentado)          | `http://api.app.localhost`  |
| `react`          | Frontend de prueba (comentado)         | `http://app.localhost`      |
| `postgres-n8n`   | Base de datos para n8n                 | —                            |
| `postgres-app`   | Base de datos para la app              | —                            |
| `caddy`          | Proxy inverso y soporte HTTPS futuro   | —                            |

---

## 📦 Estructura del repositorio

```
/infra
  /caddy             ← Configuración de Caddy
  /n8n               ← Configuración persistente de flujos
  /env               ← Variables de entorno centralizadas
/docker-compose.yml ← Orquestación completa
README.md
```

---

## 🔧 Cómo levantarlo

1. Instalar Docker y Docker Compose:
```bash
sudo apt update && sudo apt install docker.io docker-compose -y
```

2. Clonar el repositorio:
```bash
git clone https://github.com/tu-usuario/markverse.git
cd markverse/infra
```

3. Levantar los servicios activos:
```bash
docker-compose up -d
```

4. Acceder a los servicios:
- `http://agente.localhost:5678` para n8n

> ⚠️ Para usar .localhost como dominios, agregá las siguientes líneas en `/etc/hosts`:
```
127.0.0.1 agente.localhost
127.0.0.1 app.localhost
127.0.0.1 api.app.localhost
```

---

## 🔐 Variables de entorno

Este proyecto utiliza un archivo `.env` con credenciales y configuraciones. Podés copiar el archivo de ejemplo y completarlo:

```bash
cp .env.example .env
```

También podés usar `docker-compose --env-file .env up -d` o herramientas como `dotenv`, `direnv`, etc.

---

## ✅ Recomendaciones

1. **Agregá a `.gitignore`**:
```gitignore
infra/.env
```

2. Si usás un dominio real, solo tenés que ajustar el Caddyfile.

3. Mantené cada servicio con su propia base de datos para facilitar pruebas y mantenimiento.

---

## 🤖 ¿Qué es Xarvis Mark I?

**Xarvis Mark I** es un asistente personal extensible que combina:

- Razonamiento contextual desde `xarvis-mark-i-core`
- Conectividad e integración mediante `n8n`
- Capacidad de orquestación total con `markverse`
- Futuras interfaces web para visualizar y editar información personal

---

## 🔜 Próximos pasos

- Integración con dominio personalizado y HTTPS
- Conectores estables para WhatsApp, Gmail y Calendario
- UI web para visualizar memoria y tareas
- Backup y restauración automáticos

---

## Licencia

MIT. Usalo, adaptalo y compartilo. Xarvis crece con vos.
