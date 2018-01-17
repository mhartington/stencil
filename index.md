
<h2 style="font-weight: bolder; font-family: 'Avenir Next'; font-size: 2.4em">Stencil</h2>
### the Rise of Web Components

[Mike Hartington | @mhartington](https://twitter.com/mhartington)

---

### _Back in the Day…_

---

### Circa 2013

 _Ionic was still just an idea_

- Fast components were just difficult
- Frameworks at the time: 🗑 🔥

---

All we wanted

```html
  <ion-content>
    <ion-item>
      Hello World
    </ion-item>
  </ion-content>
```

---

### JavaScript at the time

- jQuery (not really a "framework")
- Backbone (MarionetteJS)
- AngularJS (still pretty new)

---

AngularJS Directives

# 💙

---

### Fast Forward

---

- Angular (2,…,4, 5)
- (P)React
- Ember
- VueJs

**All center around 'components'**

---

Yet a different API for each one

"Yo Dawg, I heard you like component APIs"

---

## Enter Web Components

<img src="imgs/web-component-logo.png" />

---

Vanilla JS API for reusable components

Built into the browser

Easily polyfill-able

---

<img src="https://imgs.xkcd.com/comics/standards.png" />

---

```js
  class BetterImg extends HTMLElement {

    constructor() {
      super();
      this.usingFallback = false;
    }

    get defaultWidth() {
      return 480;
    }

    get defaultHeight() {
      return 640;
    }

    connectedCallback() {
      this.init();
    }

    init() {
      this.innerHTML = this.template;
      this.addErrorListener();
      this.setSrc(this.url);
    }

    addErrorListener() {
      this.querySelector('img').onerror = this.onImgError.bind(this);
    }

    get url() {
      return this.getAttribute('url');
    }

    set url(value) {
      return this.url = value;
    }

    get width() {
      return this.getAttribute('width') || this.defaultWidth;
    }

    get height() {
      return this.getAttribute('height') || this.defaultHeight;
    }

    get fallback() {
      return this.getAttribute('fallback');
    }

    get logCallback() {
      return this.getAttribute('log');
    }

    get altText() {
      return this.getAttribute('alt') || "";
    }

    get template() {
      return `
        <img
          width=${this.width}
          height=${this.height}
          alt="${this.altText}"
        />
      `;
    }

    onImgError(err) {
      this.logError(err);
      this.useFallback();
    }

    useFallback() {
      if(this.fallback && !this.usingFallback) {
        this.setAttribute('url', this.fallback);
        this.setSrc(this.fallback);
        this.usingFallback = true;
      }
    }

    logError(err) {
      if(this.logCallback){
        window[this.logCallback](err);
      }
    }

    setSrc(url) {
      this.querySelector('img').src = url;
    }
  }

  customElements.define('better-img', BetterImg);
```

<small>
<a href="http://github.com/pearlbea/better-img">pearlbea/better-img</a>
</small>

---

## Powerful

<p class="fragment">But too low level</p>

---

- Reactive Data-binding
- Virtual DOM
- TypeScript support
- Async rendering ala React Fiber
- JSX
- SSR, pre-compilation

---

<!-- .slide: data-background="white" -->

<img src="imgs/stencil-logo.svg" width="200" />

<h1 style="color: #5850FF; font-weight: bolder;" >Stencil</h1>

---

- **Not a framework**
- Build time API
- Outputs Vanilla Web Components
- Borrows from other frameworks
<p class="fragment"> Did I mention, it's not a framework?</p>

---

<!-- .slide: data-background="#1b2b34" -->

<h1>
  <code style="color: #99c794">$ Demo</code>
</h1>

---

### API

<table>
  <tbody>
    <tr class="odd">
      <td><code>@Component</code></td>
      <td>Decorate a class as web component</td>
    </tr>
    <tr class="even">
      <td><code>@Prop()</code></td>
      <td>Expose a class property as an element property</td>
    </tr>
    <tr class="odd">
      <td><code>@State()</code></td>
      <td>Internal data that can cause a rerender</td>
    </tr>
    <tr class="even">
      <td><code>@Event()</code></td>
      <td>Decorator for custom events</td>
    </tr>
    <tr class="odd">
      <td><code>@Listen()</code></td>
      <td>Decorator for listening to custom events</td>
    </tr>
    <tr class="even">
      <td><code>@Element()</code></td>
      <td>Get a raw DOM reference to the current component</td>
    </tr>
  </tbody>
</table>

---

### But wait...Angular Elements?

Similar Ideas, different goals

---

### Not the only one

- [SkateJS](https://github.com/skatejs/skatejs)
- [Lit-Element](https://www.npmjs.com/package/lit-html-element)

---

### What's next?

- Docs: [stenciljs.com](https://stenciljs.com/docs/intro)
- Demos: [Async Rendering](https://stencil-fiber-demo.firebaseapp.com)
- Ionic/core 4.0 Built with Stencil!

---


### Build something cool?

Let us know, [@stenciljs](https://twitter.com/@stenciljs)

<img src="imgs/stencil-badge.svg" width="300" alt="">

---

## Thank you!

#### [stenciljs.com](https://stenciljs.com/)


`</html>`

