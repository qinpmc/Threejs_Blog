1. 基本材质 THREE.MeshBasicMaterial 不会对光源有任何反应（见 03-materials-light.html，03-materials-light2.html 对比）

2. 开启阴影耗费大量资源：

- renderer.shadowMap.enabled = true;
- cube.castShadow = true;
- sphere.castShadow = true;
- plane.receiveShadow = true;
- spotLight.castShadow = true; // 并不是所有的光源都可以产生阴影


3. mesh可以同时接受和投射阴影(03-materials-light3_测试阴影.html)：

```
  roofMesh.receiveShadow = true;
  baseMesh.receiveShadow = true;
  roofMesh.castShadow = true;
  baseMesh.castShadow = true;
```

4. 使得鼠标交互生效,initTrackballControls 放在 document.getElementById("webgl-output").appendChild(renderer.domElement) 后面才生效:

```
    // add the output of the renderer to the html element
    document.getElementById("webgl-output").appendChild(renderer.domElement);

    var clock = new THREE.Clock();
    // initialize the trackball controls and the clock which is needed ,
    var trackballControls = initTrackballControls(camera, renderer);

    function initTrackballControls(camera, renderer) {
    var trackballControls = new THREE.TrackballControls(camera, renderer.domElement);
    trackballControls.rotateSpeed = 1.0;
    trackballControls.zoomSpeed = 1.2;
    trackballControls.panSpeed = 0.8;
    trackballControls.noZoom = false;
    trackballControls.noPan = false;
    trackballControls.staticMoving = true;
    trackballControls.dynamicDampingFactor = 0.3;
    trackballControls.keys = [65, 83, 68];

    return trackballControls;
}

```

并且render 应当 循环执行：

```
    // call the render function
    render();

    function render(){
        trackballControls.update(clock.getDelta());
        // render using requestAnimationFrame
        requestAnimationFrame(render);
        // call the render function
        renderer.render(scene, camera);
    }

````