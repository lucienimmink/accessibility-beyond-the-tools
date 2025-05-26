<!-- .slide: data-theme="black" data-background-emoji="✨"-->
# Loosely coupled architectue

---

<!-- .slide: data-theme="black" data-background-emoji="🙋"-->
## Who uses API contracts?

---

<!-- .slide: data-theme="black" data-background-emoji="🏭"-->
## Who generates SDKs instead of writing API clients?

---

<!-- .slide: data-theme="black" data-background-emoji="💡"-->
## Tried that with UI components yet?

---

<!-- .slide: data-theme="yellow" data-background-emoji="📎"-->
## Lucien Immink

---

<!-- .slide: data-theme="yellow" data-clippy="It looks like you are looking at a consultant, shall we move on?" -->
![Lucien Immink](/assets/lucien-2024.jpg)<!-- .element: class="circle" style="max-height: 20vh" -->

### Principal Consultant @ Team Rockstars IT

#### Google Developer Expert

---

<!-- .slide: data-theme="black" data-background-emoji="👨‍🍳"-->
## Menu

- Communication<!-- .element: class="fragment fade-in-then-semi-out" -->
- Scale up using loosely coupled architecture<!-- .element: class="fragment fade-in-then-semi-out" -->
- Web-components<!-- .element: class="fragment fade-in-then-semi-out" -->
- Custom Elements Manifest<!-- .element: class="fragment fade-in-then-semi-out" -->
- Automation<!-- .element: class="fragment fade-in-then-semi-out" -->

---

<!-- .slide: data-theme="black" -->

![communication](/assets/law-of-communication.svg)

---

<!-- .slide: data-theme="black" -->

![communication](/assets/comms-server.svg)

---

<!-- .slide: data-theme="black" -->

![communication](/assets/comms-components.svg)

---

<!-- .slide: data-theme="black" data-background-emoji="🏭"-->
## Scale up using loosely coupled architecture

- Better delivery performance<!-- .element: class="fragment fade-in-then-semi-out" -->
  - Increased tempo
  - Stability
  - Reduces burnout and pain of deployment
- Increases linearly productivity<!-- .element: class="fragment fade-in-then-semi-out" -->

---

<!-- .slide: data-theme="black" data-background-emoji="🗹"-->
## To linearly scale up

- A goal oriented generative culture<!-- .element: class="fragment fade-in-then-semi-out" -->
- A modular architecture<!-- .element: class="fragment fade-in-then-semi-out" -->
- Engineering practises to enable CD<!-- .element: class="fragment fade-in-then-semi-out" -->
- Effective leadership<!-- .element: class="fragment fade-in-then-semi-out" -->

---

<!-- .slide: data-theme="black" data-background-emoji="🤔"-->
## Can we apply this beyond back-end?

- A goal oriented generative culture<!-- .element: class="fragment fade-in-then-semi-out checked" -->
- A modular architecture<!-- .element: class="fragment fade-in-then-semi-out checked" -->
- Engineering practises to enable CD<!-- .element: class="fragment fade-in-then-semi-out checked" -->

---

<!-- .slide: data-theme="black" data-background-emoji="🗹"-->
## Web Components

_Independent_ of any framework

- &lt;template&gt;, &lt;slot&gt;<!-- .element: class="fragment fade-in-then-semi-out" -->
- shadow dom<!-- .element: class="fragment fade-in-then-semi-out" -->
- custom-elements<!-- .element: class="fragment fade-in-then-semi-out" -->
- part of the web platform<!-- .element: class="fragment fade-in-then-semi-out" -->

---

<!-- .slide: data-theme="black" data-background-emoji="🚫"-->
## Framework agnostic

_Independent_ of any framework

- No (peer)dependency on React/Angular/Vue/...<!-- .element: class="fragment fade-in-then-semi-out" -->
- No need to rewrite your code to use UI component<!-- .element: class="fragment fade-in-then-semi-out" -->
- No upgrade dead-locks<!-- .element: class="fragment fade-in-then-semi-out" -->

---

<!-- .slide: data-theme="black" data-background-emoji="🧑‍💻"-->

```html[0|4]
<!DOCTYPE html>
<html lang="en">
  <body>
    <hello-world type="amazing"></hello-world>
    <script type="module" src="hello-world.js"></script>
  </body>
</html>
```

<p>
  <img src="/assets/icons/html.svg" class="icon icon-inline" alt=""> index.html
</p><!-- .element: class="filename" -->

---

<!-- .slide: data-theme="black" data-background-emoji="📋"-->
## Web (Components) API

<ul>
    <li>properties <span class="muted">(input)</span></li><!-- .element: class="fragment fade-in-then-semi-out" -->
    <li>events <span class="muted">(output)</span></li><!-- .element: class="fragment fade-in-then-semi-out" -->
    <li>slots <span class="muted">(placement)</span></li><!-- .element: class="fragment fade-in-then-semi-out" -->
    <li>css (variables) <span class="muted">(styling)</span></li><!-- .element: class="fragment fade-in-then-semi-out" -->
</ul>

---

