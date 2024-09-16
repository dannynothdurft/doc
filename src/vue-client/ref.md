[zurück](../Readme.md)

# ref()

`ref()` ist eine Funktion in Vue.js, die verwendet wird, um reaktive Referenzen auf primitive Werte oder Objekte zu erstellen. Diese Referenzen ermöglichen es, einfache Werte wie Zahlen oder Strings und komplexe Datenstrukturen wie Objekte oder Arrays reaktiv zu halten, sodass Änderungen an ihnen automatisch von der Vue-Reaktivitätssystem verfolgt werden. `ref()` wird häufig in der Composition API verwendet, um Zustand innerhalb von Komponenten zu verwalten.

## Grundlegende Verwendung

`ref()` wird innerhalb der `setup()`-Funktion einer Vue-Komponente verwendet, um reaktive Daten zu erstellen, die dann in der Template- oder anderen Setup-Funktionen verwendet werden können.

## Beispiel

```html
<template>
  <div>
    <input v-model="message" placeholder="Type something" />
    <p>The message is: {{ message }}</p>
  </div>
</template>

<script>
  import { ref } from "vue";

  export default {
    setup() {
      const message = ref("");
      return { message };
    },
  };
</script>
```

## Erläuterung

- `ref('')`:

  Erstellt eine reaktive Referenz auf einen leeren String. Der Wert innerhalb des `ref`-Objekts kann durch die `.value`-Eigenschaft abgerufen oder geändert werden.

- `v-model="message"`:

  Bindet den Wert des Eingabefeldes an die `message`-Referenz. Wenn der Benutzer in das Eingabefeld schreibt, wird der Wert von `message` automatisch aktualisiert und umgekehrt.

## Dynamische Attribute mit Objekten

`ref()` kann auch verwendet werden, um komplexe Datenstrukturen wie Objekte oder Arrays reaktiv zu halten. Bei der Arbeit mit Objekten oder Arrays muss jedoch beachtet werden, dass der Zugriff auf die Daten über die `.value`-Eigenschaft erfolgt.

`state.value.count++`: Der Wert von `count` innerhalb der `state`-Referenz wird erhöht. Die Änderung wird automatisch in der Benutzeroberfläche reflektiert.

```html
<template>
  <div>
    <button @click="increment">Increment</button>
    <p>Count: {{ state.count }}</p>
  </div>
</template>

<script>
  import { ref } from "vue";

  export default {
    setup() {
      const state = ref({ count: 0 });

      function increment() {
        state.value.count++;
      }

      return { state, increment };
    },
  };
</script>
```

## Sicherheut und Performance

- Sicherheit:

  `ref()` an sich hat keine besonderen Sicherheitsrisiken. Es ist jedoch wichtig, sicherzustellen, dass sensible Daten nicht versehentlich in einer reaktiven Referenz gespeichert werden, die für die Benutzeroberfläche zugänglich ist.

- Performance:

  `ref()` ist effizient, da es nur die reaktive Referenz verwaltet und keine tiefen Reaktivitätsstrukturen erstellt. Beachte, dass bei sehr großen oder komplexen Datenstrukturen die Performance durch die Größe der reaktiven Objekte beeinflusst werden kann. In solchen Fällen kann die gezielte Verwendung von `ref()` und `reactive()` helfen, die Leistung zu optimieren.

## Zusammenfassung

Die Funktion `ref()` in Vue.js ermöglicht die Erstellung von reaktiven Referenzen auf primitive Werte und komplexe Datenstrukturen. Sie wird in der Composition API verwendet, um den Zustand einer Komponente zu verwalten und sicherzustellen, dass Änderungen an den Daten automatisch in der Benutzeroberfläche reflektiert werden. `ref()` ist besonders nützlich für die Verwaltung von Zustand in Vue-Komponenten und bietet eine einfache Möglichkeit, reaktive Daten zu erstellen und zu nutzen.

[zurück](../Readme.md)
