# Documentatie voor Todo Applicatie Installatie

Deze documentatie beschrijft de stappen om de Todo applicatie op te zetten en te draaien op een lokale machine met behulp van Docker Compose. Zorg ervoor dat je de volgende stappen nauwkeurig volgt om de applicatie correct te configureren en te laten draaien.

### Stap 1: Klonen van Git-repository

Clone de Git-repository naar je lokale machine:

```bash
git clone <repository_url>
cd <repository_directory>
```

### Stap 2: Configuratie van omgevingsvariabelen

Kopieer het voorbeeld van de omgevingsvariabelen naar een nieuw bestand genaamd `.env`:

```bash
cp .env.example .env
```

Bewerk het `.env`-bestand met behulp van een teksteditor en voeg de specifieke waarden toe voor de volgende variabelen:

```bash
MYSQL_USER=gebruikersnaam
MYSQL_PWD=wachtwoord
MYSQL_DB=databasenaam
MYSQL_ROOT_PASSWORD=rootwachtwoord
```

Vervang `gebruikersnaam`, `wachtwoord`, `databasenaam` en `rootwachtwoord` door de relevante gegevens.

### Stap 3: Opslaan van wijzigingen

Sla de wijzigingen op in het `.env`-bestand en zorg ervoor dat dit bestand niet wordt gedeeld via versiebeheer of openbare repositories om veiligheidsredenen.

### Stap 4: Vereisten

Zorg ervoor dat de gebruiker Traefik op zijn machine heeft geïnstalleerd voordat je doorgaat naar de volgende stap.

### Stap 5: Starten van de applicatie

Voer het volgende commando uit om de Docker containers te starten:

```bash
docker-compose up -d
```

Dit zal de Todo applicatie opstarten en laten draaien op de lokale machine.

### Opmerkingen:

- Controleer of Traefik correct is geconfigureerd en actief is op je machine voordat je de applicatie start.
- Gebruik de juiste Docker Compose-opdrachten als er specifieke vereisten zijn voor het beheer van de containers.

Door deze stappen te volgen, zou de Todo applicatie moeten worden geïnstalleerd en draaien op je lokale omgeving. Zorg ervoor dat je alle vereisten nakijkt voordat je de applicatie start.

# Projectopdracht

Welkom bij het de repository voor de doorlopende opdracht van DevOps. 

## Situatie

Je werkt voor ACME. Ze hebben onlangs een todo-applicatie ontwikkeld. 
Je wordt gevraagd om een DevOps pipeline uit te werken. Hiervoor zal je op een remote Linux machine werken.

Er zijn twee onderdelen: Back-end en Front-end. Er is geen authenticatie.

De back-end is een NodeJs applicatie die de API host. De back-end luistert op poort 3000. 
De back-end draait standaard in-memory. Met andere woorden, de taken worden enkel opgeslagen in geheugen, niet op disk. 
De back-end kan ook een connectie maken naar een mysql databank. Die stel je in met volgende environment variabelen:

* STORAGE=mysql
* MYSQL_HOST=<hostname>
* MYSQL_USER=<username>
* MYSQL_PWD=$mysqlpwd 
* MYSQL_DB=$mysqldb

De Front-end is een HTML5 statische applicatie en luistert op poort 80. 
Via AJAX calls wordt de API aangeroepen. De front-end en de API moeten op dezelfde host draaien. 
De API draait in een subfolder /api.

## Architectuur

![Architectuur](./architectuur.png)

## Opdracht:

1. Connecteer naar je Debian Linux omgeving
1. Clone deze repository
1. Bouw een container voor de back-end. De back-end draait op NodeJS. Kies zelf een tag.
1. Bouw een container voor de front-end. De front-end draait op Nginx. Je maakt gebruik van nginx. Je kan gebruik maken van de standaard configuratie.
1. Maak een docker compose file aan die deze containers refereert. Expose je front-end op poort 80.
1. Voeg Mysql toe aan je netwerk dmv een docker container. Je maakt gebruik van een mysql image. Voeg disk mappings toe zodat de state van je mysql container bewaard blijft.
1. De repository bevat een bestand init.sql. Zorg dat dit wordt uitgevoerd bij de start van de Mysql container. 
1. Configureer de API zodat die deze MySql databank gebruikt.
1. Installeer Traefik als Reverse proxy op je omgeving.
1. Configureer ssl certificaat aanvraag via LetsEncrypt
1. Expose de todo applicatie op ```https://<studentnr>.devops-ap.be```
