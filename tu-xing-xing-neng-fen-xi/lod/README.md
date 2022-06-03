# LOD

## 一. 简介

**unity的官方文档就挺详细的**

{% embed url="https://docs.unity3d.com/cn/current/Manual/LevelOfDetail.html" %}

## 二. 和texture关系

通过观察unity的插件**Rocky Hills Environment - Pro**，在实现树的lod上：

* 网格模型：不同lod引用的是不同的fbx模型
* 纹理：除了最低级别的billboard外（1024x1024），其他模型用的都是同一张大贴图（4096x4096，真大！）
