# Práctica: Evaluación de Seguridad de Active Directory con ARES

## Curso

Curso de Especialización en Ciberseguridad en Entornos de las Tecnologías de la Información

## Duración

20 horas

## Objetivos

Al finalizar esta práctica el alumnado será capaz de:

- Desplegar una infraestructura Active Directory de laboratorio.
- Instalar y configurar ARES.
- Definir alcances de evaluación.
- Realizar reconocimiento sobre un dominio.
- Identificar configuraciones inseguras.
- Detectar problemas de permisos.
- Analizar riesgos asociados a Active Directory.
- Elaborar informes técnicos.

---

# Escenario

## Infraestructura

| Equipo | Sistema Operativo | IP |
|----------|----------|----------|
| Kali | Kali Linux | 192.168.56.10 |
| DC01 | Windows Server 2022 | 192.168.56.100 |
| WIN11-01 | Windows 11 | 192.168.56.101 |

Dominio:

cibes8a.local

---


# Parte 1. Preparación del Dominio

## Instalación de Active Directory

Instalar en active directory en el servidor y promoverlo a serrvidor del dominio cibes8a


## Crear usuarios

- Director
- Profesor1
- Profesor2
- Profesor3
- Alumno1
- Alumno2
- Alumno3
- Alumno4
- SoporteIT

---

## Grupos

- IT
- Docentes
- Dirección
- Alumnos

---

## Configuraciones inseguras

### Usuario con contraseña débil

Usuario:

Alumno1

Contraseña:

Password123!

### Usuario con contraseña que nunca expira

Profesor2

### Carpeta compartida

\\\\DC01\\material

Permisos:

Todos lecturas

---

# Parte 2. Instalación de Kali

Actualizar el sistema:

```bash
sudo apt update
sudo apt full-upgrade -y
```

Instalar dependencias:

```bash
sudo apt install docker.io docker-compose git python3-pip -y
```

Habilitar Docker:

```bash
sudo systemctl enable docker
sudo systemctl start docker
```

---

# Parte 3. Instalación de ARES

## Descarga

```bash
git clone https://github.com/Mafifrizi/ARES.git
cd ARES
```

## Configuración

```bash
cp .env.example .env
```

Generar SECRET_KEY:

```bash
python3 -c "import secrets; print(secrets.token_hex(32))"
```

---

# Docker Compose

```yaml
version: "3.9"

services:

  postgres:
    image: postgres:16
    container_name: ares-postgres

    environment:
      POSTGRES_USER: ares
      POSTGRES_PASSWORD: areslab
      POSTGRES_DB: ares

    volumes:
      - postgres_data:/var/lib/postgresql/data

  ares:
    build: .
    container_name: ares

    depends_on:
      - postgres

    ports:
      - "8000:8000"

    environment:
      DATABASE_URL: postgresql://ares:areslab@postgres:5432/ares
      SECRET_KEY: CAMBIAR_POR_LA_GENERADA

volumes:
  postgres_data:
```

Levantar servicio:

```bash
docker compose up -d
```

---

# Parte 4. Reconocimiento

Identificar:

- Nombre DNS del dominio.
- Equipos unidos al dominio.
- Usuarios.
- Grupos.
- Unidades Organizativas.
- Recursos compartidos.

---

# Parte 5. Auditoría

Comprobar:

## Usuarios

- Contraseñas débiles.
- Contraseñas sin caducidad.
- Usuarios inactivos.
- Usuarios privilegiados.

## Recursos compartidos

Analizar:

\\\\DC01\\material

## Políticas

- Complejidad.
- Historial.
- Longitud.
- Bloqueos.

---

# Parte 6. Informe Técnico

Para cada hallazgo documentar:

## Título

## Descripción

## Evidencia

## Impacto

## Recomendación

## Criticidad

- Alta
- Media
- Baja

---

# Entrega

Documento PDF que incluya:

- Inventario.
- Hallazgos.
- Evidencias.
- Recomendaciones.

---

# Rúbrica

| Criterio | Puntos |
|-----------|----------|
| Despliegue laboratorio | 15 |
| Instalación ARES | 15 |
| Inventario dominio | 10 |
| Enumeración usuarios | 10 |
| Enumeración grupos | 10 |
| Análisis permisos | 10 |
| Análisis políticas | 10 |
| Evidencias | 10 |
| Informe final | 10 |

Total: 100 puntos