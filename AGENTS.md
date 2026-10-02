# AGENTS

Projektregeln und vorhandene Dokumentation haben Vorrang. Keine Secrets in Git, Logs, Issues oder Prompts.

## Repository-eigener GitHub-Zugang
Dieses Repository wird für einen eigenen Fine-Grained PAT vorbereitet. Skill/Workflow folgen dem zentralen Vertrag in FloCola/Bibliotheken #17.

## Repository-eigener GitHub-Zugang
Dieses Repository ist für einen eigenen Fine-Grained PAT vorbereitet. Vor GitHub-Arbeit
außerhalb des normalen ChatGPT-Connectors `skills/github-repository-admin/SKILL.md`
lesen und bei Bedarf **Repository GitHub capability probe** ausführen.
Secrets: `GH_REPO_TOKEN`, `GH_REPO_ACC=FloCola`. Werte nie anfordern/ausgeben.
Token nur an dieses Repository binden. Vor grünem Probe Einrichtung nicht behaupten.
Technische Rechte ersetzen keine Projekt-/Sicherheits-/Produktionsfreigabe.
Zentrale Einrichtung/Rotation: https://github.com/FloCola/Bibliotheken/issues/17

## GitHub-native Arbeitsweise und Branch-Abschluss

- GitHub-Funktionen direkt nutzen, sobald der Connector oder der geprüfte repo-eigene Zugang sie anbietet.
- Idee/Architekturfrage → **Discussion**; angenommene Architekturentscheidung → **Decision/ADR-Discussion** mit Ownerbeleg.
- Gap, Bug, Migration oder konkrete Umsetzung → **Issue**; Priorität, Status und Roadmap → **Project**.
- Dauerhaftes Handbuch-/Runbookwissen → **Wiki**; Codeänderung/Abnahme → **Pull Request + Checks**; Veröffentlichung → **Release**.
- Keine neuen aktiven `GAPS`-, `ROADMAP`-, `DISCUSSIONS`-, `STATUS`- oder `HANDOFF`-Dateien im Source, sofern es kein versionsgebundener Build-/API-/Formatvertrag ist.
- **Jede Arbeit hat Issue, kurzlebigen Branch und PR; nach geprüftem Merge den unveränderten, ungeschützten Arbeitsbranch ohne offene Folge-PRs entfernen, sonst Owner und nächste Aktion im Issue festhalten.**

## Exklusive Infrastruktur-Zuständigkeit

**Deployments ab Installation/Rollout, Zugriffe und Remotezugriffe, VPN, SSH, RDP, Zugriffs-Keys/Secrets, Hostdokumentation, Runnerbetrieb/-registrierung sowie Live-Abfragen von Hosts/Diensten werden ausschließlich in [FloCola/Infrastruktur](https://github.com/FloCola/Infrastruktur) behandelt.**

Dieses Repository bleibt für Source, Build, Tests, Pakete und Releases zuständig. CI darf freigegebene Runnerlabels konsumieren; Runnerbereitstellung, Hostzugriff und Betriebsautomation bleiben in Infrastruktur. Für Betrieb/Zugriff nur auf Infrastruktur-Issues, Workflows und Verträge verweisen; keine parallelen Deployment-, Host-, VPN-, SSH-, RDP-, Key-, Runner- oder Live-Inventarstrukturen anlegen. Bestehende solche Inhalte werden nach Infrastruktur migriert statt dupliziert.

