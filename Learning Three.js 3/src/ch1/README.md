
1. 基本材质THREE.MeshBasicMaterial不会对光源有任何反应（见03-materials-light.html，03-materials-light2.html 对比）

2. 开启阴影耗费大量资源：


- renderer.shadowMap.enabled = true;
- cube.castShadow = true;
- sphere.castShadow = true;
- plane.receiveShadow = true;
- spotLight.castShadow = true; // 并不是所有的光源都可以产生阴影

