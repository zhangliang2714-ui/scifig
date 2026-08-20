# Blender参考图约束重构规范

## 目标

Blender在本 Skill 中不是用来“凭文字生成一个大致像的3D图”，而是用来把参考图中已经确定的轮廓、方向、密度、接触关系和结构层级重新参数化。2D参考图通常不能唯一确定3D结构，因此无法从单张图片推断的深度、晶体学占位或真实配位数必须标记为“示意假设”，不能伪装成实验事实。

## 建模前的结构契约

每个模型开始前建立以下参数表：

| 参数 | 内容 |
|---|---|
| silhouette | 参考图外轮廓、长宽比和主要边界 |
| orientation | 纤维、晶界、裂纹或配体的主方向 |
| density | 对象数量、密排程度、孔隙率或体积分数 |
| hierarchy | 基体、局域有序、第二相、孔隙、界面之间的层级 |
| camera | 正交/透视、旋转、焦距、裁切范围 |
| lighting | 主光方向、阴影强度、材质粗糙度和背景 |
| uncertain | 只能作为示意假设的深度或内部细节 |

没有完成这张表，不进入复杂节点搭建。

## 固定渲染条件

优先使用正交相机或弱透视相机，固定以下变量：

```python
SEED = 2714
CAMERA_TYPE = "ORTHO"       # 参考图为平面示意时的默认值
BACKGROUND_ALPHA = 0.0
RENDER_ENGINE = "BLENDER_EEVEE_NEXT"
```

所有程序化分布使用固定种子；模型结构改变时只改变明确的参数，不允许每次渲染都重新生成随机晶粒、纤维或颗粒。相机、光照、色彩管理和透明背景设置在同一套模板中复用。

## 五类可复用模板

### 1. `polymer_fiber`

用 `Curve` 或细长圆柱表达连续、实心、方向明确的聚合物前驱体纤维。可调参数包括长度、直径、弯曲幅度、方向和颜色。不加入内部线网，除非正文明确提出聚合物内部网络。

### 2. `coordination_network`

用金属中心球、配体曲线和桥联连接表达配位网络。先生成中心点和连接表，再用 `Curve to Mesh` 生成配体/键；通过颜色、半径和连接数区分金属中心、双齿配体和多羧酸桥联。不能用随机线团替代化学连接关系。

### 3. `packed_grains_with_boundary_pores`

采用 Voronoi/受约束点集或预制多面体实现晶粒搭接与密排。孔隙只放在晶界、三叉结和接触不完全区域；不得绘制成悬浮在晶粒内部的白点。通过晶粒尺度分布、边界颈化和孔隙率控制组织状态。

### 4. `local_order_and_second_phase`

局域有序在基体内部表现为有限范围的占位或配位相关区域；第二相必须有独立边界、较大尺度和不同材质。若文字表达“竞争相异常长大”，第二相应具有明显粗化、偏聚或各向异性长大特征。

### 5. `sintered_fiber_node`

先生成两根或多根真实接触的纤维，再在接触处生成烧结颈。通过颈径比、接触面积和融合程度控制弱接触、适度颈化和强烧结，不得把节点画成漂浮球或远离纤维的独立块体。

## Geometry Nodes核心节点

优先使用以下节点保持结构可控：

- 纤维：`Curve Line`、`Resample Curve`、`Set Position`、`Curve to Mesh`、`Align Euler to Vector`；
- 实例：`Mesh to Points`、`Instance on Points`、`Realize Instances`、`Random Value`（必须连接固定种子）；
- 晶粒：受约束点集、`Voronoi Texture`、`Mesh to Volume`、`Volume to Mesh`；
- 连接：`Curve to Mesh`、`Join Geometry`、`Raycast`、`Sample Index`；
- 缺陷与孔隙：通过边界筛选和布尔/体积操作放置，不使用完全随机散点。

## 参考图对照循环

每个模型至少输出三张预览：

1. 原始参考图；
2. Blender透明背景渲染；
3. 参考图与渲染图的50%透明度叠加图。

按以下顺序修正：外轮廓 → 主方向 → 对象数量与密度 → 接触/边界关系 → 颜色与材质 → 内部细节。不得先调材质而忽略轮廓和结构关系。

## 交付参数

每个可复用模型应记录：

```text
template_name:
seed:
camera_type:
camera_rotation:
object_scale:
orientation_axis:
grain_or_fiber_density:
second_phase_fraction:
pore_fraction:
neck_radius_ratio:
uncertain_assumptions:
```

如果暂时没有真正的 `.blend` 模板文件，至少交付以上参数契约和可复现脚本；不能把一张不可编辑的渲染图称为参数化模板。
