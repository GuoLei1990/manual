# 粒子动画

Oasis Engine 的粒子渲染器[ParticleRenderer](${book.api}classes/core.particlerenderer.html) 是常用的渲染组件，具备丰富的属性，通过各个属性值达到绚丽多彩的粒子效果。

```typescript
let particles: ParticleRenderer = particleEntity.addComponent(ParticleRenderer);

particles.maxCount = 100;
particles.velocity = new Vector3(1, 1, 1);
particles.acceleration = new Vector3(-1, -1, -1);
particles.accelerationRandomness = new Vector3(-3, -3, -3);
particles.velocityRandomness = new Vector3(-1, -1, -1);
particles.rotateRate = 1;
particles.rotateRateRandomness = 1;
particles.size = 1;
particles.is2d = true;

// Start play
particleComp.start();

// Stop
particleComp.stop();
```

## 属性

粒子渲染器包含生命周期、纹理颜色、变换等属性。

### 基础属性 
- [`maxCount`](${book.api}classes/core.particlerenderer.html#maxcount)：最大粒子数，决定所占内存的大小，需要合理分配。

### 生命周期
- [`lifetime`](${book.api}classes/core.particlerenderer.html#lifetime)：粒子的生命周期，单位秒。
- [`startTimeRandomness`](${book.api}classes/core.particlerenderer.html#starttimerandomness)：开始时间随机因子。
- [`isOnce`](${book.api}classes/core.particlerenderer.html#isonce) ：是否只发射一次，默认 `false` （循环发射）。

### 纹理颜色
- [`texture`](${book.api}classes/core.particlerenderer.html#texture) ： 粒子形状贴图。
- [`color`](${book.api}classes/core.particlerenderer.html#color)：粒子颜色。
- [`colorRandomness`](${book.api})，颜色随机因子，取值在 0~1 之间，颜色的 R、G、B通道的色值会分别在随机因子范围内取一个随机值，然后截取在 0~1 范围内。
- [`isUseOriginColor`](${book.api}) ：是否使用图片原色，为 `true` (默认) 时使用图片原色，为 `false`  时，图片原色混合用户配置的颜色，可以在原图的基础上混合出任意的颜色：

  ![image.png](https://intranetproxy.alipay.com/skylark/lark/0/2019/png/161276/1566567187067-d4067842-c5b3-43f8-a936-395c628ce97c.png#align=left&display=inline&height=250&margin=%5Bobject%20Object%5D&name=image.png&originHeight=499&originWidth=1009&size=506372&status=done&style=none&width=504.5)

- [`alpha`](${book.api})：透明度。
- [`alphaRandomness`](${book.api})：透明度随机因子。
- [`fadeIn`](${book.api}) ：是否添加淡入效果。
- [`fadeOut`](${book.api}) ：是否添加淡出效果。

### 变换
- [`position`](${book.api}classes/core.particlerenderer.html#position) ：初始位置。
- [`positionRandomness`](${book.api}classes/core.particlerenderer.html#positionrandomness)：位置随机因子。
- [`positionArray`](${book.api}classes/core.particlerenderer.html#positionarray) ：位置数组。
- [`velocity`](${book.api}classes/core.particlerenderer.html#velocity) ：移动速度。
- [`velocityRandomness`](${book.api}classes/core.particlerenderer.html#velocityrandomness)：移动速度随机因子。
- [`acceleration`](${book.api}classes/core.particlerenderer.html#acceleration)：加速度。
- [`accelerationRandomness`](${book.api}core.particlerenderer.html#accelerationrandomness)：加速度随机因子。
- [`angle`](${book.api}classes/core.particlerenderer.html#angle): 初始旋转角度。
- [`angleRandomness`](${book.api}classes/core.particlerenderer.html#anglerandomness): 初始旋转角度随机因子，取值在 0~1 之间，例如：rotate 为 0，随机因子为 0，则生成的粒子角度均为 0，随机因子为 1，则生成的角度在 -PI~PI 之间随机。
- [`rotateVelocity`](${book.api}classes/core.particlerenderer.html#rotatevelocity): 旋转速度。
- [`rotateVelocityRandomness`](${book.api}classes/core.particlerenderer.html#rotatevelocityrandomness): 旋转速度随机因子。
- [`isRotateToVelocity`](${book.api}classes/core.particlerenderer.html#isrotatetovelocity)：是否跟随粒子运动速度的方向，默认 `false`，为 `true`  时，将粒子贴图的单位向量旋转至粒子运动速度的方向，例如烟花：

  ![xi.gif](https://intranetproxy.alipay.com/skylark/lark/0/2019/gif/161276/1566567277218-594ec692-7608-4b5a-8aff-05e6cea2b62f.gif#align=left&display=inline&height=385&margin=%5Bobject%20Object%5D&name=xi.gif&originHeight=489&originWidth=494&size=345464&status=done&style=none&width=389)

  为 `false` 时，无旋转，适用于方向一致的场景，例如孔明灯：

  ![xx.gif](https://intranetproxy.alipay.com/skylark/lark/0/2019/gif/161276/1566567330802-a71c903d-5f3c-4daa-a058-d076df2372ed.gif#align=left&display=inline&height=389&margin=%5Bobject%20Object%5D&name=xx.gif&originHeight=489&originWidth=494&size=1532055&status=done&style=none&width=393)

- [`is2d`](${book.api}classes/core.particlerenderer.html#is2d)：是否是 2D 粒子，默认 `true`。
- [`size`](${book.api}classes/core.particlerenderer.html#size)：粒子大小。
- [`sizeRandomness`](${book.api}classes/core.particlerenderer.html#sizerandomness)：粒子大小随机因子。
- [`scale`](${book.api}classes/core.particlerenderer.html#scale)：粒子缩放。
- [`isScaleByLifetime`](${book.api}classes/core.particlerenderer.html#isscalebylifetime) ：是否随生命周期缩小至消失。为 `true` 时粒子会越来越小，为 `false` 时粒子大小保持不变，只有透明度会降低，可用于制作淡出消失的效果：

  ![](https://gw.alipayobjects.com/zos/rmsportal/ZtxLeEHDUbWvGliQmWMu.gif#align=left&display=inline&height=534&margin=%5Bobject%20Object%5D&originHeight=638&originWidth=478&status=done&style=none&width=400) |