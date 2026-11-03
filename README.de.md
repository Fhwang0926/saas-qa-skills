# SaaS Web QA Skill

[한국어](README.md) | [English](README.en.md) | [日本語](README.ja.md) | [Tiếng Việt](README.vi.md) | [Español](README.es.md) | [Português](README.pt.md) | [Français](README.fr.md) | Deutsch | [Italiano](README.it.md)

Ein Skill zur Prüfung von Websites und SaaS-Diensten, responsiven Oberflächen und Barrierefreiheit. Er übernimmt ausgewählte Arbeitsweisen öffentlicher Skills von Anthropic, Vercel, Microsoft und weiteren QA-Quellen. Anleitungen und Checklisten sind enthalten; die ursprünglichen Skills und ihre Werkzeuge werden nicht installiert.

Je nach Auftrag unterstützt der Skill auch risikobasierte QA-Planung, API-Prüfungen, die Durchsicht vorhandener Playwright- oder Cypress-Tests und die Untersuchung von Fehlern. Siehe [Quellen und Umfang](skills/saas-web-qa/references/sources.md).

Bei angemeldeten Prüfungen werden autorisierte Rolle und Arbeitsbereich, relevante Listen und Filter sowie der Umfang der Persistenzprüfung unterschieden. Getrennte Browsersitzungen können dennoch serverseitige Daten gemeinsam nutzen.

Bei persona-basierter QA durchlaufen zehn simulierte Nutzer den Dienst in einem echten Browser. Wenn möglich, sammeln Subagenten Befunde und Screenshots; bei beauftragten Korrekturen werden die Wege erneut geprüft. Siehe [Ablauf](skills/saas-web-qa/references/persona-journeys.md).

## QA-Ablauf

- **Diagnostizieren, beheben und erneut prüfen:** Sowohl bei allgemeiner als auch bei persona-basierter QA werden beauftragte Korrekturen im vereinbarten Umfang umgesetzt. Sobald der laufende Dienst die Änderung übernommen hat, wird das ursprüngliche Verhalten erneut geprüft. Ist das nicht möglich, werden Grund und ungeprüfter Umfang gemeldet.
- **Getrennte Wege:** Bei mehreren Funktionen werden Einstieg und Erfolgskriterium für jeden Weg festgelegt. Die persona-basierte QA trennt die Ergebnisse je Weg und erfasst pro Problem, wie viele Rollen den Schritt bewerten konnten und wie viele betroffen waren. Die Sortierung erfolgt nach Häufigkeit; schwere Probleme werden gesondert hervorgehoben.
- **Vor und nach der Anmeldung:** Ist die Anmeldung blockiert, aber eine autorisierte Sitzung vorhanden, können angemeldete Funktionen separat geprüft werden. Ein durchgehend erfolgreicher Gesamtweg wird dadurch nicht behauptet.

## Berücksichtigte öffentliche QA-Skills

Arbeitsweisen aus den folgenden sieben Skills oder Sammlungen wurden selektiv in einen `saas-web-qa`-Skill übernommen. Die Originalpakete, vollständigen Regeln, Skripte und Werkzeuge werden nicht mitgeliefert oder installiert. Links und Umfang stehen unter [Quellen](skills/saas-web-qa/references/sources.md).

| Öffentlicher Skill oder Sammlung | Übernommene Arbeitsweise |
| --- | --- |
| Anthropic `webapp-testing` | Gerenderte Seiten prüfen, bevor Nutzeraktionen und Ergebnisse geprüft werden. |
| Vercel `web-design-guidelines` | Prüfung von UI, Nutzbarkeit, Interaktion und Barrierefreiheit. |
| Microsoft `playwright-cli` | Arbeitsweisen für Browserinteraktion und Automatisierung. |
| `qa-skills` | Risikobasierte Planung, explorative QA, API-Prüfung und Fehlerberichte. |
| `e2e-skills` | Qualitätsprüfung vorhandener E2E-Tests und Untersuchung von Fehlern. |
| TestDino `playwright-skill` | Browsertests mit der vorhandenen Playwright-Umgebung des Projekts. |
| `cypress-agent-skill` | Browsertests mit der vorhandenen Cypress-Umgebung des Projekts. |

## Einen Agenten mit Installation und QA beauftragen

Gib deinem Coding-Agenten beispielsweise den folgenden Auftrag. Das Repository muss auf GitHub veröffentlicht und für den Agenten zugänglich sein.

