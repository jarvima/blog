
## paper-icon-button - hidden dependency

One little gotcha that I found while using `paper-icon-button`:

`paper-icon-button` has a dependency on `iron-icons` (for the default icons) that isn't included in its html imports.

## The fix

#### Quickly explained:

So if you are using the default icons, whenever you html import `paper-icon-button`:

```html
<link rel="import" href="/bower_components/paper-icon-button/paper-icon-button.html">
```

You will also need to html-import `iron-icons`:

```html
<link rel="import" href="/bower_components/iron-icons/iron-icons.html">
```

#### In more verbose terms:

The following will not render a button because the icon won't resolve.

```html
<link rel="import" href="/bower_components/polymer/polymer.html">
<link rel="import" href="/bower_components/paper-icon-button/paper-icon-button.html">

<dom-module id="mj-debug">
  <template>
    <paper-icon-button icon="help" style="color: blue"></paper-icon-button>
  </template>
</dom-module>

<script>
  Polymer({
    is: 'mj-debug'
  });
</script>
```

The following will render the icon.  Notice the additional html import.

```html
<link rel="import" href="/bower_components/polymer/polymer.html">
<link rel="import" href="/bower_components/paper-icon-button/paper-icon-button.html">
<link rel="import" href="/bower_components/iron-icons/iron-icons.html">

<dom-module id="mj-debug">
  <template>
    <paper-icon-button icon="help" style="color: blue"></paper-icon-button>
  </template>
</dom-module>

<script>
  Polymer({
    is: 'mj-debug'
  });
</script>
```
