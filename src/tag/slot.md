[zurück](../Readme.md)

# `<slot>`-Tag

## 1. Grundlegende Verwendung

Der `<slot>`-Tag in Vue.js wird verwendet, um Platzhalter für Inhalte in Komponenten zu definieren. Mit Slots können Sie flexible und wiederverwendbare Komponenten erstellen, bei denen bestimmte Teile des Inhalts von außen bereitgestellt werden können.

### Beispiel

```html
<!-- ParentComponent.vue -->
<template>
  <div>
    <ChildComponent>
      <p>Dies ist der Inhalt, der in den Slot eingefügt wird.</p>
    </ChildComponent>
  </div>
</template>

<!-- ChildComponent.vue -->
<template>
  <div>
    <header>Header der Kindkomponente</header>
    <slot><!-- Hier wird der Inhalt des Elternteils eingefügt --></slot>
    <footer>Footer der Kindkomponente</footer>
  </div>
</template>
```

## 2. Erklärung

- `<slot></slot>`:

  Platzhalter, der den Inhalt anzeigt, der von der Elternkomponente in den Slot eingefügt wird. In dem Beispiel oben wird der <p>-Tag im ParentComponent in den <slot> des ChildComponent eingefügt.

- Namensgebende Slots:

  Man kann mehrere Slots definieren und ihnen Namen geben, um gezielt Inhalte zu platzieren.

  Zum Beispiel:

  ```html
  <!-- ChildComponent.vue -->

  <template>
    <div>
      <header>
        <slot name="header"></slot>
      </header>
      <main>
        <slot></slot>
      </main>
      <footer>
        <slot name="footer"></slot>
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

weiter infos zu [v-slot](../direktive/v-slot.md)

[zurück](../Readme.md)
