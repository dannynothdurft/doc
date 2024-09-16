[zurück](../Readme.md)

# v-on

Die `v-on` Direktive in Vue.js wird verwendet, um Event-Listener an DOM-Elemente zu binden. Dies ermöglicht es dir, auf Benutzerinteraktionen wie Klicks, Eingaben oder andere Ereignisse zu reagieren, indem du Methoden oder Funktionen in deiner Vue-Komponente ausführst.

## Was ist `v-on`?

- `v-on` wird verwendet, um Event-Listener an HTML-Elemente zu binden. Dadurch kannst du auf Ereignisse reagieren und entsprechende Logik in deiner Vue-Komponente ausführen.

- Syntax:

  - Langform: `v-on:event="method"`
  - Kurzform: `@event="method"`
  - Beispiel:

  ```html
  <button v-on:click="handleClick">Klick mich!</button>
  <!-- oder kürzer -->
  <button @click="handleClick">Klick mich!</button>
  ```

## Beispiel

Hier ist ein detailliertes Beispiel, das zeigt, wie `v-on` verwendet wird:

```html
<template>
  <div>
    <button @click="handleClick">Klick mich!</button>
    <!-- <button @click="handleClick(hier kann was übergeben werden)">Klick mich!</button> -->
    <!-- <button @click="handleClick1(), handleClick2()">Klick mich!</button> mehere Übergeben -->
    <input
      v-model="inputValue"
      @input="handleInput"
      placeholder="Gib etwas ein"
    />
    <p>Du hast eingegeben: {{ inputValue }}</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        inputValue: "",
      };
    },
    methods: {
      handleClick() {
        alert("Button wurde geklickt!");
      },
      handleInput(event) {
        this.inputValue = event.target.value;
      },
    },
  };
</script>
```

## Erklärung

- `<button @click="handleClick">Klick mich!</button>`:

  - Die `@click` Kurzform von `v-on:click` wird verwendet, um die Methode `handleClick` bei einem Klick-Ereignis auf den Button aufzurufen. Wenn der Button geklickt wird, wird die `handleClick` Methode in der Vue-Komponente ausgeführt, die eine `alert`-Nachricht anzeigt.

- `<input v-model="inputValue" @input="handleInput" placeholder="Gib etwas ein">`:

  - Das `v-model` Attribut bindet den Wert des `<input>`-Feldes an die `inputValue` Datenbindung, was eine reaktive Zwei-Wege-Datenbindung ermöglicht.

  - Die `@input` Direktive wird verwendet, um die Methode `handleInput` aufzurufen, wenn der Benutzer etwas in das Eingabefeld eingibt. Die Methode `handleInput` aktualisiert den Wert von `inputValue` mit dem aktuellen Wert des Eingabefeldes, der über `event.target.value` erhalten wird.

## Besondere Aspekte

- Event-Objekt:

  In Event-Handler-Methoden kannst du das Event-Objekt verwenden, um auf spezifische Details des Ereignisses zuzugreifen. Zum Beispiel, `event.target.value` gibt dir den aktuellen Wert eines `<input>`-Feldes.

- Modifikatoren:

  Vue.js unterstützt auch Event-Modifikatoren, die das Verhalten von Ereignissen ändern können, wie `.stop` (verhindert das Event-Bubbling) oder `.prevent` (verhindert das Standardverhalten des Events).

  ```html
  <button @click.stop="handleClick">Klick mich!</button>
  ```

## Zusammenfassung

Die `v-on` Direktive in Vue.js wird verwendet, um Event-Listener an DOM-Elemente zu binden, sodass du auf Benutzerinteraktionen reagieren kannst. Mit `v-on` (oder der Kurzform `@`) kannst du Methoden in deiner Vue-Komponente aufrufen, wenn ein bestimmtes Ereignis eintritt. Es bietet auch Möglichkeiten zur Event-Objekt-Verarbeitung und unterstützt Event-Modifikatoren für zusätzliche Steuerung.

## Events

### 1.Maus-Events

