[zurück](../Readme.md)

# v-for

Die `v-for`-Direktive in Vue.js ermöglicht es, über eine Liste von Daten zu iterieren und dynamisch Elemente im DOM zu rendern. Sie wird verwendet, um eine Liste von wiederholten DOM-Elementen zu erzeugen, indem sie über Arrays oder Objekte läuft und für jedes Element in der Liste eine Instanz eines HTML-Elements erstellt.

## Grundlegende Verwendung von `v-for`

Die grundlegende Verwendung von `v-for` folgt dem Format:

`<li v-for="item in items" :key="item.id">{{ item.name }}</li>`

- `item`: Die Variable, die auf das aktuelle Element in der Schleife verweist.
- `items`: Das Array oder Objekt, über das iteriert wird.
- `:key`: Eine eindeutige Identifizierung für jedes gerenderte Element, was für die Effizienz beim Aktualisieren des DOMs wichtig ist.

## Beispiel

Angenommen, wir haben eine Liste von Aufgaben, die angezeigt werden soll:
In diesem Beispiel wird für jede Aufgabe im Array tasks ein <li>-Element erstellt, das den Titel der Aufgabe enthält.

```html
<template>
  <ul>
    <li v-for="task in tasks" :key="task.id">{{ task.title }}</li>
  </ul>
</template>

<script>
  export default {
    data() {
      tasks: [
        { id: 1, title: "Aufgabe 1" },
        { id: 2, title: "Aufgabe 2" },
        { id: 3, title: "Aufgabe 3" },
      ];
    },
    methods: {
      handleClick() {
        alert("Button geklickt!");
      },
    },
  };
</script>
```

## Erläuterung

Die `v-for`-Direktive wird verwendet, um über Arrays, Objekte oder auch Zahlen zu iterieren:

- Array-Iteration:

  `v-for` durchläuft Arrays und erstellt für jedes Element eine Instanz eines HTML-Tags.

- Objekt-Iteration:

  Du kannst auch über die Schlüssel und Werte eines Objekts iterieren:

  ```html
  <div v-for="(value, key) in object" :key="key">{{ key }}: {{ value }}</div>
  ```

  Hier kannst du sowohl auf den Schlüssel als auch auf den Wert des Objekts zugreifen.

- teration mit Index:

  Du kannst zusätzlich zum aktuellen Element auf den Index zugreifen:

  ```html
  <li v-for="(item, index) in items" :key="index">
    {{ index }} - {{ item.name }}
  </li>
  ```

## Sicherheut und Performance

- `key`-Attribut:

  Die Verwendung des `key`-Attributs ist wichtig, wenn du mit dynamischen Listen arbeitest. Es hilft Vue, Elemente effizient zu aktualisieren, indem es die Unterschiede zwischen den einzelnen Elementen erkennt, statt die gesamte Liste neu zu rendern. Das verbessert die Performance erheblich, besonders bei großen Listen.

- Reihenfolge beachten:

  Da Vue das DOM auf effiziente Weise aktualisiert, kann es vorkommen, dass bei Änderungen an der Reihenfolge von Listen unerwartete Ergebnisse auftreten, wenn das `key`-Attribut fehlt oder nicht eindeutig ist. Ohne eindeutige `keys` kann Vue nicht richtig erkennen, welches Element geändert wurde.

## Zusammenfassung

Die `v-for`-Direktive ist eine der mächtigsten Funktionen von Vue.js, die es ermöglicht, dynamisch über Arrays oder Objekte zu iterieren und wiederholte DOM-Elemente zu generieren. Durch das Hinzufügen des `key`-Attributs kann die Performance optimiert werden. Ob du über Arrays von Elementen oder Objekte iterierst, `v-for` bietet eine flexible und einfache Möglichkeit, Daten zu visualisieren.

[zurück](../Readme.md)
