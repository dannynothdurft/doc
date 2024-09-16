[zurück](../Readme.md)

# `<transition>`-Tag

Der `<transition>`-Tag in Vue.js dient dazu, Übergänge (Animationen) für das Ein- und Ausblenden von HTML-Elementen oder Komponenten zu definieren. Vue.js bietet dabei eine einfache Möglichkeit, CSS-Animationen oder JavaScript-Hooks zu verwenden, um das Benutzererlebnis zu verbessern.

## 1. Grundlegende Verwendung

Der `<transition>`-Tag wird um ein einzelnes Element oder eine Komponente gelegt, das bzw. die beim Ein- oder Austritt animiert werden soll.

### Beispiel

```html
<template>
  <div>
    <button @click="show = !show">Toggle Box</button>
    <transition name="fade">
      <div v-if="show" class="box">Ich bin animiert!</div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false
    };
  }
}
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <=2.1.8 */ {
  opacity: 0;
}
</style>

</script>
```

## 2. Erklärung

- `<transition>`-Tag:

  Umhüllt das Element oder die Komponente, die animiert werden soll.

- `name="fade"`:

  Bestimmt den Namenspräfix für die CSS-Klassen, die während des Übergangs verwendet werden. Hierdurch wird automatisch ein Set von CSS-Klassen für den Übergang generiert (z. B. `.fade-enter`, `.fade-leave-to`, `.fade-enter-active`).

- CSS-Klassen:

  Vue.js verwendet vordefinierte Namenskonventionen für die CSS-Klassen:

  - `*-enter`: Zustand beim Eintritt, bevor die Animation startet.
  - `*-enter-active`: Aktive Animation beim Eintritt.
  - `*-leave`: Zustand beim Austritt, bevor die Animation startet.
  - `*-leave-active`: Aktive Animation beim Austritt.

## 3. Dynamische Attribute mit Objekten

Du kannst auch JavaScript-Animationen nutzen, indem du Transition-Hooks in den `<transition>`-Tag einfügst. Hier ist ein Beispiel für dynamische Übergänge, die mit JavaScript gesteuert werden:

```html
<template>
  <div>
    <button @click="toggle">Toggle Box</button>
    <transition @before-enter="beforeEnter" @enter="enter" @leave="leave">
      <div v-if="show" class="box">Ich bin animiert!</div>
    </transition>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        show: false,
      };
    },
    methods: {
      toggle() {
        this.show = !this.show;
      },
      beforeEnter(el) {
        el.style.opacity = 0;
      },
      enter(el, done) {
        // Transition in JavaScript
        setTimeout(() => {
          el.style.transition = "opacity 0.5s";
          el.style.opacity = 1;
          done();
        }, 100);
      },
      leave(el, done) {
        el.style.opacity = 1;
        setTimeout(() => {
          el.style.transition = "opacity 0.5s";
          el.style.opacity = 0;
          done();
        }, 100);
      },
    },
  };
</script>
```

## 4. Sicherheit und Performance

- Sicherheit:

  Der `<transition>`-Tag selbst hat keine Sicherheitsrisiken, aber es ist wichtig, sicherzustellen, dass Animationen oder JS-Hooks keine sensible Datenmanipulation zulassen. Verwende geprüfte CSS-Animationen und achte darauf, dass dynamische Transitionen keine Sicherheitslücken (z.B. durch Cross-Site Scripting) erzeugen.

- Performance:

  Animationen können die Performance beeinflussen, insbesondere auf mobilen Geräten. Verwende einfache und effiziente Animationen, die hardwarebeschleunigt sind (z.B. `transform` oder `opacity`), um die Ausführung zu optimieren. Verwende `<transition-group>` für animierte Listen, um die Performance bei mehreren Elementen zu verbessern.

## 5. Zusammenfassung

Der `<transition>`-Tag von Vue.js ermöglicht das einfache Hinzufügen von Animationen für das Ein- und Ausblenden von HTML-Elementen oder Komponenten. Es gibt sowohl Unterstützung für CSS-Animationen als auch JavaScript-basierte Übergänge. Sicherheit und Performance sollten bei umfangreichen Animationen und dynamischen Inhalten beachtet werden.

[zurück](../Readme.md)