| event      | Beschreibung                                              | code                             |
| ---------- | --------------------------------------------------------- | -------------------------------- |
| click      | Wird ausgelöst, wenn auf ein Element geklickt wird.       | `@click="handleClick"`           |
| dblclick   | Wird ausgelöst, wenn doppelt geklickt wird.               | `@dblclick="handleClick"`        |
| mousedown  | Wird ausgelöst, wenn eine Maustaste gedrückt wird.        | `@mousedown="handleMouseDown"`   |
| mouseup    | Wird ausgelöst, wenn die Maustaste losgelassen wird.      | `@mouseup="handleMouseUp"`       |
| mousemove  | Wird ausgelöst, wenn die Maus bewegt wird.                | `@mousemove="handleMouseMove"`   |
| mouseenter | Wird ausgelöst, wenn der Mauszeiger ein Element betritt.  | `@mouseenter="handleMouseEnter"` |
| mouseleave | Wird ausgelöst, wenn der Mauszeiger ein Element verlässt. | `@mouseleave="handleMouseLeave"` |

### 2.Tastatur-Events

| event    | Beschreibung                                                          | code                         |
| -------- | --------------------------------------------------------------------- | ---------------------------- |
| keydown  | Wird ausgelöst, wenn eine Taste gedrückt wird.                        | `@keydown="handleKeyDown"`   |
| keyup    | Wird ausgelöst, wenn eine Taste losgelassen wird.                     | `@keyup="handleKeyUp"`       |
| keypress | Wird ausgelöst, wenn eine Taste gedrückt und wieder losgelassen wird. | `@keypress="handleKeyPress"` |

### 3.Formularevents

| event  | Beschreibung                                                                               | code                     |
| ------ | ------------------------------------------------------------------------------------------ | ------------------------ |
| input  | Wird ausgelöst, wenn sich der Wert eines Eingabefeldes ändert.                             | `@input="handleInput"`   |
| change | Wird ausgelöst, wenn sich der Wert eines Eingabefeldes ändert und der Fokus verloren geht. | `@change="handleChange"` |
| submit | Wird ausgelöst, wenn ein Formular übermittelt wird.                                        | `@submit="handleSubmit"` |
| focus  | Wird ausgelöst, wenn ein Element den Fokus erhält.                                         | `@focus="handleFocus"`   |
| blur   | Wird ausgelöst, wenn ein Element den Fokus verliert.                                       | `@blur="handleBlur"`     |

### 4.Fenster-Events

| event  | Beschreibung                                           | code                     |
| ------ | ------------------------------------------------------ | ------------------------ |
| resize | Wird ausgelöst, wenn das Browserfenster geändert wird. | `@resize="handleResize"` |
| scroll | Wird ausgelöst, wenn auf einer Seite gescrollt wird.   | `@scroll="handleScroll"` |

### 5.Drag & Drop Events

| event     | Beschreibung                                                 | code                           |
| --------- | ------------------------------------------------------------ | ------------------------------ |
| drag      | Wird ausgelöst, wenn ein Element gezogen wird.               | `@drag="handleDrag"`           |
| dragstart | Wird ausgelöst, wenn der Ziehvorgang beginnt.                | `@dragstart="handleDragStart"` |
| dragend   | Wird ausgelöst, wenn der Ziehvorgang endet.                  | `@dragend="handleDragEnd"`     |
| dragenter | Wird ausgelöst, wenn ein gezogenes Element ein Ziel betritt. | `@dragenter="handleDragEnter"` |
| drop      | Wird ausgelöst, wenn das Element fallen gelassen wird.       | `@drop="handleDrop"`           |

### 6.Medien-Events

| event      | Beschreibung                                      | code                             |
| ---------- | ------------------------------------------------- | -------------------------------- |
| play       | Wird ausgelöst, wenn die Wiedergabe beginnt.      | `@play="handlePlay"`             |
| pause      | Wird ausgelöst, wenn die Wiedergabe pausiert.     | `@pause="handlePause"`           |
| ended      | Wird ausgelöst, wenn der Medieninhalt endet.      | `@ended="handleEnded"`           |
| timeupdate | Wird während der Wiedergabe regelmäßig ausgelöst. | `@timeupdate="handleTimeUpdate"` |

### 7.Clipboard-Events

| event | Beschreibung                                        | code                   |
| ----- | --------------------------------------------------- | ---------------------- |
| copy  | Wird ausgelöst, wenn Inhalte kopiert werden.        | `@copy="handleCopy"`   |
| cut   | Wird ausgelöst, wenn Inhalte ausgeschnitten werden. | `@cut="handleCut"`     |
| paste | Wird ausgelöst, wenn Inhalte eingefügt werden.      | `@paste="handlePaste"` |

### 8.Andere Events

| event       | Beschreibung                                        | code                               |
| ----------- | --------------------------------------------------- | ---------------------------------- |
| contextmenu | Wird ausgelöst, wenn das Kontextmenü geöffnet wird. | `@contextmenu="handleContextMenu"` |
| wheel       | Wird ausgelöst, wenn das Mausrad bewegt wird.       | `@wheel="handleWheel"`             |

