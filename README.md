# What's this?

This is a webpack loader. It can inline SVG files into HTML, so that you can apply css to them.

It was forked from [https://github.com/asnowwolf/markup-inline-loader] - thank you!

## Example 

### Configuration

```js
{
  test: /\.html$/,
  loader: 'svg-inline'
},
```

or with html-loader:

```js
{
  test: /\.html$/,
  loader: 'html!svg-inline'
},
```


### Original HTML

Attributes (apart from `src`) are retained in the output.

```html
<svg class="icon" src="./icons/camera.svg" />
```

### Translated HTML

```svg
<svg class="icon" viewBox="0 0 1024 1404.416" xmlns="http://www.w3.org/2000/svg">
  <path d="M960 440.384h-256v-128c0-35.312-28.656-64-64-64h-256c-35.344 0-64 28.688-64 64v128h-128v-64h-128v64c-35.344 0-64 28.688-64 64v704c0 35.376 28.656 64 64 64h896c35.344 0 64-28.624 64-64v-704c0-35.312-28.656-64-64-64z m-512-64h128v64h-128v-64z m448 768h-768v-576h768v576z m-384-128c106.032 0 192-85.938 192-192s-85.968-192-192-192-192 85.938-192 192 85.968 192 192 192z m0-256c35.344 0 64 28.624 64 64s-28.656 64-64 64-64-28.624-64-64 28.656-64 64-64z"/>
</svg>
```

So we can apply css styles to `svg > path {}`.

or

```svg
<?xml version="1.0" encoding="utf-8"?>
<!-- Generator: Adobe Illustrator 19.1.0, SVG Export Plug-In . SVG Version: 6.00 Build 0)  -->
<svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
   viewBox="0 0 250 250" style="enable-background:new 0 0 250 250;" xml:space="preserve">
<style type="text/css">
  .st0{fill:#DD0031;}
  .st1{fill:#C3002F;}
  .text{fill:#FFFFFF;}
</style>
<g>
  <polygon class="st0" points="125,30 125,30 125,30 31.9,63.2 46.1,186.3 125,230 125,230 125,230 203.9,186.3 218.1,63.2 	"/>
  <polygon class="st1" points="125,30 125,52.2 125,52.1 125,153.4 125,153.4 125,230 125,230 203.9,186.3 218.1,63.2 125,30 	"/>
  <path class="text" d="M125,52.1L66.8,182.6h0h21.7h0l11.7-29.2h49.4l11.7,29.2h0h21.7h0L125,52.1L125,52.1L125,52.1L125,52.1
    L125,52.1z M142,135.4H108l17-40.9L142,135.4z"/>
</g>
</svg>
```

So we can apply css animations to `svg > .text`, for example: 

```css
@keyframes rotate {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(-180deg);
  }
}

svg > .text {
  animation: 3s infinite rotate;
  transform-origin: center;
}
```
