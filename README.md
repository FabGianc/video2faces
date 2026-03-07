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
