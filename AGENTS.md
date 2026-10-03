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

<!-- flocola-contract:platform-ownership:start -->
## Plattform-, Werkzeug- und Testzuständigkeit

### Bridge365-first: kleine, eigenständig debuggbare Module

**Bridge365 ist das wichtigste Produkt.** Kleinere Projekte dienen vorrangig als vorhandene Spender und begrenzte Erstconsumer für dieselben Kernfunktionen. Reihenfolge: Bridge-Bedarf/Quellen vergleichen → vorhandene Funktion in kleinen nativen Provider auslagern → kleinen echten Consumer auf exakten Paketpin anbinden → fehlende generische Bridge-Fähigkeiten upstream ergänzen → Bridge365 modulweise integrieren und separat abnehmen. Keine vollständige Nebenprojektreparatur und kein grüner Bridge-Monolith als Voraussetzung; ein isolierbarer Bridge-Baustein braucht keinen künstlichen zweiten Consumer.

**Jede Library wird für KI-Nutzung und KI-Fehlersuche entwickelt:** normale Funktions-/Profilbeschreibungen, sichere Konfiguration/Zustandsbilder und begrenzte korrelierbare Phasen-/Fehler-/Abbruch-/Cleanup-/UNKNOWN-Zugänge. Kein Patch, Subclassing, Monkeypatch oder Debugbuild zum Debuggen. Monitoring-/Development-Plane konsumiert diese Fähigkeiten; sie ersetzt sie nicht. Details: [Library-Beobachtbarkeit](https://github.com/FloCola/Bibliotheken/blob/main/governance/LIBRARY-OBSERVABILITY.md).

Vor jedem Slice genau einen Codeowner, Testowner und Bridge-Integrationspunkt benennen; bestehende Issues/PRs/Kommentare und parallele Bearbeiter beachten. Native Sprachfamilien teilen nur belegte Profile/Fixtures, keine erzwungene FFI und keine neuen Common-/Utils-Monolithen. Erfolg heißt reproduzierbarer Einzelfehler ohne Gesamtproduktstart, echtes Paket und getrennte Provider-/Kleinconsumer-/Bridge-Nachweise. Nach jedem Slice Quell-/Referenz-/Pin-Sweep; Altcode erst nach gezielter Consumerabnahme entfernen, fremde Arbeit/Archivrefs erhalten. Neue unabhängige Nebenprojektfeatures sind nachrangig.

**Herkunft und führende Koordination:** [Ownerstrategie vom 03.10.2026](https://github.com/FloCola/Bibliotheken/issues/41#issuecomment-5970653091), [Bridge365-Zerlegung #8](https://github.com/FloCola/Bridge365/issues/8). Diese Priorität ist keine Test-, Versand-, Datenbank-, Secret- oder Deploymentfreigabe. SOURCE_PREPARED, TESTED, PACKAGED und CONSUMER_VERIFIED getrennt ausweisen.

**FloCola/Deployments besitzt den gemeinsamen Deployment-Werkzeugkasten:** Ansible-Adapter, Rollen/Playbooks, Docker/Compose/Buildx/OCI-Werkzeuge, Installer-, Update-, Rollback-, Artefakt- und Recovery-Orchestrierung sowie Plan/Preflight/Apply/Verify/Receipt-Verträge. Diese Werkzeuge werden unabhängig von Bridge365 gebaut, getestet, versioniert und gehärtet. Bestehende Herstellerwerkzeuge werden integriert, nicht neu implementiert.

**FloCola/Diagnose besitzt gemeinsame Test- und Diagnosewerkzeuge:** Szenarien, synthetische Gegenstellen, Konformitäts-/Fehlerinjektionstests, Evidence-Validatoren, Replay und gezielte Diagnose. Schnelle Unit-/Negativtests bleiben zusätzlich beim jeweiligen Tool-/Librarycode; ein zentral laufender Diagnosedienst ist keine Testvoraussetzung.

**FloCola/Monitoring besitzt laufende Beobachtung:** Collector-/Providerprofile, Zeitreihen, Freshness, Health, Findings und Alarmierung. Es konsumiert versionierte Fakten und Ergebnisse, statt Deploymentwerkzeuge oder Diagnoseengine zu duplizieren.

**FloCola/Infrastruktur besitzt reale Infrastruktur und Ausführungsfreigabe:** Hosts/VMs/Netzwerk, Runnerregistrierung/-routing, Snapshots, produktive Secrets/Zugriffe und freigegebene reale Zielausführung. Ein Tool in Deployments oder ein Diagnoseprofil verleiht keine Host-, Credential- oder Mutationsrechte.

**FloCola/Bibliotheken** koordiniert gemeinsame Verträge, Wiederverwendung und Provider-/Consumerbeziehungen. Produktrepos behalten Fachregeln und Integrationsabnahme; Bridge365 ist Spender und Consumer, keine Voraussetzung für die Providerentwicklung. AISpotlight-Upgrade und Bridge-Gesamtreparatur sind kein vorgeschaltetes Gate.

Vor neuer Arbeit vorhandene Issues samt Kommentaren, offene PRs, Branches und echte Discussions lesen. Ein führendes Issue, ein Codeowner und ein Testowner je Schnitt; keine parallelen Implementierungen überschreiben. Bei nicht lesbarer Discussion den Prüfstand offenlassen, keinen geprüften Konsens behaupten.

Werkzeuge beschreiben Inputs/Outputs, Version, unterstützte Profile, Effekte, Budgets, Abbruch/Cleanup und Unknown/No-Replay. Library-/Tooltest, externes Paket, Consumerabnahme und Livezustand bleiben getrennte Nachweise. Secrets, private Schlüssel und unbereinigte Kundendaten werden nicht kopiert. Alte Quellen erst nach gezielter Consumerabnahme entfernen.

### Temporäre GitHub-Actions-Queue

Vor dem Start/Dispatch einer neuen GitHub Action die zentrale Queue-Projektion lesen, sofern der freigegebene read-only Weg erreichbar ist. NocoDB ist dabei nur temporäres Read-Model; GitHub bleibt Source of Truth. Zugriff für KIs ausschließlich über den von Infrastruktur dokumentierten Pfad `pc.local -> VPN -> interne NocoDB-Queue`. Öffentliche NocoDB-/Authelia-Zugänge sind kein KI-Automationspfad.

Queued/running Jobs mit passenden Runnerlabels und vorhandene Arbeit anderer KIs berücksichtigen; erwartete Laufzeit soweit bekannt dokumentieren. Ist die Queue nicht erreichbar, den Zustand als `UNKNOWN` festhalten und niemals „Queue leer“ behaupten. Nach Dispatch die GitHub Run-/Job-ID im führenden Issue festhalten. Die Queue wird nicht manuell gepflegt: `workflow_job completed` entfernt den Eintrag unabhängig vom Ergebnis.

Bei laufenden Actions nicht busy-waiten oder den Stream offenhalten. Run-ID, Attempt und Head festhalten; mit tatsächlich verfügbarer externer Wiederaufnahme im 15-Minuten-Takt frisch prüfen. Ohne passenden Timer `WAITING_FOR_ACTION` mit nächstem Check übergeben und Antwort beenden. Kein erfundener Hintergrundlauf, kein automatischer Redispatch/Merge/Apply; Abschluss erst nach tatsächlicher Conclusion und Evidence.
<!-- flocola-contract:platform-ownership:end -->