## Modifikation

### 1.Event-Modifikatoren

| event   | Beschreibung                                                                         | code                                                          |
| ------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------- |
| stop    | Verhindert das Weiterleiten des Events (Event-Bubbling).                             | `<button @click.stop="handleClick">Button</button>`           |
| prevent | Verhindert das Standardverhalten des Events.                                         | `<form @submit.prevent="submitForm"></form>`                  |
| capture | Setzt den Listener in der Capture-Phase anstelle der Bubbling-Phase an.              | `<button @click.capture="handleClick">Button</button>`        |
| self    | Führt das Event nur aus, wenn es auf dem genauen Ziel-Element ausgelöst wird.        | `<div @click.self="handleClick">Div</div>`                    |
| once    | Der Event-Listener wird nur einmal ausgeführt.                                       | `<button @click.once="handleClick">Einmaliger Klick</button>` |
| passive | Nutzt den Listener in einer passiven Weise, um die Scroll-Performance zu verbessern. | `<div @scroll.passive="handleScroll">Inhalt</div>`            |

### 2.System-Key-Modifikatoren (für Tastatur-Events)

| event | Beschreibung                                                                                           | code                             |
| ----- | ------------------------------------------------------------------------------------------------------ | -------------------------------- |
| ctrl  | Das Event wird nur ausgelöst, wenn die Ctrl-Taste gedrückt ist.                                        | `@keydown.ctrl="handleKeyDown"`  |
| alt   | Das Event wird nur ausgelöst, wenn die Alt-Taste gedrückt ist.                                         | `@keydown.alt="handleKeyDown"`   |
| shift | Das Event wird nur ausgelöst, wenn die Shift-Taste gedrückt ist.                                       | `@keydown.shift="handleKeyDown"` |
| meta  | Das Event wird nur ausgelöst, wenn die Meta-Taste (Windows-Taste oder Command auf macOS) gedrückt ist. | `@keydown.meta="handleKeyDown"`  |

### 3.Maus-Button-Modifikatoren (für Maus-Events)

| event  | Beschreibung                                                              | code                          |
| ------ | ------------------------------------------------------------------------- | ----------------------------- |
| left   | Das Event wird nur ausgelöst, wenn die linke Maustaste gedrückt wurde.    | `@click.left="handleClick"`   |
| right  | Das Event wird nur ausgelöst, wenn die rechte Maustaste gedrückt wurde.   | `@click.right="handleClick"`  |
| middle | Das Event wird nur ausgelöst, wenn die mittlere Maustaste gedrückt wurde. | `@click.middle="handleClick"` |

### 4.Keycode-Modifikatoren (für spezifische Tasten)

| event      | Beschreibung                                                                 | code                                  |
| ---------- | ---------------------------------------------------------------------------- | ------------------------------------- |
| enter      | Das Event wird nur ausgelöst, wenn die Enter-Taste gedrückt wird.            | `@keydown.enter="handleKeyDown"`      |
| tab        | Das Event wird nur ausgelöst, wenn die Tab-Taste gedrückt wird.              | `@keydown.tab="handleKeyDown"`        |
| delete     | Das Event wird nur ausgelöst, wenn die Delete-Taste gedrückt wird.           | `@keydown.delete="handleKeyDown"`     |
| esc        | Das Event wird nur ausgelöst, wenn die Escape-Taste gedrückt wird.           | `@keydown.esc="handleKeyDown"`        |
| space      | Das Event wird nur ausgelöst, wenn die Leertaste gedrückt wird.              | `@keydown.space="handleKeyDown"`      |
| arrow-up   | Das Event wird nur ausgelöst, wenn die Pfeil nach oben-Taste gedrückt wird.  | `@keydown.arrow-up="handleKeyDown"`   |
| arrow-down | Das Event wird nur ausgelöst, wenn die Pfeil nach unten-Taste gedrückt wird. | `@keydown.arrow-down="handleKeyDown"` |

### 5.Modifikatoren für Eingabegeräte

| event | Beschreibung                                                                            | code                              |
| ----- | --------------------------------------------------------------------------------------- | --------------------------------- |
| exact | Das Event wird nur ausgelöst, wenn nur die angegebenen Modifikatortasten gedrückt sind. | `@click.ctrl.exact="handleClick"` |

[zurück](../Readme.md)
