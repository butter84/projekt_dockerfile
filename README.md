# Miniprojekt Dockerfile 

Dieses Miniprojekt wird mit Ngix gemacht um eine Webseite einzurichten

## Voraussetzungen
- Docker installiert
- Git (für Versionskontrolle und Upload zu GitHub/GitLab)

---

## Setup-Anleitung

### 1 Repository klonen
```sh
git clone [https://github.com/butter84/projekt_dockerfile]
cd projekt_dockerfile
```

### 2 Ordnerstruktur
```
projekt_dockerfile/
│── Dockerfile
│── Website/
│   ├── index.html
│── logs/   
│── README.md
```

**Hinweis:** Git erlaubt keine leeren Ordner. Um `logs/` im Repository zu behalten, füge eine leere Datei hinzu.
```sh
touch logs/.gitkeep
```
Dann das Verzeichnis committen:
```sh
git add logs/.gitkeep
```

---

## Docker-Build und Start

### Container erstellen und starten
#### 1. Docker-Image bauen:
```sh
docker build -t my-webserver .
```

#### 2. Container starten:
```sh
docker run -d -p 8080:80 \
    -v $(pwd)/Website:/usr/share/nginx/html \
    -v $(pwd)/logs:/var/log/nginx \
    --name my-webserver my-webserver
```

#### 3. Website im Browser öffnen:
```
http://localhost:8080
```

#### 4. Logs anzeigen:
```sh
docker logs my-webserver
```

#### 5. Container stoppen:
```sh
docker stop my-webserver
```

#### 6. Container entfernen (optional):
```sh
docker rm my-webserver
```

---


