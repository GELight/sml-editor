# SLM Editor

Provides a simple web component for sml editing in browser.

## CDN

For using SML as runtime build in your browser you can use the latest version with:

```html
<script src="https://unpkg.com/@gelight/sml-editor"></script>
```
or
```html
<script src="https://cdn.jsdelivr.net/npm/@gelight/sml-editor"></script>
```

## Using

Using the component in your template
```js
<sml-editor auto-resize class="editor"></sml-editor>
```

| Attributes    | Description |
| ------------- | ----------- |
| auto-resize   | Defines whether the component height should be auto sized |
| class         | The class attribute specifies one or more CSS classnames for the component. |

## Events

```js
<script type="text/javascript">
    let editor = document.querySelector('sml-editor');
    editor.addEventListener('change', (e) => {
        console.log(e.detail);
    });
</script>
```

## CSS Customizing

| CSS Variables                 |
| ----------------------------- |
| --sml-editor-tab-size         |
| --sml-editor-color            |
| --sml-editor-bg               |
| --sml-editor-border           |
| --sml-editor-padding          |
| --sml-editor-max-height       |
| --sml-editor-height           |
| --sml-editor-box-shadow       |
| --sml-editor-text-shadow      |
| --sml-editor-font-family      |
| --sml-editor-font-size        |
| --sml-editor-line-height      |
| --sml-editor-font-weight      |
| --sml-editor-font-style       |
| --sml-editor-font-stretch     |
| --sml-editor-letter-spacing   |
| --sml-editor-text-transform   |
