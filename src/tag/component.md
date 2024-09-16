[zurück](../Readme.md)

# `<component>`-Tag

Der `<component>`-Tag in Vue.js ist ein dynamischer Platzhalter für andere Komponenten. Er ermöglicht das Rendern unterschiedlicher Komponenten zur Laufzeit, basierend auf dynamischen Werten. Dies ist besonders nützlich, wenn du mehrere verschiedene Komponenten an derselben Stelle in der App einfügen möchtest, deren Auswahl auf Variablen oder Bedingungen beruht.

## 1. Grundlegende Verwendung

Der `<component>`-Tag rendert eine Komponente, die durch das Attribut `:is` definiert wird.

### Beispiel

```html
<!-- ParentComponent.vue -->
<template>
  <div>
    <component :is="currentComponent"></component>
  </div>
</template>

<script>
  import HeaderComponent from "./HeaderComponent.vue";
  import FooterComponent from "./FooterComponent.vue";

  export default {
    data() {
      return {
        currentComponent: "HeaderComponent", // Dynamischer Komponentenname
      };
    },
    components: {
      HeaderComponent,
      FooterComponent,
    },
  };
</script>
```

## 2. Erklärung

In diesem Beispiel steuert die `currentComponent`-Variable, welche Komponente gerendert wird. Wenn `currentComponent` auf `HeaderComponent` gesetzt ist, wird die `HeaderComponent` gerendert. Wird der Wert auf `FooterComponent` geändert, rendert Vue.js die entsprechende `FooterComponent`. Das Attribut `:is` dient als dynamische Referenz auf den Namen der zu rendernden Komponente.

## 3. Dynamische Attribute mit Objekten

```html
<template>
  <div>
    <component :is="components[currentView]"></component>
  </div>
</template>

<script>
  import HomeComponent from "./HomeComponent.vue";
  import AboutComponent from "./AboutComponent.vue";

  export default {
    data() {
      return {
        currentView: "home",
        components: {
          home: HomeComponent,
          about: AboutComponent,
        },
      };
    },
  };
</script>
```

In diesem Fall wird die gerenderte Komponente von der `currentView`-Variable gesteuert. Wenn `currentView` auf `about` gesetzt wird, zeigt es die `AboutComponent` an, und bei `home` die `HomeComponent`.

## 4. Sicherheit und Performance

- Sicherheit:

  Da dynamische Komponenten oft auf Benutzereingaben oder Zustände reagieren, sollte darauf geachtet werden, dass keine unerwarteten oder unsicheren Komponenten zur Laufzeit geladen werden. Es ist ratsam, nur vertrauenswürdige Komponenten in den `components`-Block zu laden und den Zugriff zu kontrollieren.

- Performance:

  Beim dynamischen Rendern vieler verschiedener Komponenten kann Vue.js unnötige Neukonstruktionen und -initialisierungen von Komponenten vermeiden, indem es Komponenten cached. Um die Performance weiter zu verbessern, kann der <keep-alive>-Wrapper verwendet werden. Er sorgt dafür, dass eine dynamisch gerenderte Komponente im Speicher bleibt, auch wenn sie nicht aktiv angezeigt wird.

```html
<keep-alive>
  <component :is="currentComponent"></component>
</keep-alive>
```

## 5. Zusammenfassung

Der `<component>`-Tag von Vue.js ermöglicht es, dynamisch zwischen verschiedenen Komponenten zu wechseln, was Flexibilität und Modularität in Anwendungen fördert. In Kombination mit dynamischen Daten oder Objekten kannst du Komponenten basierend auf Bedingungen oder Zuständen anzeigen. Sicherheit und Performance sollten beachtet werden, insbesondere bei größeren Anwendungen oder vielen dynamischen Komponenten.

[zurück](../Readme.md)
