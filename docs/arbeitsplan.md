# Arbeitsplan (IPERKA Schritt 2)

Projekt: Container-Services fuer KMU (Nextcloud 8080, gogs/GitLab, Portainer, Persistenz, GitHub-Versionierung)  
Team: ___________________________      Datum: __________

## Struktur & Artefakte
- `docs/` → **Arbeitsplan.md**, **Testkonzept.md**, **Testprotokoll.md**, **Sicherheitskonzept.md**, **Journal.md**
- `compose/` → **docker-compose.yml**, **.env.example**, **.gitignore**
- `diagrams/` → **Systemuebersicht.png**
- `README.md`

---

## Block 1 — 150 min (Informieren, Planen, Entscheiden, IaC-Grundlage)

| Nr | Aufgabe | Kurzschritte | Dauer | Deliverables | Raster / HANOK |
|---:|---|---|---:|---|---|
| 1 | Repo & Doku-Skelett | GitHub-Repo, Ordner anlegen, Vorlagen-Dateien erzeugen | 10 | Initial-Commit „Projektstruktur“ | Versionsverwaltung • M169 1.4 |
| 2 | Anforderungen & Entscheide | Ports festlegen (NC 8080, gogs/GitLab, Portainer), gogs statt GitLab (ressourcenschonend) | 10 | `docs/README`-Notiz „Architektur-Entscheide“ | Dokumentation • M347 2.4 |
| 3 | Systemuebersicht (Diagramm) | Netzwerke, Nebencontainer (DBs), Volumes | 20 | `diagrams/Systemuebersicht.png` | IaC • M169 1.5/1.6 • M347 2.1 |
| 4 | **DIESER Arbeitsplan finalisieren** | Tabelle + Zeiten + Verantwortliche | 15 | `docs/Arbeitsplan.md` | Doku-Gliederung |
| 5 | Compose Grundgeruest | `networks`, `volumes`, `restart`, `healthcheck`-Platzhalter, `.env.example` | 20 | `compose/docker-compose.yml` (Basis) | IaC • M169 1.6 |
| 6 | Nextcloud + DB | Services **nextcloud** + **mariadb/postgres**, Volumes, Port **8080** | 30 | Compose + Screenshot `docker ps` | IaC/Persistenz • M169 1.6 |
| 7 | CVS (gogs) + DB | Services **gogs** + **db**, Volumes, Port (z.B. 3000) | 30 | Compose + Screenshot | IaC/Persistenz • M347 2.1 |
| 8 | Start & Smoke-Test | `docker compose up -d`, Health, Ports, Volumes pruefen | 10 | Screenshots in `docs/Journal.md` | Testkonzept (Vorstufe) |
| 9 | Journal-Eintrag | Ziele, erledigt, Probleme, Abweichungen | 5 | `docs/Journal.md` (Block 1) | Arbeitsjournal |

**Zwischenergebnis (DoD Block 1):** NC+DB und gogs+DB laufen mit Volumes, Diagramm & Plan vorhanden, erster Compose-Stand versioniert.

---

## Block 2 — 180 min (Realisieren, Testen, Absichern, Dokumentieren)

| Nr | Aufgabe | Kurzschritte | Dauer | Deliverables | Raster / HANOK |
|---:|---|---|---:|---|---|
| 10 | Portainer | Service ergaenzen, Zugriff testen | 10 | Compose + Screenshot | IaC |
| 11 | Ressourcenlimits | `mem_limit`, `cpus`, ggf. `ulimits` pro Service; Neustart | 25 | Compose-Diff + Portainer-Screenshot | **Ressourcenbeschraenkungen** |
| 12 | NC einrichten & Persistenztest | Admin anlegen, Datei hochladen, Neustart → Daten vorhanden | 25 | Testbeleg + Screenshot | Test/Protokoll • M169 3.3 |
| 13 | gogs einrichten & Persistenztest | Admin, Repo anlegen, lokal klonen, Push, Neustart-Check | 25 | Testbeleg + Screenshot | Test/Protokoll |
| 14 | Persistenz-Doku | Volumes/Bind-Mounts & Speicherorte auflisten | 15 | Abschnitt in `docs/README`/`Arbeitsplan` | IaC/Persistenz |
| 15 | Testkonzept final | 2 aussagekraeftige Testfaelle (NC & gogs): Randbedingungen, Mittel, Schritte, Soll | 10 | `docs/Testkonzept.md` | **Testkonzept** |
| 16 | Tests ausfuehren & protokollieren | Ist-Resultate, Screenshots, Abweichungen | 20 | `docs/Testprotokoll.md` | **Testprotokoll** |
| 17 | Sicherheitskonzept final | `.env` nutzen, keine Passwoerter im Repo, Rollen/Backups/Updates/Ports | 25 | `docs/Sicherheitskonzept.md` + `.gitignore` | **Sicherheitskonzept** • M169 1.
