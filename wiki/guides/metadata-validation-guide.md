---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# Handbuch zur Metadatenvalidierung

Um die korrekte Formatierung von Metadaten in MD-Dateien sicherzustellen, haben wir einen Metadaten-Validierungstest durchgeführt. Dieses Dokument enthält Richtlinien, die Beitragende dabei unterstützen, einige der häufigsten Metadaten-Validierungsfehler zu vermeiden.

**Beispiel für Metadaten:**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## Häufige Validierungsfehler und wie diese vermieden/behoben werden

Im Folgenden finden Sie einige der häufigsten Szenarien, in denen Fehler bei der Metadatenvalidierung auftreten.

### Doppelpunkt in Metadaten

Ein Validierungsfehler tritt auf, wenn entweder der Titel oder die Titel oder beide Doppelpunkte aufweisen.

**Beispiel:**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

Um diesen Fehler zu vermeiden, schließen Sie den Titel oder die Beschriftungen (oder beide, wenn beide über Doppelpunkte verfügen) in **einfache Anführungszeichen**.

**Beispiel:**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### Doppelpunkt und einfaches Anführungszeichen oder Apostroph in Metadaten

Die vorherige Lösung funktioniert nicht, wenn der Titel oder die Titel Doppelpunkte, einfache Anführungszeichen oder Apostrophe enthalten.

**Beispiel:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

Dieser Fehler wird behoben, indem der Titel oder die Beschriftungen (oder beide) in **Doppelte Anführungszeichen**.

**Beispiel:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### Doppelpunkt, doppeltes Anführungszeichen und einfaches Anführungszeichen oder Apostroph in Metadaten

**Beispiel:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

In diesem Fall können Sie den Titel oder die Beschriftungen (oder beides) in **Doppelte Anführungszeichen** und verwenden Sie eine **umgekehrter Schrägstrich** um alle doppelten Anführungszeichen in Titel und Titel zu maskieren.

**Beispiel:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### Fehlende Felder in Metadaten

Ein Validierungsfehler tritt auf, wenn das Feld für Titel oder Titel in den Metadaten fehlt.

**Beispiel:**

```markdown
---
title: This is a title
---
```

ODER

```markdown
---
labels: article,labels,tags
---
```

Um diesen Fehler zu vermeiden, schließen Sie beide Felder in die Metadaten ein.

Das Feld Titel kann leer gelassen werden und führt nicht zu einem Fehler, aber das Feld Titel muss ausgefüllt werden.

**Beispiel:**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
