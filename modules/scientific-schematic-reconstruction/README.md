# 科研机制图重构 Skill

这是一个专门将 AI 生成图片或参考科研图片，使用 Blender、SVG、Python 等工具重构为科学、可编辑、可复现科研机制图的 Codex Skill。它适用于项目申请书技术路线图、多尺度材料示意图和机制图，不是简单的图片放大或风格滤镜工具。

直接调用：

```text
使用 $scientific-schematic-reconstruction 重构这张科研机制图。
```

标准流程是：先明确科学结论和区域含义，再切分总图、建立线框、判断 SVG/Python/Blender 分工，随后逐区构建、单独预览、统一嵌入，并在最终尺寸下检查字体、线宽、比例、科学表达和输出文件。

适用对象包括纤维、晶粒、配位网络、局域有序、第二相、孔隙、界面、裂纹和数据图。详细使用说明见 `references/workflow.md`，验收清单见 `references/qa-and-pitfalls.md`。
