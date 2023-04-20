# Ingest verkeersboete gebruik makend van Linked Data Transformation Orchestrator (LDTO) Workflow
Met deze stappen kan een een jsonld file omgezet worden naar een versie object met behulp van de [VSDS Linked Data Transformation Orchestrator (LDTO)](https://github.com/Informatievlaanderen/VSDS-Linked-Data-Interactions) workflow (see [config](./ldio-workflow.config.yml)).

1. Launch systems
```bash
docker compose up -d
```
4. Upload [verkeersboete.jsonld](./verkeersboete.jsonld) file
```bash
curl -X POST http://localhost:9003/data  -H "Content-Type: application/ld+json" -d "@verkeersboetes/verkeersboete1.jsonld"
```

curl -X POST http://localhost:9003/data  -H "Content-Type: application/ld+json" -d "@verkeersboete.jsonld"


5. Controleer of de eerste pagina de verkeersboete bevat
```bash
curl http://localhost:8080/verkeersboete/by-page?pageNumber=1
```
6. Stop systems
```bash
docker compose down
```
