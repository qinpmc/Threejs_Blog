# Three.js notes  



## Three.js 渲染器


three.js 渲染器有:

- THREE.CanvasRenderer ,基于canvas2D的渲染器
- THREE.THREE.CSS2DRenderer ,基于canvas2D的渲染器
- THREE.CSS3DRenderer ,基于canvas2D的渲染器
- THREE.SVGRenderer，基于 SVG渲染的渲染器
- THREE.WebGLRenderer， 基于WebGL渲染的渲染器


## Three.js 相机


camera.position.set函数是设置当前相机的位置，函数传的三个值分别是x轴坐标，y轴坐标和z轴坐标。
相机默认的朝向是朝向0点坐标的，我们也可以设置相机的朝向。
 
```
var camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.1, 200); //实例化相机
camera.position.set(0, 0, 15);
```

- THREE.PerspectiveCamera 透视相机

## WebGL坐标系统

![WebGL坐标系统](./webgl.png)
WebGL坐标系统作为3D坐标， z轴的正方向是朝向屏幕向外，我们眼看去的方向是是z轴的负方向。


## Three.js 场景

场景只是作为一个容器，我们将需要显示的内容都放到场景对象当中。如果我们需要将一个模型放入到场景当中，则可以使用scene.add方法，如：


```
var scene = new THREE.Scene(); //实例化场景
scene.add(mesh); //添加一个网格（模型）到场景
```

## Three.js 模型（mesh）
创建一个网格（模型）需要两种对象：几何体和材质。

- 几何体：代表模型的形状，它是由固定的点的位置组成，点绘制出面，面组成了模型。
- 材质：是我们看到当前模型显示出来的效果，如显示的颜色，质感等。


```
var geometry = new THREE.BoxGeometry( 2, 2, 2 ); //创建几何体，长度，宽度和高度
var material = new THREE.MeshNormalMaterial(); //创建材质 MeshNormalMaterial根据面的朝向不同，显示不同的颜色
var mesh = new THREE.Mesh( geometry, material ); //创建网格
scene.add( mesh ); //将网格添加到场景
 
```


## Three.js的性能检测插件 stats.js

引入 stats.js：

```
<script src="http://www.wjceo.com/lib/js/libs/stats.min.js"></script>
```

使用 stats.js：

```
stats = new Stats();
document.body.appendChild(stats.dom);
stats.update(); //更新性能插件
```









