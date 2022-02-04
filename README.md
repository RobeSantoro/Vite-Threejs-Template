# Vite Three.js Template

![alt text](./SocialImage.jpg)

# index.html
Add the link to the css file:
```html
<link rel="stylesheet" href="./style.css">
```

Add a canvas element to the body tag of index.html file.
```html
<canvas class="webgl">
  <p>Your browser doesn't support WebGL</p>
</canvas>
```

Add script tag to the body tag of index.html file.
```html
<script type="module" src="./main.js"></script>
```
___
# style.css
Add the following styles to style.css file.
```css
* {
  margin: 0;
  padding: 0;
}

html, body {
  background: transparent;
  overflow: hidden;
}

.webgl {
  position: fixed;
  top: 0;
  left: 0;
  outline: none;
}
```
___
# main.js
#### Import Three-JS
```js
import * as THREE from 'three'
```

#### Get the canvas element from the DOM
```js
// Get the canvas
const canvas = document.querySelector('canvas.webgl')
```

#### Create Scene
```js
// Scene
const scene = new THREE.Scene()
```

#### Create Camera ,set its Position, and add it to the scene
```js
// Camera
const camera = new THREE.PerspectiveCamera(30, window.innerWidth / window.innerHeight, 0.1, 1000)
camera.position.set(-5, 3, 5)
camera.lookAt(new THREE.Vector3(0, 0, 0))

scene.add(camera)
```

#### Create a Cube and add it to the scene
```js
// Create a Cube
const geometry = new THREE.BoxGeometry(1, 1, 1)
const material = new THREE.MeshStandardMaterial({ color: 0x00ff00 })
const cube = new THREE.Mesh(geometry, material)  

scene.add(cube)
```

### Create a Light
```js
// Add a light
const light = new THREE.DirectionalLight(0xffffff, 1)
light.position.set(-1, 3, 4)

scene.add(light)
```

#### Create Renderer, set its size, and launch the render
```js
// Create the Renderer
const renderer = new THREE.WebGLRenderer( { canvas : canvas } )
// Render the Scene
renderer.setSize(window.innerWidth, window.innerHeight)
renderer.render(scene, camera)

