# Miniprojekt Dockerfile 

Dieses Miniprojekt wird mit Ngix gemacht um eine Webseite einzurichten

## Voraussetzungen
- Docker installiert
- Git (für Versionskontrolle und Upload zu GitHub/GitLab)

---

## Setup-Anleitung

### 1 Repository klonen
```sh
git clone [https://github.com/Yat008/M169/](https://github.com/butter84/projekt_dockerfile)
cd projekt_dockerfile
```

### 2 Projektstruktur
Stellen Sie sicher, dass Ihr Verzeichnis wie folgt aussieht:
```
projekt_dockerfile/
│── Dockerfile
│── website/
│   ├── index.html
│   ├── styles.css
│── logs/   (dieses Verzeichnis speichert Logs)
│── README.md
```

**Hinweis:** Git erlaubt keine leeren Ordner. Um `logs/` im Repository zu behalten, fügen Sie eine leere `.gitkeep`-Datei hinzu:
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
    -v $(pwd)/website:/usr/share/nginx/html \
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


