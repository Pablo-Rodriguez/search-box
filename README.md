# search-box

Search-box web component made with polymer and baconjs

## Install

```
  $ bower install --save search-box
```

## Usage
```html
<!doctype html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>search-box</title>
  <!-- We import polymer  -->
  <link rel="import" href="bower_components/polymer/polymer.html">
  <!-- We import search-box  -->
  <link rel="import" href="bower_components/search-box/search-box.html">
</head>
<body>

  <template id="app" is="dom-bind">
    <search-box
      url="http://localhost:3000/users"
      label="your search"
      last-response="{{res}}"
      on-waiting="waiting"
      on-response="handleResponse"></search-box>
    <template is="dom-repeat" items="{{res}}" as="model">
      <div>
        <span>name: {{model.name}}</span>
        <span>last: {{model.last}}</span>
      </div>
    </template>
    <div id="loading"></div>
  </template>

  <script>
    document.addEventListener('dom-change', function () {
      var app = document.getElementById('app');
      var loading = document.getElementById('loading');
      app.waiting = function () {
        loading.innerHTML = 'loading...';
      }
      app.handleResponse = function () {
        loading.innerHTML = '';
      }
    });
  </script>

</body>
</html>
```
