[zurück](../Readme.md)

# props

In Vue.js sind `props` eine Möglichkeit, Daten von einer Elternkomponente an eine Kindkomponente weiterzugeben. Sie ermöglichen es, eine flexible und modulare Komponentenhierarchie zu erstellen, in der die Kindkomponente vom Elternteil bestimmte Werte (`props`) erhält und auf Basis dieser Werte rendern oder reagieren kann. Props werden von der Elternkomponente als Attribute definiert und in der Kindkomponente empfangen.

## Grundlegende Verwendung

- Elternkomponente: Überträgt Daten an die Kindkomponente, indem sie `props` als HTML-Attribute an die Komponente übergibt.
- Kindkomponente: Deklariert die `props` und empfängt die Werte von der Elternkomponente.

## Beispiel

```html
<!-- Elternkomponente -->
<template>
  <div>
    <child-component title="Hello World" :count="5"></child-component>
  </div>
</template>

<script>
  import ChildComponent from "./ChildComponent.vue";

  export default {
    components: {
      ChildComponent,
    },
  };
</script>

<!-- Kindkomponente (ChildComponent.vue) -->
<template>
  <div>
    <h1>{{ title }}</h1>
    <p>Count: {{ count }}</p>
  </div>
</template>

<script>
  export default {
    props: {
      title: {
        type: String,
        required: true,
      },
      count: {
        type: Number,
        default: 0,
      },
    },
  };
</script>
```

## Erläuterung

- Elternkomponente:

  Hier werden die Daten `title="Hello World"` und `:count="5"` an die Kindkomponente `ChildComponent` übergeben.

  - Der Doppelpunkt (`:`) vor `count` bedeutet, dass es sich um eine dynamische Bindung handelt, die den Wert von `5` an die Kindkomponente übergibt.

- Kindkomponente:

  Die `props` `title` und `count` werden deklariert und in der Komponente verwendet.

  - `type`: Bestimmt, welchen Datentyp die Prop haben soll (z. B. `String`, `Number`).
  - `required`: Gibt an, ob die Prop von der Elternkomponente bereitgestellt werden muss.
  - `default`: Gibt einen Standardwert an, falls die Elternkomponente keine Daten übergibt.

## Dynamische Attribute mit Objekten

Props können auch als Objekte übergeben werden, was besonders praktisch ist, wenn viele Werte übergeben werden sollen.

```html
<template>
  <div>
    <child-component :user="user"></child-component>
  </div>
</template>

<script>
  import ChildComponent from "./ChildComponent.vue";

  export default {
    data() {
      return {
        user: {
          name: "John Doe",
          age: 25,
        },
      };
    },
    components: {
      ChildComponent,
    },
  };
</script>
<!-- Elternkomponente -->
<template>
  <div>
    <child-component :user="user"></child-component>
  </div>
</template>

<script>
  import ChildComponent from "./ChildComponent.vue";

  export default {
    data() {
      return {
        user: {
          name: "John Doe",
          age: 25,
        },
      };
    },
    components: {
      ChildComponent,
    },
  };
</script>

<!-- Kindkomponente (ChildComponent.vue) -->
<template>
  <div>
    <p>Name: {{ user.name }}</p>
    <p>Age: {{ user.age }}</p>
  </div>
</template>

<script>
  export default {
    props: {
      user: {
        type: Object,
        required: true,
      },
    },
  };
</script>
```

Dynamische Props: Die gesamte `user`-Datenstruktur wird als Objekt an die Kindkomponente übergeben. Dadurch können mehrere Daten in einer einzigen Prop übertragen werden.

## Validierung von Props

Vue.js bietet die Möglichkeit, die Typen und Anforderungen für Props zu validieren. Neben einfachen Typen wie `String`, `Number` und `Object` kannst du auch benutzerdefinierte Validatoren hinzufügen.

```html
props: { age: { type: Number, required: true, validator(value) { return value >=
18; } } }
```

In diesem Beispiel prüft die `validator`-Funktion, ob das `age`-Prop größer oder gleich 18 ist. Wenn die Bedingung nicht erfüllt wird, gibt Vue eine Warnung aus.
Props in Verbindung mit v-model

Props können auch mit `v-model` verwendet werden, um eine Zwei-Wege-Datenbindung zwischen einer Eltern- und Kindkomponente zu erreichen. In diesem Fall muss das `v-model`-Directive in der Kindkomponente als `value`-Prop verwendet und ein `input`-Event zur Aktualisierung ausgelöst werden.

```html
<!-- Elternkomponente -->
<template>
  <div>
    <custom-input v-model="name"></custom-input>
    <p>Dein Name: {{ name }}</p>
  </div>
</template>

<script>
  import CustomInput from "./CustomInput.vue";

  export default {
    data() {
      return {
        name: "",
      };
    },
    components: {
      CustomInput,
    },
  };
</script>

<!-- Kindkomponente (CustomInput.vue) -->
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

  Bei der Verwendung von `props` gibt es keine spezifischen Sicherheitsrisiken, aber es sollte sichergestellt werden, dass sensible Daten nicht unnötig an Kindkomponenten weitergegeben werden. Prop-Validierung kann helfen, unerwünschte oder fehlerhafte Daten zu verhindern.

- Performance:

  Props sind in der Regel sehr effizient. Wenn jedoch große oder tiefe Datenstrukturen übergeben werden, könnte es zu Performanceproblemen kommen. In solchen Fällen kann es sinnvoll sein, nur die notwendigen Daten zu übergeben oder zu prüfen, ob eine Veränderung der Struktur tatsächlich notwendig ist.

## Zusammenfassung

Vue.js `props` ermöglichen eine klare und einfache Methode, Daten zwischen Eltern- und Kindkomponenten zu teilen. Sie unterstützen Typenvalidierung und können als Objekte übergeben werden, um komplexere Datenstrukturen zu handhaben. Mit Props können Komponenten modular und wiederverwendbar gestaltet werden, was die Flexibilität und Wartbarkeit einer Anwendung erheblich verbessert.

[zurück](../Readme.md)
