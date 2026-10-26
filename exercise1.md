# Ejercicio 11.1 – Calentamiento

Supongamos un equipo de seis personas que desarrolla una aplicación en **Python** (una API con FastAPI) y que pronto saldrá a producción.

## Herramientas

- **Linting:** `ruff` (rápido, reemplaza a flake8 e isort) o `pylint`; para tipos, `mypy`.
- **Formato:** `black` o el propio `ruff format`.
- **Pruebas:** `pytest`, con `pytest-cov` para medir cobertura y `tox` o `nox` para correrlas en varias versiones de Python.
- **Construcción:** Python no se compila, así que "build" significa empaquetar: `build` + `pyproject.toml` para generar el wheel, o `docker build` si se despliega en contenedor. `pip-tools` o `poetry` fijan las dependencias.

## Alternativas a Jenkins y GitHub Actions

GitLab CI/CD, CircleCI, Travis CI, Azure Pipelines, Bitbucket Pipelines, Jenkins X, TeamCity, Drone y Buildkite. Si el código ya vive en GitLab o Bitbucket, lo natural es usar el CI de esa misma plataforma.

## ¿Autoalojado o en la nube?

Para un equipo de seis personas elegiría un CI **en la nube**. No hay que mantener servidores, parchear ni escalar runners, y el tiempo del equipo se queda en el producto. Los planes gratuitos o baratos alcanzan para un proyecto de este tamaño.

Cambiaría de opinión si hay requisitos de seguridad o cumplimiento que impidan sacar el código o los secretos de la red interna, si las pruebas necesitan hardware especial (GPU, dispositivos) o si el volumen de minutos de CI hace que la nube salga más cara que mantener runners propios. Para decidir necesitaría saber:

1. el presupuesto y el volumen esperado de builds;
2. las restricciones legales o de seguridad del cliente;
3. cuánto dura la suite de pruebas;
4. si alguien del equipo puede dedicar tiempo a operar la infraestructura.
