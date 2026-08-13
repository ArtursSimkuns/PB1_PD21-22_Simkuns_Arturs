# Broken API

## Projekta apraksts

Šis ir vienkāršs Python Flask API projekts, kas izveidots praktiskajam darbam `PB1_PD21-22 – Broken Project Rescue`.

Projekta mērķis ir salabot nepabeigtu Python projektu, pārbaudīt tā darbību lokāli, palaist testus, sakārtot Docker konfigurāciju un dokumentāciju.

API lokāli atbild uz sākumlapas pieprasījumu:

```text
http://localhost:5000
```

Sagaidāmā JSON atbilde:

```json
{
  "message": "Hello PB1"
}
```

## Projekta struktūra

```text
broken-api/
├── app.py
├── utils.py
├── requirements.txt
├── test_app.py
├── Dockerfile
├── docker-compose.yml
├── .github/
│   └── workflows/
│       └── ci.yml
└── README.md
```

Galvenie faili:

- `app.py` – Flask programmas galvenais fails;
- `utils.py` – palīgfunkcijas;
- `requirements.txt` – nepieciešamās Python bibliotēkas;
- `test_app.py` – projekta testi;
- `Dockerfile` – Docker image izveides konfigurācija;
- `docker-compose.yml` – Docker Compose konfigurācija;
- `.github/workflows/ci.yml` – GitHub Actions CI konfigurācija.

## Prasības

Lai palaistu projektu lokāli, nepieciešams:

- Python 3;
- pip;
- instalētas projekta bibliotēkas no `requirements.txt`.

Papildus Docker palaišanai nepieciešams:

- Docker Desktop;
- Docker Compose.

## Instalācija

Atver termināli projekta mapē:

```powershell
cd .\Pielikumi\broken-api
```

Instalē nepieciešamās bibliotēkas:

```powershell
python -m pip install -r .\requirements.txt
```

## Programmas palaišana lokāli

Programmu var palaist ar komandu:

```powershell
python app.py
```

Pēc palaišanas pārlūkā jāatver:

```text
http://localhost:5000
```

Ja programma darbojas pareizi, pārlūkā redzama JSON atbilde:

```json
{
  "message": "Hello PB1"
}
```

Lai apturētu programmu terminālī, jāspiež:

```powershell
Ctrl + C
```

## Testu palaišana

Testus var palaist ar komandu:

```powershell
python -m pytest
```

Veiksmīgas izpildes gadījumā rezultātā jābūt redzamam, ka tests ir izgājis, piemēram:

```text
1 passed
```

## Docker palaišana

Izveido Docker image:

```powershell
docker build -t pb1-broken-api .
```

Palaid konteineru:

```powershell
docker run -d --rm --name pb1-broken-api -p 5000:5000 pb1-broken-api
```

Pārbaudi programmu pārlūkā:

```text
http://localhost:5000
```

Apturi konteineru:

```powershell
docker stop pb1-broken-api
```

## Docker Compose palaišana

Programmu var palaist arī ar Docker Compose:

```powershell
docker compose up --build
```

Pēc pārbaudes konteineru var apturēt ar:

```powershell
Ctrl + C
```

Ja Docker Compose palaists fonā, to var apturēt ar:

```powershell
docker compose down
```

## CI pipeline

Projektā ir GitHub Actions konfigurācija:

```text
.github/workflows/ci.yml
```

CI pipeline paredzēts, lai automātiski pārbaudītu projektu, instalētu nepieciešamās bibliotēkas un palaistu testus.

CI konfigurācija ir papildināta ar Docker pārbaudi un pipeline var arī izveidot Docker image un palaist testus Docker konteinerī.

## Biežāk lietotās komandas

```powershell
python -m pip install -r .\requirements.txt
python app.py
python -m pytest
docker build -t pb1-broken-api .
docker run -d --rm --name pb1-broken-api -p 5000:5000 pb1-broken-api
docker stop pb1-broken-api
```