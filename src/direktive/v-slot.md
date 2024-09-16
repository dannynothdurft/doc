[zurück](../Readme.md)

# v-slot

`v-slot` ist eine Direktive in Vue.js, die verwendet wird, um benannte Slots in Komponenten zu definieren und zu nutzen. Sie ermöglicht eine präzise Steuerung darüber, wie Inhalte in Slots eingefügt werden, und bietet mehr Flexibilität beim Umgang mit komplexeren Komponentenstrukturen. `v-slot` ersetzt die vorherige `slot`-Syntax in Vue.js und unterstützt auch Scoped Slots, die es ermöglichen, Daten zwischen der Kind- und Elternkomponente auszutauschen.

## Grundlegende Verwendung von `v-slot`

`v-slot` wird verwendet, um benannte oder standardmäßige Slots in einer Vue-Komponente zu binden und Inhalte in diese Slots einzufügen. Diese Direktive erlaubt es Ihnen, spezifische Slots durch Namen zu identifizieren und Inhalte dynamisch zu steuern.

## Beispiel

```html
<!-- ChildComponent.vue -->
<template>
  <div>
    <header>
      <slot name="header"></slot>
      <!-- Benannter Slot -->
    </header>
    <main>
      <slot></slot>
      <!-- Standard Slot -->
    </main>
    <footer>
      <slot name="footer"></slot>
      <!-- Benannter Slot -->
    </footer>
  </div>
</template>

<!-- ParentComponent.vue -->
<template>
  <ChildComponent>
    <template v-slot:header>
      <h1>Header-Inhalt</h1>
    </template>

    <p>Hauptinhalt</p>

    <template v-slot:footer>
      <p>Footer-Inhalt</p>
    </template>
  </ChildComponent>
</template>
```

## Erläuterung

- `<slot name="header"></slot>`:

  Definiert einen benannten Slot, der mit `v-slot`:header in der Elternkomponente gefüllt wird.

- `<slot></slot>`:

  Definiert einen Standard-Slot, der mit `v-slot` ohne Namen in der Elternkomponente gefüllt wird.

- `v-slot:header`:

  Die Syntax, um Inhalte in einen benannten Slot einzufügen. Es ersetzt die frühere `slot="header"`-Syntax.

## Kurzeschreibweise

`#header` ist die Kurzschreibweise für `v-slot:header`.

Es gibt an, dass der Inhalt für den Slot mit dem Namen header bereitgestellt wird.

## Dynamische Attribute mit Objekten

`v-slot` unterstützt auch die Bindung von Slot-Props, die es ermöglichen, Daten an den Slot weiterzugeben:

```html
<!-- ChildComponent.vue -->
<template>
  <div>
    <slot v-bind="slotProps"></slot>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        slotProps: {
          message: "Hallo aus der Kindkomponente",
        },
      };
    },
  };
</script>

<!-- ParentComponent.vue -->
<template>
  <ChildComponent>
    <template v-slot:default="slotProps">
      <p>{{ slotProps.message }}</p>
    </template>
  </ChildComponent>
</template>
```

In diesem Beispiel werden die Daten aus `slotProps` der ChildComponent an den Slot in der ParentComponent weitergegeben.

## Sicherheit und Performance

- Sicherheit:

  Die Verwendung von `v-slot` ist sicher, da sie nur die Inhalte rendern, die explizit in den Slots definiert sind. Es gibt keine inhärenten Sicherheitsrisiken, solange die Daten, die in Slots eingefügt werden, vertrauenswürdig sind.

- Performance:

  `v-slot` kann die Performance beeinflussen, wenn viele Slots oder komplexe Slot-Strukturen verwendet werden. Es ist wichtig, die Komponentenstruktur übersichtlich zu halten und unnötige Slots zu vermeiden, um die Rendering-Leistung zu optimieren.

## Zusammenfassung

- Verwendung:

  `v-slot` ermöglicht die Definition und Nutzung von benannten und Standard-Slots in Vue-Komponenten.

- Benannte und Standard-Slots:

  Erlauben die präzise Platzierung und Kontrolle von Inhalten.

- Dynamische Attribute:

  Können durch `v-bind` auf Slots angewendet werden, um zusätzliche Daten weiterzugeben.

- Sicherheit und Performance:

  `v-slot` ist sicher, aber komplexe Slot-Strukturen sollten effizient gestaltet werden, um die Performance zu optimieren.

[zurück](../Readme.md)
