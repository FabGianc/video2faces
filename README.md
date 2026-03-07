# video2faces

Estrae volti (frame/face crops) da file video e salva gli output in una cartella “outbox”, con una variante **web** per l’esecuzione tramite interfaccia.

> Nota: questo repository contiene il **pacchetto di deploy minimo** (Dockerfile + compose + reverse proxy Caddy).
> Personalizza i percorsi e le variabili in `.env` (partendo da `.env.example`).

---

## Struttura repository

.  
├─ app/  
│ ├─ Dockerfile  
│ ├─ requirements.txt  
│ ├─ video2faces.py  
│ └─ video2faces_web.py  
└─ config/  
├─ Caddyfile  
└─ docker-compose.prod.yml  


---

## Prerequisiti

- Docker Engine + Docker Compose (plugin)
- (Opzionale) Caddy via container come da `docker-compose.prod.yml`
- Connettività LAN se previsto (esposizione limitata)

---

## Avvio in produzione (Docker Compose)

1) Crea il file `.env` a partire dall’esempio:
```bash
cp .env.example .env
```
2) Avvia lo stack:
```bash
docker compose -f config/docker-compose.prod.yml --env-file .env up -d --build
```
4) Verifica container e log:
```bash
docker compose -f config/docker-compose.prod.yml ps
docker compose -f config/docker-compose.prod.yml logs -f
```

Variabili d’ambiente

Le variabili in `.env` sono pensate per:

- impostare porte e host

- definire percorsi input/output montati in container

- configurare dominio (se usi Caddy come reverse proxy)

Vedi `.env.example` per una base.

Esecuzione “local dev” (senza Docker)

Da root repo:
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r app/requirements.txt
```
Esempi (adatta eventuali argomenti/parametri ai tuoi script):

CLI:
```bash
python app/video2faces.py
```
Web:
```bash
python app/video2faces_web.py
```

Output

Per convenzione gli output (immagini/face crops/log) dovrebbero finire in una cartella tipo:

outbox/

outbox/Pictures/

outbox/Pictures/<run_YYYY-MM-DD_HHMMSS>/...

(I dettagli dipendono dalla logica interna degli script.)










