# 4 basic elements
>* Scene
>* Objects
>* Camera
>* Renderer


## a. Create a Scene
`const scene = new THREE.Scene();`

## b. Create Object
### 1. Create geometry
`const geometry = new THREE.BoxGeometry(1,1,1);`

### 2. Create material
`const material = new THREE.MeshBasicMaterial({color: 'red'})`

### 3. Create mesh with geometry and material
`const mesh = new THREE.Mesh(geometry, material)`

### 4. Add mesh to scene
`scene.add(mesh)`

## c. Create Camera
```Javascript
const sizes = {
    width: 800,
    height: 600
}

// pov, aspect ratio
const camera = new THREE.PerspectiveCamera(75, sizes.width / sizes.height)
```

`75 = field of view (degree)`

_*large number = can see more direction, hence distortion_

_*small number = things look zoomed in_

`sizes.width / sizes.height = aspect ratio`

_* usually width of canvas divided by height

### d. Create renderer
*create after adding canvas in html

```Javascript 
const renderer = new THREE.WebGLRenderer({
    canvas: canvas
})

renderer.setSize(sizes.width, sizes.height)

renderer.render(scene, camera)
```

*After render to scene, you can't see the objet cause it's in 1,1,1 position
*Therefore you need to move backward of the camera

### Every object has a position in three.js, including camera
*Therefore move the position of camera
```javascript
camera.position.z = 3
```
_*position number = move backward_

## Create canvas in html
```HTML
<canvas class="webgl"></canvas>
```

in javascript you can select this DOM element using CSS selector, `querySelector`

```Javascript
const canvas = document.querySelector('canvas.webgl')
```