<!-- .slide: data-theme="black" -->
### Custom elements manifest (CEM)

Many tools need some machine-readable descriptions of custom elements: IDEs, documentation viewers, linters, graphical design tools, etc.<!-- .element: class="fragment fade-in-then-semi-out" -->

Custom elements manifest is an effort to bring together tool owners to standardize on a common specification for a description format.<!-- .element: class="fragment fade-in-then-semi-out" -->

---

<!-- .slide: data-theme="black" data-background-emoji="🤔" -->
## Design-first or not to design-first

<ul>
    <li>Write CEM first <span class="muted">or</span></li><!-- .element: class="fragment fade-in-then-semi-out" -->
    <li>Write skeleton component to generate CEM</li><!-- .element: class="fragment fade-in-then-semi-out" -->
</ul>

---

<!-- .slide: data-theme="black" data-background-emoji="👩‍💻" -->
## Custom Element Manifest

```json[0|9-20|45-60|61-70]
{
  "kind": "javascript-module",
  "path": "components/hello-world.ts",
  "declarations": [
    {
      "kind": "class",
      "description": "Hello generated world! Click for a gift or a bomb",
      "name": "HelloWorld",
      "cssProperties": [
        {
          "description": "Controls the text colour",
          "name": "--text-color",
          "default": "black"
        },
        {
          "description": "Controls the background colour",
          "name": "--background-color",
          "default": "red"
        }
      ],
      "members": [
        {
          "kind": "field",
          "name": "type",
          "type": {
            "text": "string"
          },
          "default": "\"wonderful\"",
          "description": "What type is the world today?",
          "attribute": "type"
        },
        {
          "kind": "method",
          "name": "eventFunctionGift",
          "privacy": "private",
          "description": "Write function that dispatches the event Gift"
        },
        {
          "kind": "method",
          "name": "eventFunctionBomb",
          "privacy": "private",
          "description": "Write function that dispatches the event Bomb"
        }
      ],
      "events": [
        {
          "name": "Gift",
          "type": {
            "text": "Event"
          },
          "description": "gift - I'm bearing a gift"
        },
        {
          "name": "Bomb",
          "type": {
            "text": "Event"
          },
          "description": "bomb - This was a mistake..."
        }
      ],
      "attributes": [
        {
          "name": "type",
          "type": {
            "text": "string"
          },
          "default": "wonderful",
          "description": "What type is the world today?",
          "fieldName": "type"
        }
      ],
      "superclass": {
        "name": "LitElement",
        "package": "lit"
      },
      "tagName": "hello-world",
      "customElement": true
    }
  ],
  "exports": [
    {
      "kind": "js",
      "name": "HelloWorld",
      "declaration": {
        "name": "HelloWorld",
        "module": "components/hello-world.ts"
      }
    },
    {
      "kind": "custom-element-definition",
      "name": "hello-world",
      "declaration": {
        "name": "HelloWorld",
        "module": "components/hello-world.ts"
      }
    }
  ]
}
```

<p>
  <img src="/assets/icons/javascript.svg" class="icon icon-inline" alt=""> custom-elements.json
</p><!-- .element: class="filename" -->

---

<!-- .slide: data-theme="black" data-block="true" data-background-emoji="🪄"-->
## 🧙‍♂️ magic time ✨🌈

<api-viewer src="./src/custom-elements.json" selected="hello-world">API viewer not available</api-viewer><!-- .element: class="fragment fade-in" -->

---

<!-- .slide: data-theme="black" data-background-emoji="💡"-->
## Automation

- Demos<!-- .element: class="fragment fade-in-then-semi-out" -->
- Linting<!-- .element: class="fragment fade-in-then-semi-out" -->
- Testing<!-- .element: class="fragment fade-in-then-semi-out" -->
- Cataloging<!-- .element: class="fragment fade-in-then-semi-out" -->
- Generation<!-- .element: class="fragment fade-in-then-semi-out" -->
- Integration<!-- .element: class="fragment fade-in-then-semi-out" -->
- Documentation<!-- .element: class="fragment fade-in-then-semi-out" -->

---

<!-- .slide: data-theme="black" data-background-emoji="🎀"-->
## Wrap up

- Communication<!-- .element: class="fragment fade-in-then-semi-out checked" -->
- Scale up using loosely coupled architecture<!-- .element: class="fragment fade-in-then-semi-out checked" -->
- Web-components<!-- .element: class="fragment fade-in-then-semi-out checked" -->
- Custom Elements Manifest<!-- .element: class="fragment fade-in-then-semi-out checked" -->
- Automation<!-- .element: class="fragment fade-in-then-semi-out checked" -->

---

<!-- .slide: data-theme="black" data-background-emoji="🙏" -->
## Thank you

Contact me:

🏭 [www.teamrockstars.nl](https://www.teamrockstars.nl/) <br >
🏢 [linkedin.com/in/lucien-immink](https://www.linkedin.com/in/lucien-immink/) <br >
📧 [lucien.immink@teamrockstars.nl](mailto://lucien.immink@teamrockstars.nl) <br >
