[zurück](../Readme.md)

# Einfacher Vue-Store

Ein einfacher Vue-Store verwendet die `reactive` und `readonly` APIs von Vue 3, um einen zentralen Zustand zu verwalten. Dies bietet eine weniger komplexe Möglichkeit zur Verwaltung des Zustands im Vergleich zu Vuex und ist ideal für kleinere oder spezifische Anwendungen.

Dieser Ansatz verwendet Vue 3's reaktive System, um einen zentralen Zustand zu erstellen und zu verwalten. Durch die `readonly` Funktion wird der Zustand vor direkten Änderungen von außen geschützt und ermöglicht eine kontrollierte Mutation.

## Grundlegende Verwendung

Der Store wird durch die Erstellung eines reaktiven Zustands mit der `reactive`-Funktion erstellt. Getter und Mutationen werden definiert, um auf den Zustand zuzugreifen und ihn zu ändern. Der Zustand wird dann readonly exportiert, um eine unveränderliche Ansicht des Zustands bereitzustellen.

## Beispiel

```javaScript
import { reactive, readonly } from 'vue';

//Reaktiver Zustand
const state = reactive({
    count: 0
});

//Getter zum Abrufen von Daten
const getters = {
    getCount: () => state.count
};

//Mutationen zum Ändern des Zustands
const mutations = {
    increment() {
        state.count++;
    },
    decrement() {
        state.count--;
    }
};

export default {
    state: readonly(state),
    getters,
    mutations,
};
```

```html
<!-- component -->
<template>
  <div>
    <h1>Count: {{ count }}</h1>
    <button @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
  </div>
</template>

<script>
  import store from "./store"; // Importiere den Store

  export default {
    name: "MyComponent",

    computed: {
      count() {
        return store.getters.getCount();
      },
    },

    methods: {
      increment() {
        store.mutations.increment();
      },
      decrement() {
        store.mutations.decrement();
      },
    },
  };
</script>

<style scoped>
  /* Deine CSS-Styles hier */
</style>
```

## Erläuterung

- `state`:

  Der zentrale Zustand, der durch die `reactive`-Funktion erstellt wird. Dieser Zustand ist reaktiv und wird automatisch in den Vue-Komponenten reflektiert, wenn sich die Daten ändern.

- `getters`:

  Funktionen, die auf den Zustand zugreifen und abgeleitete Daten bereitstellen. Sie helfen dabei, den Zustand zu verarbeiten, ohne ihn direkt zu ändern.

- `mutations`:

  Funktionen, die den Zustand ändern. Sie sind synchron und ermöglichen eine klare und nachvollziehbare Änderung des Zustands.

- `readonly(state)`:

  Macht den Zustand von außen unveränderlich, sodass er nur durch definierte Mutationen geändert werden kann. Dies hilft, die Integrität des Zustands zu bewahren.

## Dynamische Attribute mit Objekten

Der einfache Vue-Store ermöglicht es, Attribute und Datenstrukturen dynamisch hinzuzufügen, indem die Mutationen entsprechend angepasst werden. Dies bietet Flexibilität beim Umgang mit unterschiedlichen Datenanforderungen.

## Sicherheut und Performance

- Sicherheit:

  Durch die Verwendung von `readonly` wird sichergestellt, dass der Zustand nur durch die definierten Mutationen geändert werden kann. Dies schützt vor unkontrollierten Änderungen und bewahrt die Konsistenz.

- Performance:

  Vue’s reaktive System sorgt dafür, dass nur die Teile der Anwendung neu gerendert werden, die von Änderungen betroffen sind. Dies sorgt für gute Performance selbst bei komplexeren Anwendungen.

## Zusammenfassung

Der einfache Vue-Store bietet eine unkomplizierte Möglichkeit zur Verwaltung des Zustands in Vue-Anwendungen, indem er Vue 3’s reaktive APIs verwendet. Er eignet sich gut für kleinere Projekte oder spezielle Anwendungsfälle, bei denen eine vollständige Vuex-Implementierung möglicherweise überdimensioniert wäre.

[zurück](../Readme.md)
