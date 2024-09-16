[zurück](../Readme.md)

# v-show

Das `v-show`-Directive in Vue.js dient dazu, Elemente basierend auf einer Bedingung anzuzeigen oder auszublenden. Im Gegensatz zu `v-if`, das Elemente komplett aus dem DOM entfernt, ändert `v-show` nur die CSS-Eigenschaft `display`, um Elemente ein- oder auszublenden. Dies ist besonders nützlich, wenn du Elemente häufig und schnell sichtbar machen oder verstecken willst, ohne sie jedes Mal neu zu rendern.

## Grundlegende Verwendung

- `v-show`:

  Steuert die Sichtbarkeit eines Elements basierend auf dem Wert einer Bedingung. Wenn die Bedingung `true` ist, wird das Element angezeigt, andernfalls bleibt es im DOM, wird aber nicht gerendert (es wird mit `display: none` ausgeblendet).

## Beispiel

```html
<template>
  <div>
    <button @click="showBox = !showBox">Toggle Box</button>
    <div v-show="showBox" class="box">
      Ich werde nur ein- oder ausgeblendet, aber nicht entfernt!
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        showBox: true,
      };
    },
  };
</script>

<style>
  .box {
    width: 100px;
    height: 100px;
    background-color: lightblue;
  }
</style>
```

## Erläuterung

- `v-show="showBox"`:

  Das `div`-Element mit der Klasse `box` wird angezeigt, solange `showBox` `true` ist. Wenn `showBox` `false` ist, bleibt das Element im DOM, wird aber durch `display: none` ausgeblendet.

- Unterschied zu `v-if`:

  Bei `v-show` bleibt das Element immer im DOM und seine Sichtbarkeit wird nur durch CSS gesteuert. Bei `v-if` wird das Element aus dem DOM entfernt, wenn die Bedingung `false` ist.

## Dynamische Attribute mit Objekten

Wie bei anderen Vue.js-Direktiven können auch bei `v-show` dynamische Werte verwendet werden, um komplexere Logik zur Steuerung der Sichtbarkeit zu implementieren. Du kannst auch direkt mit Methoden und berechneten Eigenschaften arbeiten.

```html
<template>
  <div>
    <input type="text" v-model="username" placeholder="Enter your name" />
    <p v-show="isAdmin">You have admin privileges!</p>
    <p v-show="!isAdmin">Welcome, {{ username }}!</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        username: "",
      };
    },
    computed: {
      isAdmin() {
        return this.username === "admin";
      },
    },
  };
</script>
```

In diesem Beispiel steuert die `isAdmin`-berechnete Eigenschaft, ob die spezielle Nachricht für Administratoren angezeigt wird.

## Sicherheut und Performance

- Sicherheit:

  Da das Element bei `v-show` im DOM verbleibt, kann es theoretisch weiterhin von außen (z.B. durch Developer-Tools) gesehen oder manipuliert werden. Es ist wichtig, keine sicherheitskritischen Informationen einfach nur durch `v-show` zu verstecken. Falls Daten wirklich geschützt werden sollen, sollten sie aus dem DOM entfernt oder auf der Serverseite kontrolliert werden.

- Performance:

  `v-show` ist performanter als `v-if` bei häufigen Sichtbarkeitsänderungen, da das Element nicht ständig hinzugefügt oder entfernt wird. Für den ersten Renderdurchlauf kann `v-if` effizienter sein, da es unnötiges Rendering vermeidet, wenn die Bedingung `false` ist. Wenn das Element jedoch häufig angezeigt und versteckt werden muss, sollte `v-show` bevorzugt werden, da nur die CSS-Eigenschaft `display` geändert wird.

## Zusammenfassung

Das `v-show`-Directive in Vue.js ist ideal, wenn du die Sichtbarkeit von Elementen dynamisch steuern willst, ohne sie aus dem DOM zu entfernen. Es ändert lediglich die CSS-Eigenschaft `display`, was es schneller und effizienter macht als `v-if`, insbesondere wenn Elemente oft ein- und ausgeblendet werden müssen. Für sensible Daten solltest du jedoch Vorsicht walten lassen, da `v-show` das Element im DOM behält.

Mehr zu [`v-if`](./v-if.md)

[zurück](../Readme.md)
