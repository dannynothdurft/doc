[zurück](../Readme.md)

# v-html

Die `v-html` Direktive in Vue.js wird verwendet, um HTML-Inhalte dynamisch in der Vue-Komponente zu rendern. Sie erlaubt es dir, rohes HTML in deine Vue-Komponente einzufügen, das dann als tatsächliches HTML interpretiert und dargestellt wird.

## Verwendung von `v-html`

Hier ist eine detaillierte Erklärung, wie `v-html` verwendet wird und was du beachten solltest:

- Einfügen von HTML-Inhalten:

  Die `v-html` Direktive wird auf ein HTML-Element angewendet, um den Inhalt dieses Elements mit rohem HTML zu füllen. Der HTML-Code, der in der gebundenen Datenquelle enthalten ist, wird als HTML gerendert und nicht als Text angezeigt.

- Dynamische HTML-Inhalte:

  Du kannst mit `v-html` dynamische HTML-Inhalte einfügen, die möglicherweise von einer API oder einem anderen Datenquellen kommen.

## Beispiel

Hier ist ein Beispiel, das zeigt, wie `v-html` in einer Vue-Komponente verwendet wird:

```html
<template>
  <div>
    <h2>HTML-Inhalt:</h2>
    <div v-html="rawHtml"></div>
    <button @click="updateHtml">Update HTML</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        rawHtml: "<p>Hier ist ein <strong>starker</strong> Text!</p>",
      };
    },
    methods: {
      updateHtml() {
        this.rawHtml = "<p>Der HTML-Inhalt wurde <em>aktualisiert</em>!</p>";
      },
    },
  };
</script>
```

## Erläuterung

- `v-html` Direktive:

  Die `v-html` Direktive wird auf das `<div>`-Element angewendet, um den Inhalt von rawHtml als HTML anzuzeigen. Der HTML-Code in rawHtml wird direkt in das DOM eingefügt.

- Dynamischer Inhalt:

  Der updateHtml-Methode ändert den Inhalt der rawHtml-Datenbindung, wodurch der HTML-Inhalt im `<div>` aktualisiert wird. Beim Klicken auf den Button wird der HTML-Inhalt neu gesetzt, und der Browser rendert den neuen HTML-Code.

## Sicherheitsaspekte

### Cross-Site Scripting (XSS):

- Da `v-html` rohes HTML direkt in die Seite einfügt, ist es wichtig, sicherzustellen, dass der HTML-Inhalt, der eingefügt wird, sicher ist. Unsicherer oder unkontrollierter HTML-Code kann zu [Cross-Site Scripting (XSS)](https://de.wikipedia.org/wiki/Cross-Site-Scripting) Angriffen führen.

- Vermeide es, unsichere Datenquellen direkt in `v-html` einzufügen. Stelle sicher, dass HTML-Inhalte vor dem Einfügen bereinigt werden, wenn sie aus unbekannten oder unsicheren Quellen stammen.

## Wann `v-html` verwenden?

- Dynamischer HTML-Inhalt:

  Verwende `v-html`, wenn du HTML-Inhalte dynamisch ändern oder einfügen musst, die aus einer API, einem Editor oder einer anderen Quelle stammen.

- Rich Text:

  Es ist nützlich für die Anzeige von rich-text-Inhalten, wie sie oft von Content-Management-Systemen (CMS) geliefert werden.

## Zusammenfassung

Die `v-html` Direktive in Vue.js ist ein leistungsfähiges Werkzeug, um HTML-Inhalte dynamisch in deine Komponenten einzufügen. Es ist besonders nützlich für die Arbeit mit rich text und dynamischen Inhalten. Beachte jedoch, dass du bei der Verwendung von `v-html` auf die Sicherheit achten musst, um potenzielle Sicherheitsrisiken wie XSS-Angriffe zu vermeiden.

[zurück](../Readme.md)
