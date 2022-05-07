# 基础

![范例](<../.gitbook/assets/image (1) (1).png>)

上图出自unity插件Rocky Hills Environment - Pro Pack 2.1的场景RHESecene\_UnityTerrain\_Summer，在build成exe后运行的性能分析，没有优化。每帧耗时23ms。

* 3.4k的dc中有1.6k是透明度计算

在网络上关于pc游戏的drawcall其实很少，有个参考《死亡搁浅》1688，《ff14》8k，主要还是看着色器复杂度。



