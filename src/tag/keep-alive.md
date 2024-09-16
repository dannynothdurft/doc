[zurück](../Readme.md)

# `<keep-alive>`-Tag

Der `<keep-alive>`-Tag in Vue.js ist ein spezieller Wrapper, der verwendet wird, um dynamische Komponenten zwischen dem Ein- und Ausblenden im Speicher zu behalten, anstatt sie jedes Mal neu zu laden. Dies ist besonders nützlich für die Performance, wenn man oft zwischen verschiedenen Komponenten hin- und herschaltet, da der Zustand der Komponente beibehalten wird.

## 1. Grundlegende Verwendung

Der `<keep-alive>`-Tag umschließt dynamische Komponenten, die beim Wechseln nicht neu gerendert, sondern zwischengespeichert werden sollen.

### Beispiel

```html
<template>
  <div>
    <button @click="currentView = 'home'">Home</button>
    <button @click="currentView = 'profile'">Profile</button>

    <keep-alive>
      <component :is="currentView"></component>
    </keep-alive>
  </div>
</template>

<script>
  import HomeComponent from "./HomeComponent.vue";
  import ProfileComponent from "./ProfileComponent.vue";

  export default {
    data() {
      return {
        currentView: "home",
      };
    },
    components: {
      home: HomeComponent,
      profile: ProfileComponent,
    },
  };
</script>
```

## 2. Erklärung

In diesem Beispiel wird der `<keep-alive>`-Tag um die dynamische Komponente `component` gelegt. Wenn der Nutzer zwischen "Home" und "Profile" wechselt, bleibt der Zustand der inaktiven Komponente (z.B. eingegebene Daten, Scrollposition) erhalten. Das bedeutet, dass die Komponenten nicht neu instanziiert werden, wenn man zwischen ihnen hin und her wechselt.

## 3. Dynamische Attribute mit Objekten

Der `<keep-alive>`-Tag unterstützt auch einige dynamische Attribute, die es ermöglichen, genau zu kontrollieren, welche Komponenten zwischengespeichert werden.

- include:

  Bestimmt, welche Komponenten basierend auf ihren Namen zwischengespeichert werden sollen. Es kann ein String, ein Array oder ein regulärer Ausdruck sein.

- exclude:

  Bestimmt, welche Komponenten von der Zwischenspeicherung ausgeschlossen werden sollen.

- max:

  Definiert die maximale Anzahl an Komponenten, die zwischengespeichert werden sollen. Wenn die Grenze erreicht wird, wird die älteste zwischengespeicherte Komponente entfernt.

```html
<keep-alive include="home,profile" max="2">
  <component :is="currentView"></component>
</keep-alive>
```

## 4. Sicherheit und Performance

- Sicherheit:

  Der `<keep-alive>`-Tag selbst bringt keine direkten Sicherheitsrisiken mit sich, aber es sollte beachtet werden, dass zwischengespeicherte Komponenten ihren Zustand und ihre Daten behalten. Sensible Informationen sollten sicher verwaltet werden, da sie im Speicher verbleiben könnten, solange die Komponente zwischengespeichert ist.

- Performance:

  Der Hauptvorteil von `<keep-alive>` liegt in der Performance. Anstatt Komponenten jedes Mal neu zu erstellen und deren Lifecycle-Hooks erneut auszuführen, bleiben sie im Cache. Dies reduziert die Belastung, insbesondere wenn man zwischen häufig verwendeten Ansichten wechselt. Es sollte jedoch darauf geachtet werden, dass nicht zu viele Komponenten zwischengespeichert werden, um übermäßigen Speicherverbrauch zu vermeiden (mit der Option `max` lässt sich das kontrollieren).

## 5. Zusammenfassung

Der `<keep-alive>`-Tag in Vue.js ist eine leistungsstarke Möglichkeit, die Performance dynamischer Komponenten zu verbessern, indem deren Zustand zwischen dem Ein- und Ausblenden erhalten bleibt. Du kannst festlegen, welche Komponenten zwischengespeichert werden sollen und wie viele, um den Speicherverbrauch zu optimieren. Achte auf mögliche Sicherheitsimplikationen, wenn sensible Daten in zwischengespeicherten Komponenten verbleiben.

[zurück](../Readme.md)
