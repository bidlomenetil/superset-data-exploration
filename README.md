# Apache Superset data exploration

Data exploration platform with a Flask/Python backend and a React/TypeScript frontend, including visualization plugins and SQL exploration.

This repository is a separately imported source snapshot of [superset](https://github.com/apache/superset). Upstream contributors created the imported application; local work is recorded in the commits after the source import. See [Upstream source](UPSTREAM_SOURCE.md) for attribution.

## Read the history accurately

The local history starts with a source import on November 3, 2026. The parent year directory and the “Original project year” field do not establish a historical contribution date or a release tag. The imported upstream commit and release are not recorded in the available provenance file.

## Navigate the source

| Path | Responsibility |
| --- | --- |
| [superset/](superset/) | Backend application and database integrations |
| [superset-frontend/](superset-frontend/) | Frontend and visualization workspaces |
| [tests/](tests/) | Backend unit and integration tests |
| [docker/](docker/) | Container development configuration |
| [INSTALL.md](INSTALL.md) | Installation entry point |

## Prepare development

Read `INSTALL.md`, `AGENTS.md`, `pyproject.toml`, and `superset-frontend/package.json`. Use the repository development instructions to configure Python, frontend dependencies, and a metadata database. `docker-compose.yml` is an additional development entry point; inspect its environment settings before starting it.

The commands below are existing project entry points, to run after their toolchain, dependency, and service prerequisites are ready:

```sh
pytest tests/unit_tests/
pre-commit run
```

## Validation scope

The documentation change was checked for local link targets, manifest command references, and whitespace errors. Application builds, dependency installation, and service-backed test suites were not run for this documentation change. These instructions do not establish deployment readiness.

## Preserve upstream licensing

Missing upstream license notices were restored from the official repository. [License restoration](LICENSE_RESTORATION.md) records the retrieval revision, exact source URLs, and SHA-256 hashes. That revision does not identify the imported application snapshot. Read per-file and subtree notices as well as the root license before redistribution. This documentation does not change the license of imported code.

## Install and run locally

The repository includes a development Compose environment. Review `docker/.env` and its referenced configuration, choose local credentials, then build and start it:

```sh
docker compose up --build
```

Use `docker compose logs` to inspect initialization and `docker compose down` to stop the environment. The frontend can also be developed from `superset-frontend/` using its package scripts; backend dependency sets are in `requirements/`. Read `INSTALL.md` before choosing a native setup.

## Plan a deployment

The top of `docker-compose.yml` explicitly says the supplied Compose environment is not supported for production. Use the deployment guidance and `helm/` configuration to plan secrets, metadata database persistence, worker queues, and ingress for your target environment. Do not promote the development Compose defaults directly to production.
