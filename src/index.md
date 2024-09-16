# Vue.js

Vue.js ist ein progressives JavaScript-Framework für den Aufbau von Benutzeroberflächen. Es ist besonders gut für den Aufbau von Single-Page-Anwendungen geeignet. Vue ist so konzipiert, dass es schrittweise eingeführt werden kann, was bedeutet, dass du es in bestehenden Projekten verwenden kannst, ohne das gesamte Projekt umstellen zu müssen. Die Hauptmerkmale von Vue.js sind:

- Reaktive Datenbindung: Vue.js sorgt dafür, dass das Modell und die Ansicht synchron bleiben. Änderungen an den Daten im Modell spiegeln sich automatisch in der Ansicht wider und umgekehrt.

- Komponentenbasierter Aufbau: Vue-Anwendungen bestehen aus wiederverwendbaren Komponenten, die ihre eigene Logik und ihr eigenes Styling enthalten.

- Einfaches Lernen: Die API von Vue.js ist einfach und intuitiv, was es zu einer ausgezeichneten Wahl für Entwickler macht, die neu im Bereich der Frontend-Entwicklung sind.

Verwendung: Um Vue.js in deinem Projekt zu verwenden, fügst du es entweder über ein CDN in deinem HTML-Dokument ein oder installierst es über npm/yarn, wenn du ein Build-Tool wie Webpack verwendest. Danach kannst du Vue-Komponenten erstellen und in deine Anwendung integrieren.

[Vue.js Dokumentation](https://vuejs.org/guide/quick-start.html)

## Tag

Ein Tag in Vue.js bezeichnet ein grundlegendes Element, das zur Strukturierung und Darstellung von Inhalten verwendet wird. Tags bestehen aus einem Start- und einem Endtag und können optional Attribute enthalten, um zusätzliche Informationen oder Eigenschaften zu definieren. Sie sind die Bausteine einer HTML-Dokumentstruktur und spielen eine wichtige Rolle in der Definition von Komponenten und deren Verhalten in Vue.js.

- [`<component>`](./tag/component.md)
- [`<keep-alive>`](./tag/keep-alive.md)
- [`<slot>`](./tag/slot.md)
- [`<transition>`](./tag/transition.md)

## Interpolation

Interpolation in Vue.js ist eine Methode, um Daten in den HTML-Code einzufügen. Dies erfolgt durch die Verwendung von doppelten geschweiften Klammern `{{ }}`. Vue.js ersetzt diese Platzhalter mit dem Wert der entsprechenden Datenquelle, die in der Vue-Instanz definiert ist.

- [`{{ }}`](./interpolation/{{}}.md)

## Direktives

Direktiven sind spezielle Attribute in Vue.js, die das Verhalten von HTML-Elementen steuern. Direktiven beginnen mit dem Präfix v- und weisen Vue an, wie es das DOM (Document Object Model) aktualisieren soll, wenn sich die zugrunde liegenden Daten ändern.

- [`v-bind`](./direktive/v-bind.md)
- [`v-for`](./direktive/v-for.md)
- [`v-html`](./direktive/v-html.md)
- [`v-if`](./direktive/v-if.md)
- [`v-model`](./direktive/v-model.md)
- [`v-on`](./direktive/v-on.md)
- [`v-once`](./direktive/v-once.md)
- [`v-pre`](./direktive/v-pre.md)
- [`v-show`](./direktive/v-show.md)
- [`v-slot`](./direktive/v-slot.md)

## Komponentenkommunikation

Die Komponentenkommunikation in Vue.js ermöglicht den Austausch von Daten zwischen Eltern- und Kindkomponenten. Durch Mechanismen wie Props, Events und Slots können Komponenten miteinander interagieren und Informationen teilen. Dies erleichtert die Modularisierung und Wiederverwendbarkeit von Komponenten, indem sie voneinander getrennt und nur über definierte Schnittstellen kommunizieren.

- [`props`](./komponentenkommunikation/props.md)
- [`store`](./komponentenkommunikation/store.md)

## Vue Client

Der Vue Client bezieht sich auf das grundlegende Vue-API, das direkt in einer Vue-Anwendung verfügbar ist. Es umfasst verschiedene Funktionen, Methoden und Hilfsmittel, die zum Erstellen und Verwalten von reaktiven Daten, Komponenten und der App-Struktur verwendet werden. Zu den häufig verwendeten Funktionen gehören unter anderem `ref()`, `reactive()`, `computed()`, und `watch()`, die zur Verwaltung von Zuständen und Reaktivität innerhalb einer Vue-Komponente dienen.

- [`ref`](./vue-client/ref.md)

## Grober aufbau component

```html
<template>
  <div>
    <!-- Beispielinhalt, der Props verwendet -->
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
    <button @click="showAlert">{{ buttonText }}</button>
  </div>
</template>

<script>
  export default {
    name: "MyComponent", // Name der Komponente

    // Props, die von der Elternkomponente übergeben werden
    props: {
      title: {
        type: String,
        default: "Default Title",
      },
      description: {
        type: String,
        default: "Default description.",
      },
      buttonText: {
        type: String,
        default: "Click Me",
      },
    },

    // Daten, die in der Komponente verwendet werden
    data() {
      return {
        message: "Hello World",
      };
    },

    // Methoden für die Komponente
    methods: {
      // Methode zum Anzeigen einer Nachricht
      showAlert() {
        alert(this.message);
      },
    },

    // Computed Properties, falls benötigt
    computed: {
      // Beispiel für eine berechnete Eigenschaft
      uppercaseDescription() {
        return this.description.toUpperCase();
      },
    },

    // Lebenszyklus-Hooks, falls benötigt
    mounted() {
      console.log("Component mounted!");
    },
  };
</script>

<style scoped>
  /* Deine CSS-Styles hier */
  div {
    font-family: Arial, sans-serif;
    color: #333;
  }

  button {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
  }

  button:hover {
    background-color: #0056b3;
  }
</style>
```
