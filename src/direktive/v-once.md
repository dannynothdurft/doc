[zurück](../Readme.md)

# v-once

In Vue.js ist `v-once` eine Direktive, die verwendet wird, um die Wiederholung von DOM-Elementen oder DOM-Inhalten zu verhindern, nachdem sie einmal gerendert wurden. Es ist eine Möglichkeit, die Leistung zu optimieren, indem du den Vue-Rendering-Prozess anweist, ein Element oder einen Block nur einmal zu rendern und ihn dann nicht mehr zu aktualisieren.

## Verwendung von `v-once`

Hier ist eine grundlegende Beschreibung, wie `v-once` verwendet wird und wann es nützlich sein kann:

- Einmalige Rendern:

  `v-once` wird auf ein HTML-Element oder ein Vue-Template angewendet, um sicherzustellen, dass dieses Element oder Template nur einmal gerendert wird. Nach dem ersten Rendern wird das Element nicht mehr aktualisiert, auch wenn sich die zugrunde liegenden Daten ändern.

- Leistungsoptimierung:

  Dies kann die Leistung verbessern, insbesondere bei statischen Inhalten, die sich nicht ändern, da Vue.js den Aufwand für das ständige Überprüfen und Aktualisieren dieser Inhalte reduziert.

## Beispiel

Hier ist ein Beispiel, wie du `v-once` in einer Vue-Komponente verwenden kannst:

```html
<template>
  <div>
    <p v-once>
      Dieser Text wird nur einmal gerendert und nicht mehr aktualisiert.
    </p>
    <p>Aktueller Wert: {{ counter }}</p>
    <button @click="incrementCounter">Erhöhe Wert</button>
  </div>
</template>

<script setup lang="ts">
  export default {
    data() {
      return {
        counter: 0,
      };
    },
    methods: {
      incrementCounter() {
        this.counter += 1;
      },
    },
  };
</script>
```

## Erläuterung

- `v-once` Direktive:

  Die Direktive `v-once` wird hier auf das `<p>`-Tag angewendet, das den statischen Text enthält. Dieser Text wird einmal gerendert und nicht mehr aktualisiert, selbst wenn der counter-Wert sich ändert.

- Dynamischer Inhalt:

  Der zweite `<p>`-Tag zeigt den aktuellen Wert der counter-Variable, der sich beim Klicken auf den Button ändert. Dieser Inhalt wird weiterhin dynamisch aktualisiert, da `v-once` nur auf den statischen Inhalt des ersten `<p>`-Tags angewendet wird.

## Wann `v-once` verwenden?

- Statische Inhalte:

  Verwende `v-once` für Teile der UI, die sich nicht ändern, wie z. B. feste Kopfzeilen, Fußzeilen oder statische Texte.

- Leistungsoptimierung:

  Wenn du weißt, dass bestimmte Teile der Seite nicht aktualisiert werden müssen, kann `v-once` die Renderleistung verbessern.

## Zusammenfassung

`v-once` ist eine nützliche Direktive in Vue.js für das Rendering von statischen Inhalten. Es reduziert den Rendering-Aufwand, indem es sicherstellt, dass bestimmte Teile der Benutzeroberfläche nur einmal gerendert werden und anschließend nicht mehr verändert werden.

[zurück](../Readme.md)
