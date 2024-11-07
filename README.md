# m.tag custom tags

The Alpine Components Package simplifies component inclusion for Alpine.js, enabling seamless integration of dynamic and interactive elements into web projects.

## Install

### With a CDN

```html

```

### With a Package Manager

```shell
npm i m.tag
```

```js
// main.js
import Alpine from 'alpinejs'
import component from 'm.tag'

Alpine.plugin(component)

Alpine.start()
```

## Usage
The Alpine Components Package simplifies the process of including custom components in your project using either custom elements or directives.

Step 1: Setting up the Components Directory

First, create a directory called "components" (or any other preferred name) in your project's root directory. Inside this directory, create a file named "counter.html".

```html
<!-- /components/counter.html -->
<div x-data="{ count: 0 }">
  <button x-on:click="count++">Increment</button>
  <span x-text="count"></span>
</div>
``` 

Step 3: Including the Counter Component

Now, in your initial HTML file (e.g., "index.html" or any other entry point), you can include the counter component using custom elements:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
</head>
<body>
  <!-- Include the Counter Component using the custom element <m-counter.html> -->
  <m-counter.html></m-counter.html>

  <!-- Notice: Use <m-counter.html> if you will include this component only once on the page. -->

  <!-- Other way to include if you need multiple components on the page, use <m-include url=""> syntax -->
  <m-include url="components/counter.html"></m-include>

  <!-- You can include other components here using the same syntax -->
  
  <script type="module" src="/main.js"></script>
</body>
</html>
```

## Passing Data to a Component

With the Alpine Components Package, you can easily pass data to your custom components. Let's explore how to do this using the <m-counter> custom element.

Step 1: Update the Counter Component (counter.html)

In "counter.html", modify the component to use the startvalue data as the initial count:

```html
<!-- /components/counter.html -->
<div x-data="{ count: startvalue }">
  <button x-on:click="count++">Increment</button>
  <span x-text="count"></span>
</div>
```

Step 2: Including the Counter Component with Data

Now, you can include the "counter.html" component using the <m-counter> custom element and pass the startvalue data to it:

```html
<!-- index.html -->

<!-- Include the Counter Component with the initial count value -->
<m-counter x-data="{ startvalue: 5 }"></m-counter>

<!-- Notice: Use <m-counter> if you will include this component only once on the page. -->

<!-- Other way to include if you need multiple components on the page, use <m-include url=""> syntax -->
<m-include url="components/counter.html" x-data="{ startvalue: 10 }"></m-include>
```


### Notice:

- Use <m-counter.html> if you plan to include this component only once on the page. This custom element will directly fetch and render the "counter.html" component.

- If you need to include the same component multiple times or dynamically load components, use the <m-include url=""> syntax. This directive will fetch the specified component and include it in the designated area.