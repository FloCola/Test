---
name: github-repository-admin
description: Nutze den repository-eigenen Fine-Grained GitHub-Zugang für Issues, Pull Requests, Discussions, Actions und versionierte Inhalte, ohne Secrets offenzulegen oder unaufgefordert destruktive/Admin-Aktionen auszuführen.
compatibility: FloCola-Repositories mit GH_REPO_TOKEN und GH_REPO_ACC sowie GitHub Actions.
metadata:
  owner: FloCola
  central-contract: https://github.com/FloCola/Bibliotheken/blob/main/governance/GITHUB-REPOSITORY-ACCESS.md
  version: "4"
  contract-revision: "github-access-v4"
---
# Repository-GitHub-Zugang
Connector bevorzugen, wenn er reicht. Zusätzliche Repo-Funktionen über den eigenen Actions-Weg.
Werte von `GH_REPO_TOKEN`/`GH_REPO_ACC` nie anfordern/ausgeben. `GH_REPO_ACC=FloCola`;
Token nur an dieses Repo binden. Vor Nutzung **Repository GitHub capability probe** prüfen.
Nach grünem Probe: Repo-/Contents-, Issue-, PR-, Discussion-, Actions-/Workflow-,
Status-/Variablen-Funktionen im erteilten Umfang. Wiki/Projects nicht automatisch annehmen.
Ohne ausdrücklichen Owner-Auftrag: nichts löschen, kein Force-Push/History-Rewrite,
keine Benutzer-/Rechte-/Rulesetänderung, keine Secretrotation, keine Security-Alert-
Dismissals, keine Deployments/Produktionsänderung, keine kostenpflichtigen Dienste.
Bei `TOKEN_NOT_CONFIGURED`: nur fehlende Secret-Namen melden und auf
https://github.com/FloCola/Bibliotheken/issues/17 verweisen. Keine Tokens kopieren.

## Branch-Abschluss

**Jede Arbeit hat Issue, kurzlebigen Branch und PR; nach geprüftem Merge den unveränderten, ungeschützten Arbeitsbranch ohne offene Folge-PRs entfernen, sonst Owner und nächste Aktion im Issue festhalten.**

Default-, Release-, Rescue-, Archiv- und Schutzbranches niemals allein aufgrund dieser Regel löschen. Vor Löschung Merge-/PR-Zuordnung, aktuellen Head, offene Folge-PRs und Schutzstatus erneut prüfen.

## Infrastruktur-Grenze

Deployments ab Installation/Rollout, Remotezugriffe, VPN, SSH, RDP, Zugriffs-Keys/Secrets, Hostdokumentation, Runnerbetrieb/-registrierung und Live-Abfragen von Hosts/Diensten gehören ausschließlich nach `FloCola/Infrastruktur`. Produkt-/Library-Repos liefern Source/Build/Pakete/Releases; CI darf freigegebene Runnerlabels verwenden, verwaltet die Runner aber nicht. Für Betrieb/Zugriff auf Infrastruktur verweisen und keine parallelen Betriebsstrukturen aufbauen.

## API-Key-Zugriff und Wiki

- **Connector zuerst.** Native Connector-Funktion nicht durch eigenen HTTP-Code ersetzen.
- Für zusätzliche Funktionen des eigenen Repositories den repo-eigenen `GH_REPO_TOKEN` und den vorhandenen lokalen Capability-/Adminweg verwenden. Nur tatsächlich geprüfte Endpoints als verfügbar behandeln.
- Für Funktionen, die Connector und lokaler Repo-PAT-Weg nicht abdecken, ist `FloCola/Infrastruktur` der zentrale kontrollierte Bridge-Pfad. `GH_ADMIN_TOKEN` bleibt ausschließlich dort und wird niemals kopiert oder von einer KI angefordert.
- Zentral live verifiziert: Fine-Grained-Key kann ein **initialisiertes privates Wiki** über Git HTTPS lesen, schreiben und zurücklesen (OpsWorkbench, Infrastruktur-Run 37037859389).
- `WIKI_INITIALIZATION_REQUIRED`: Wiki ist aktiviert, besitzt aber noch keinen HEAD. Einmalig in GitHubs Weboberfläche eine `Home`-Seite anlegen; danach Fast-Forward + Readback verwenden.
- `GH_REPO_ACC`/`GH_ADMIN_ACC` sind Diagnosewerte; maßgeblich ist die live vom Token gelesene GitHub-Identität.

