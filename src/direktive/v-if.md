[zurück](../Readme.md)

# v-if / v-else-if / v-else

In Vue.js werden die Anweisungen `v-if`, `v-else-if` und `v-else` verwendet, um bedingt Inhalte oder Komponenten basierend auf bestimmten Bedingungen anzuzeigen oder auszublenden. Sie ermöglichen eine einfache, logische Struktur innerhalb von Templates, ähnlich wie klassische `if-else`-Bedingungen in Programmiersprachen.

## Grundlegende Verwendung

- `v-if`: Rendert das Element nur, wenn die angegebene Bedingung `true` ist.
- `v-else-if`: Optionaler Block, der als nächstes evaluiert wird, wenn die `v-if`-Bedingung `false` ist.
- `v-else`: Fängt den Fall auf, wenn keine der vorherigen Bedingungen zutrifft.

## Beispiel

```html
<template>
  <div>
    <button @click="view = 'home'">Home</button>
    <button @click="view = 'profile'">Profile</button>
    <button @click="view = 'settings'">Settings</button>

    <div v-if="view === 'home'">
      <h1>Home Page</h1>
    </div>
    <div v-else-if="view === 'profile'">
      <h1>Profile Page</h1>
    </div>
    <div v-else>
      <h1>Settings Page</h1>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        view: "home",
      };
    },
  };
</script>
```

## Erläuterung

- `v-if="view === 'home'"`:

  Zeigt den Inhalt nur an, wenn `view` den Wert `'home'` hat.

- `v-else-if="view === 'profile'"`:

  Wird evaluiert, wenn `v-if` `false` ergibt. Zeigt den Inhalt an, wenn `view` den Wert `'profile'` hat.

- `v-else`:

  Fängt alle anderen Fälle ab. In diesem Beispiel zeigt es die "Settings Page" an, wenn `view` weder `'home'` noch `'profile'` ist.

## Dynamische Attribute mit Objekten

Es ist auch möglich, komplexere Bedingungen in den `v-if`- und `v-else-if`-Blöcken zu verwenden, wie z. B. eine Kombination aus Bedingungen und dynamischen Werten.

```html
<template>
  <div>
    <input type="text" v-model="username" placeholder="Enter your name" />
    <div v-if="username === 'admin'">
      <p>Welcome, Admin!</p>
    </div>
    <div v-else-if="username">
      <p>Welcome, {{ username }}!</p>
    </div>
    <div v-else>
      <p>Please enter your name.</p>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        username: "",
      };
    },
  };
</script>
```

In diesem Fall zeigt die Anwendung eine personalisierte Nachricht an, wenn der Benutzer etwas in das Textfeld eingibt, und eine spezielle Nachricht, wenn der Benutzername `'admin'` ist.

## Sicherheut und Performance

- Sicherheit:

  Es gibt keine speziellen Sicherheitsrisiken bei der Verwendung von `v-if`, `v-else-if` und `v-else`. Beachte jedoch, dass Bedingungen von dynamischen Daten abhängig sind. Stelle sicher, dass diese Daten sicher und korrekt sind, um unerwartetes Verhalten zu vermeiden.

- Performance:

  `v-if` entfernt und erstellt DOM-Elemente basierend auf der Bedingung, was je nach Häufigkeit und Komplexität Auswirkungen auf die Performance haben kann. Für einfache Sichtbarkeitswechsel ist es effizienter, `v-show` zu verwenden, da es nur die CSS-Eigenschaft `display` ein- oder ausschaltet, ohne das Element aus dem DOM zu entfernen. `v-if` ist besser, wenn Elemente nur bei Bedarf gerendert werden sollen.

## Zusammenfassung

Die Anweisungen `v-if`, `v-else-if` und `v-else` in Vue.js bieten eine mächtige Möglichkeit, Inhalte bedingt zu rendern. Sie eignen sich gut für logische Abfolgen, bei denen verschiedene Bedingungen evaluiert werden sollen. Während `v-if` Inhalte komplett aus dem DOM entfernt, ist bei häufigen Sichtbarkeitsänderungen `v-show` eine bessere Alternative zur Performanceoptimierung.

Mehr zu [`v-show`](./v-show.md)

[zurück](../Readme.md)
