# Start Docker

1. Voordat je aan de slag kan gaan, dient Docker geïnstalleerd te zijn (https://www.docker.com/products/docker-desktop/)
2. Zorg ervoor dat de volgende poorten vrij zijn: 8080, 8000 and 27017
3. Om zeker te zijn dat de LDES Client via docker de gepubliceerde LDES in localhost correct kan uitlezen, gebruiken we de hostname van jouw laptop/desktop.
   Ga naar een bash terminal (bv. in Visual Studio Code) en gebruik dit command `export HOSTNAME=$(hostname)`
  
# Start LDES server
4. Start your LDES server met volgende command:
`docker-compose.yml uit demo_verkeersboete kan gebruikt worden`

Wanneer je nu naar 
http://localhost:8080/verkeersboete gaat, zoal je zien dat er reeds een LDES gepubliceerd is, maar nog zonder members.

# Publiceer de json-ld files als LDES members naar Apache NiFi listener:

4. ga eerst naar mapje met alle verkeersboetes:
```bash
cd verkeersboetes
```

5. Gebruiken we dit command:
```bash
curl -X POST http://localhost:8080/verkeersboete -H "Content-Type: application/json-ld" -d @verkeersboete.jsonld
```

# Publiceer de json-ld files als LDES members via Linked data interactions orchestrator:

Ingest verkeersboete gebruik makend van Linked Data Transformation Orchestrator (LDTO) Workflow
Met deze stappen kan een een jsonld file omgezet worden naar een versie object met behulp van de [VSDS Linked Data Transformation Orchestrator (LDTO)](https://github.com/Informatievlaanderen/VSDS-Linked-Data-Interactions) workflow (see [config](./ldio-workflow.config.yml)).

```bash
cd verkeersboetes
```


```bash
curl -X POST http://localhost:9003/data  -H "Content-Type: application/ld+json" -d "@Verkeersboete.jsonld"
```

# Bekijken van gepubliceerde LDES

5. Controleer of de eerste pagina de verkeersboete bevat
```bash
curl http://localhost:8080/verkeersboete/by-page?pageNumber=1
```

# LDES verkeersboetes offline zetten
6. Stop systems
```bash
docker compose down
```
