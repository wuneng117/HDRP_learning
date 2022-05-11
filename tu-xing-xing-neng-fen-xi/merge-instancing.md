# Merge - Instancing

在Instancing技术上实现不同instancing的合批渲染。

先把不同模型的顶点和索引合并成1个大模型，每个模型自己的独特数据也合并在一起，接下来解决的是大模型里的每个模型读取自己的独特数据，这里要用到gl\_VertexID。

{% hint style="info" %}
`gl_VertexID` is always going to be the logical index of the respective vertex in the sequence of primitives specified by your draw call (effectively the index from where in a vertex buffer the vertex data would be read).&#x20;
{% endhint %}

简单来讲就是告诉你这是这次绘制中的第几个vertex，保证每个模型的索引长度一致，那么通过这个值你是可以计算当前是大模型里的第几个模型，是否需要切换独特数据的，每个模型的索引不一致的话要计算每个模型占用多少个索引，因为shader没有上下文的，可能不能计算（需要实际确定下）
