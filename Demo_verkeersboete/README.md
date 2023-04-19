Deze bestanden kan je gebruiken bij het uitvoeren van de demo van de Smart Data Academy.

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

# Publiceer de json-ld files als LDES members

5. Gebruiken we dit command:`curl -X POST http://${HOSTNAME}:8080/verkeersboete -H "Content-Type: application/json-ld" -d @verkeersboete.jsonld`


