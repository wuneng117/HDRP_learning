# GPU Instancing

Instancing时设置VAO和VBO如下：

```cpp
// Generate VBO Ids and load the VBOs with data
glGenBuffers(2, m_VboIds);
glBindBuffer(GL_ARRAY_BUFFER, m_VboIds[0]);
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
// 绑定实例化数组，因为uniform长度有限
glBindBuffer(GL_ARRAY_BUFFER, m_VboIds[1]);
glBufferData(GL_ARRAY_BUFFER, sizeof(glm::vec3) * 125, &translations[0], GL_STATIC_DRAW);
glBindBuffer(GL_ARRAY_BUFFER, 0);

// Generate VAO Id
glGenVertexArrays(1, &m_VaoId);

glBindVertexArray(m_VaoId);
glBindBuffer(GL_ARRAY_BUFFER, m_VboIds[0]);
glEnableVertexAttribArray(0);
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (const void *) 0);
glEnableVertexAttribArray(1);
glVertexAttribPointer(1, 2, GL_FLOAT, GL_FALSE, 5 * sizeof(GLfloat), (const void *) (3* sizeof(GLfloat)));
glEnableVertexAttribArray(2);

//利用顶点属性来定义的实例化数组(Instanced Array)
glBindBuffer(GL_ARRAY_BUFFER, m_VboIds[1]);
glEnableVertexAttribArray(2);
glVertexAttribPointer(2, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(GLfloat), (GLvoid*)0);
glBindBuffer(GL_ARRAY_BUFFER, 0);
//指定 index=2 的属性为实例化数组，1 表示每绘制一个实例，更新一次数组中的元素
glVertexAttribDivisor(2, 1); // Tell OpenGL this is an instanced vertex attribute.
glBindVertexArray(GL_NONE);
```
