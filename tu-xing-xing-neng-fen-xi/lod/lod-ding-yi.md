# lod定义

lod实现主要有2种方式：

离散lod（discrete levels of detail）在游戏里常用到

连续lod（contunious leves of detail），几何着色器内用？

**wiki的解释**

{% hint style="info" %}
The first method, **Discrete Levels of Detail (DLOD)**, involves creating multiple, discrete versions of the original geometry with decreased levels of geometric detail. At runtime, the full-detail models are substituted for the models with reduced detail as necessary. Due to the discrete nature of the levels, there may be visual [popping](https://en.wikipedia.org/wiki/Popping\_\(computer\_graphics\)) when one model is exchanged for another. This may be mitigated by [alpha blending](https://en.wikipedia.org/wiki/Alpha\_blending) or [morphing](https://en.wikipedia.org/wiki/Morphing) between states during the transition.

The second method, **Continuous Levels of Detail (CLOD)**, uses a structure which contains a continuously variable spectrum of geometric detail. The structure can then be probed to smoothly choose the appropriate level of detail required for the situation. A significant advantage of this technique is the ability to locally vary the detail; for instance, the side of a large object nearer to the view may be presented in high detail, while simultaneously reducing the detail on its distant side.

In both cases, LODs are chosen based on some heuristic which is used to judge how much detail is being lost by the reduction in detail, such as by evaluation of the LOD's geometric error relative to the full-detail model. Objects are then displayed with the minimum amount of detail required to satisfy the heuristic, which is designed to minimize geometric detail as much as possible to maximize performance while maintaining an acceptable level of visual quality.
{% endhint %}
