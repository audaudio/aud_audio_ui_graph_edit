# aud_audio_ui_graph_edit

[English](README.md) | Deutsch

[![CI](https://github.com/audaudio/aud_audio_ui_graph_edit/actions/workflows/quick_check.yaml/badge.svg)](https://github.com/audaudio/aud_audio_ui_graph_edit/actions/workflows/quick_check.yaml)

Node-Graph-Editor-Widget der Audanika Audio Engine, nach dem Vorbild von
AudioKit Flow. Reines Flutter, frei von der Engine; Teil der Audanika Audio
Engine, geplant in [aud_audio_pm](https://github.com/audaudio/aud_audio_pm).

## Motivation

- Die Audanika Audio Engine ist ein Graph aus DSP-Knoten, der in Dart
  definiert wird; ihre Nutzer müssen diesen Graphen auf jeder Plattform sehen
  und verdrahten können, die Flutter unterstützt
- AudioKit Flow zeigt ein kleines, bewährtes, MIT-lizenziertes Patch-Modell
  und eine Zeichenfläche, die es bearbeitet; das Paket portiert beides, statt
  Neues zu erfinden
- Das Widget zeichnet und bearbeitet ein Dart-Modell und meldet Änderungen als
  Callbacks (Entscheidung ui-001), sodass es ohne Oberfläche testbar ist und
  später über OSC eine entfernte Engine steuern kann

## Installation

Das Paket ist nicht auf pub.dev veröffentlicht; binde es über seine Git-Tags
ein:

```yaml
dependencies:
  aud_audio_ui_graph_edit:
    git:
      url: git@github.com:audaudio/aud_audio_ui_graph_edit.git
      tag_pattern: '{{version}}'
    version: ^0.0.3
```

## Verwendung

Das Paket ist ein Platzhalter: Das Widget folgt mit Schritt S16 des Plans der
Audanika Audio Engine (siehe [Stand](#stand)). Bis dahin exportiert es nur den
Boilerplate-Code der Flutter-Paketvorlage, mehr läuft also nicht:

```dart
import 'package:aud_audio_ui_graph_edit/aud_audio_ui_graph_edit.dart';

void main() {
  // The widget is not built yet; the package exports the boilerplate
  // Calculator of the Flutter package template until it arrives.
  print(Calculator().addOne(1));
}
```

```text
2
```

## Grenzen

- Noch kein Widget; siehe [Stand](#stand)
- Das Widget wird nicht von der Engine abhängen (Entscheidung ui-003): Apps
  binden es über `aud_audio_ui_bindings`, Plugin-Editoren über das Protokoll
  ihrer Shell

## Dokumentation

- [Plan 17: Audanika Audio
  Engine](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/tickets/2026-10-07-17-audanika-audio-engine.md),
  der das Paket als Schritt S16 plant
- Die Entscheidungen
  [ui-001](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/concepts/decisions/ui-001.md)
  (UI-Pakete sind Flutter-Widgets über Dart-Modellen) und
  [ui-003](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/concepts/decisions/ui-003.md)
  (die Engine-Adapter liegen in einem Binding-Paket)
- [AudioKit Flow](https://github.com/AudioKit/Flow), die Vorlage (MIT)
- Die Guides in [`doc/guides`](doc/guides) und die Blog-Posts in
  [`doc/blog`](doc/blog)

## Stand

Vor 1.0 — die API kann sich zwischen Minor-Versionen ändern. Das Repo enthält
nur den Boilerplate-Code eines Flutter-Pakets und seine Versionskonstante.
Schritt S16 baut das aus AudioKit Flow portierte Patch-Modell (Knoten mit
Positionen, typisierte Ports, Verbindungen), die Zeichenfläche, das
Verdrahten, eine Knoten-Palette aus der Registry, einen Adapter an den Graphen
von `aud_audio` und einen Remote-Modus, der über `aud_audio_osc` einen Graphen
auf einem anderen Gerät bearbeitet. Dafür hängt das Paket von `aud_audio` ab.

## Mitwirken

Tickets laufen durch den `gg`-Workflow: siehe den [Develop
Guide](doc/guides/develop-guide.md) und den [Review
Guide](doc/guides/for-ai/ai-review-guide.md).

## Lizenz

MIT — siehe [LICENSE](LICENSE).
