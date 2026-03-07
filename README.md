# video2faces
App LAN (Streamlit + Docker) per estrarre volti dai video e salvare crop + JSON per ciascun file, con download via file server e ZIP su richiesta

**video2faces** estrae volti da file video e salva:
- immagini (crop dei volti)
- metadati JSON per ogni video

È pensato per uso **in LAN** con UI web (Streamlit) e download via file server (Caddy).

## Porte
- UI Streamlit: `http://<HOST_OR_IP>:8502`
- File server (download): `http://<HOST_OR_IP>:8503`

## Struttura consigliata su host (Ubuntu)
Esempio:
