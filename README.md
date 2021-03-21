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

```css
--sml-editor-tab-size: 2;
--sml-editor-color: #8e9fcd;
--sml-editor-bg: linear-gradient(161deg, #333a47 0%, #1c1d24 100%);
--sml-editor-border: 2px solid #4f5b70;
--sml-editor-padding: .8rem;
--sml-editor-max-height: auto;
--sml-editor-height: auto;
--sml-editor-box-shadow: 0 0 .8rem .8rem rgba(0,0,0,0.75);
--sml-editor-text-shadow: 0px 4px 4px rgba(0,0,0,0.85);
--sml-editor-font-family: monospace;
--sml-editor-font-size: 14px;
--sml-editor-line-height: 1.4rem;
--sml-editor-font-weight: 400;
--sml-editor-font-style: initial;
--sml-editor-font-stretch: initial;
--sml-editor-letter-spacing: .1rem;
--sml-editor-text-transform: initial;
```
