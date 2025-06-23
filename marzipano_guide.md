# Marzipano 使用指南

## 什么是 Marzipano？
Marzipano 是一个开源的 JavaScript 库，用于创建高性能的全景图展示。它支持多种全景图格式，并提供了丰富的 API 来控制视图、几何结构和交互。

---

## 使用步骤

1. **引入 Marzipano 库**  
   通过 CDN 或本地文件加载 Marzipano：
   ```html
   <script src="./script/marzipano.js"></script>
   ```

2. **创建 Viewer 对象**  
   Viewer 是全景图的核心容器，用于管理视图和场景：
   ```javascript
   var viewer = new Marzipano.Viewer(document.getElementById('pano'));
   ```

3. **定义图像源**  
   使用 `ImageUrlSource` 加载全景图：
   ```javascript
   var source = Marzipano.ImageUrlSource.fromString("./src/pano.jpg");
   ```

4. **设置几何结构**  
   定义全景图的几何结构（如 equirectangular 格式）：
   ```javascript
   var geometry = new Marzipano.EquirectGeometry([{ width: 4000 }]);
   ```

5. **限制视图范围**  
   设置视图的缩放和旋转限制：
   ```javascript
   var limiter = Marzipano.RectilinearView.limit.traditional(1024, 100 * Math.PI / 180);
   ```

6. **创建视图对象**  
   使用 `RectilinearView` 定义视图：
   ```javascript
   var view = new Marzipano.RectilinearView(null, limiter);
   ```

7. **创建场景并切换**  
   将图像源、几何结构和视图绑定到场景：
   ```javascript
   var scene = viewer.createScene({ source, geometry, view });
   scene.switchTo();
   ```

---

## 利用的 JavaScript 知识

1. **DOM 操作**  
   - 使用 `document.getElementById` 获取 HTML 元素。
   - 将全景图绑定到指定的容器。

2. **对象和方法调用**  
   - 使用 Marzipano 提供的类和方法（如 `Viewer`、`ImageUrlSource`、`EquirectGeometry`）。
   - 创建对象并调用方法来设置属性和行为。

3. **数学计算**  
   - 使用 `Math.PI` 进行角度转换。
   - 限制视图的旋转范围。

4. **模块化设计**  
   - Marzipano 的 API 设计体现了模块化思想，每个功能都通过独立的类和方法实现。

---

## 总结
Marzipano 是一个强大的工具，可以轻松实现全景图展示。通过结合 JavaScript 的 DOM 操作、对象方法调用和数学计算，你可以灵活地控制全景图的视图和交互。如果需要更复杂的功能，可以深入研究 Marzipano 的文档和 API。
