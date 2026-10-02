---
name: github-repository-admin
description: Nutze den repository-eigenen Fine-Grained GitHub-Zugang für Issues, Pull Requests, Discussions, Actions und versionierte Inhalte, ohne Secrets offenzulegen oder unaufgefordert destruktive/Admin-Aktionen auszuführen.
compatibility: FloCola-Repositories mit GH_REPO_TOKEN und GH_REPO_ACC sowie GitHub Actions.
metadata:
  owner: FloCola
  central-contract: https://github.com/FloCola/Bibliotheken/blob/main/governance/GITHUB-REPOSITORY-ACCESS.md
  version: "1"
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