```text
Installiere den Skill saas-web-qa aus https://github.com/Fhwang0926/saas-qa-skills
im aktuellen Projekt, lies seine Anleitung und führe die folgende QA durch.
Falls der Skill bereits installiert ist, prüfe vor der Nutzung, ob er die Aufgabe unterstützt.

Ziel: Anmeldeseite des aktuellen Projekts
Umfang: Desktop- und Mobilansicht, Anmeldung und Barrierefreiheit
```

Wenn du nur die Installation möchtest, beauftrage keine QA. Für die Erkennung des Skills kann eine neue Sitzung erforderlich sein; kann der Agent die installierten Dateien lesen, kann er ihre Anleitung in derselben Sitzung befolgen.

### Anleitung für Agenten

1. Ermittle Zielprojekt und Agent und lies die Anweisungen des Nutzers und Projekts. Ist `saas-web-qa` installiert, lies `SKILL.md` und die relevanten Referenzen und prüfe, ob sie die Aufgabe abdecken; der Name allein belegt keine aktuelle Version. Verwende die Installation, wenn sie genügt. Andernfalls prüfe die zugängliche Quelle dieses Repositorys, die Installationsquelle und lokale Änderungen; aktualisiere nach den geltenden Regeln, ohne nicht sicher ersetzbare Arbeit zu überschreiben. Ist eine Aktualisierung nicht sicher, verwende nach Möglichkeit direkt die Quellanweisungen. Melde fehlenden Zugriff oder fehlende Funktionen.
2. Falls nötig, führe den folgenden Installationsbefehl im Zielprojekt aus. Ist eine interaktive Auswahl nicht möglich und der Agent bekannt, wähle nur diesen Agenten; für Codex ergänze `--agent codex -y`. Verwende `-g` nur bei gewünschter globaler Installation. Beachte Berechtigungen und Werkzeugregeln der Umgebung.
3. Prüfe Installationsergebnis und Pfad und lies `SKILL.md` sowie die relevanten Dateien unter `references/`. Ist der Skill in der Sitzung nicht registriert, aber sind die Dateien lesbar, befolge sie direkt. Führe keine QA aus, wenn nur die Installation beauftragt wurde.
4. Nutze bevorzugt den laufenden Dienst und den verfügbaren Browser. Befolge die Regeln des Nutzers und Projekts für Builds, Tests, Serverstarts, Datenbanken und externe Dienste. Fehlen Werkzeuge oder Zugriff, melde Hindernis und erledigten Umfang; behaupte keinen unbelegten Erfolg.

## Direkte Installation

Führe nach Veröffentlichung des Repositorys im Zielprojekt diesen Befehl aus. Erforderlich ist Node.js 22.20 oder neuer; wähle den Agenten bei der Abfrage aus.

```bash
npx skills add Fhwang0926/saas-qa-skills --skill saas-web-qa
```

Für eine lokale Kopie ersetze den Pfad durch den tatsächlichen Speicherort:

```bash
npx skills add /path/to/saas-qa-skills --skill saas-web-qa
```

Standardmäßig gilt die Installation für das Projekt. Ergänze `-g` für eine globale Installation. Starte den Agenten bei Bedarf neu, damit er den Skill erkennt.

## Verwendung

```text
$saas-web-qa Prüfe die Anmeldeseite auf Desktop und Mobilgeräten und melde reproduzierbare Probleme.
```

### Diagnose, Korrektur und erneute Prüfung in einem Auftrag

```text
$saas-web-qa Prüfe den laufenden Dienst aus Sicht von zehn simulierten Nutzerrollen.
Nutze nach Möglichkeit getrennte Subagenten und prüfe öffentliche Seiten sowie
die Kernfunktionen mit einem autorisierten Konto in einem echten Browser.
Halte verwirrende oder blockierende Stellen mit Screenshots fest und melde je
Problem, wie viele Rollen den Schritt erreichten und wie viele es erlebten.
Behebe bestätigte Probleme gemeinsam, wiederhole die Wege unter vergleichbaren
Bedingungen und berichte, was behoben wurde und was offen bleibt.
```

Der Skill liefert Anweisungen, aber keinen Browser, kein Playwright, keine laufende Anwendung und keine Konten. Tatsächliche Prüfungen erfordern die passende Umgebung und Zugriffsrechte. Regeln des Nutzers und Projekts haben Vorrang.
