[zurück](../Readme.md)

# v-model

Das `v-model`-Directive in Vue.js wird verwendet, um eine Zwei-Wege-Datenbindung zwischen einem Formular-Element (z.B. `input`, `textarea`, `select`) und einer Komponente herzustellen. Mit `v-model` kannst du Änderungen im Formular direkt im Datenmodell speichern und umgekehrt das Modell in der Benutzeroberfläche aktualisieren, wenn sich die Daten ändern.

## Grundlegende Verwendung

`v-model` bindet den Wert eines Formularfeldes an eine Datenvariable und aktualisiert diese automatisch, wenn der Benutzer eine Änderung vornimmt.

## Beispiel

```html
<template>
  <div>
    <input v-model="message" placeholder="Type something" />
    <p>Deine Nachricht: {{ message }}</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        message: "",
      };
    },
  };
</script>
```

## Erläuterung

- `v-model="message"`:

  Verknüpft das `input`-Element mit der Datenvariable `message`. Jedes Mal, wenn der Benutzer in das Eingabefeld schreibt, wird der Wert von `message` automatisch aktualisiert.

- Datenbindung:

  Diese Zwei-Wege-Datenbindung bedeutet, dass Änderungen am Eingabefeld den Wert der `message`-Variable im Vue-Datenobjekt ändern, und umgekehrt, wenn `message` in der Datenstruktur geändert wird, spiegelt sich diese Änderung im Eingabefeld wider.

## Dynamische Attribute mit Objekten

`v-model` unterstützt die Verwendung von unterschiedlichen Formular-Elementen wie Checkboxen, Radiobuttons und Select-Optionen. Je nach Element-Typ ändert sich das Verhalten von `v-model`.

```html
<template>
  <div>
    <input type="checkbox" v-model="checked" />
    <p>Checkbox ist {{ checked ? 'ausgewählt' : 'nicht ausgewählt' }}.</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        checked: false,
      };
    },
  };
</script>
```

Checkbox: Wenn die Checkbox aktiviert ist, wird der Wert `true` in der Variablen `checked` gespeichert, andernfalls `false`.

```html
<template>
  <div>
    <select v-model="selected">
      <option disabled value="">Wähle eine Option</option>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>
    <p>Ausgewählt: {{ selected }}</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        selected: "",
      };
    },
  };
</script>
```

Select: Die ausgewählte Option wird automatisch in der `selected`-Variable gespeichert.

`v-model` mit benutzerdefinierten Komponenten

`v-model` kann auch in benutzerdefinierten Komponenten verwendet werden, indem du das `model`-Directive oder die `props` und `events` innerhalb der Komponente definierst.

```html
<template>
  <div>
    <custom-input v-model="customMessage"></custom-input>
    <p>Benutzerdefinierte Nachricht: {{ customMessage }}</p>
  </div>
</template>

<script>
  import CustomInput from "./CustomInput.vue";

  export default {
    components: {
      CustomInput,
    },
    data() {
      return {
        customMessage: "",
      };
    },
  };
</script>
```

Die benutzerdefinierte Komponente `CustomInput` könnte so aussehen:

```html
<template>
  <input :value="value" @input="$emit('input', $event.target.value)" />
</template>

<script>
  export default {
    props: ["value"],
  };
</script>
```

## Sicherheut und Performance

- Sicherheit:

  Da `v-model` direkt mit Benutzereingaben arbeitet, solltest du sicherstellen, dass alle Eingaben validiert und gegebenenfalls bereinigt werden, insbesondere wenn sie an einen Server gesendet werden. Die Validierung von Formularen kann mithilfe von Ereignissen wie `@input` oder einer Vue-Form-Bibliothek (z.B. Vuelidate) umgesetzt werden.

- Performance:

  `v-model` ist für gewöhnliche Formulare sehr effizient. Für komplexere Formularfelder, die häufig gerendert werden oder rechenintensive Operationen enthalten, kannst du bei Performanceproblemen über „debounced“ oder „lazy“ Updates nachdenken, um die Anzahl der Änderungen zu reduzieren. Mit `v-model.lazy` wird der Wert z.B. erst nach dem Verlassen des Eingabefelds (`blur`-Event) aktualisiert.

```html
<input
  v-model.lazy="message"
  placeholder="Wert wird erst nach Verlassen aktualisiert"
/>
```

## Zusammenfassung

Das `v-model`-Directive in Vue.js ist eine einfache und leistungsstarke Möglichkeit, eine Zwei-Wege-Datenbindung zwischen einem Formularfeld und der Datenstruktur herzustellen. Es unterstützt verschiedene Eingabeelemente wie Textfelder, Checkboxen, Radiobuttons und Selects sowie benutzerdefinierte Komponenten. `v-model` sorgt für eine nahtlose Interaktion zwischen der Benutzeroberfläche und den Daten und erleichtert die Verwaltung von Formulareingaben in Vue-Anwendungen.

[zurück](../Readme.md)
