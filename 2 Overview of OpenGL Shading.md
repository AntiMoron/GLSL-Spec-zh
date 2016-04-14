OpenGL Shading Language(下文GLSL)实际是几个密切关联的语言。这些语言被用来对每个OpenGL加工管线所包含的可编程处理器创建shaders。
当前，这些处理器是vertex, tessellation control, tessellation evaluation, geometry, fragment,和compute processors.

大多数OpenGL阶段不被追踪或者使其对shaders可获得。典型地，用户定义的变量会被用来在OpenGL管线的不同的阶段来进行交互。
但是，小数量的状态不是这样，有少数的内建变量作为不同OpenGL管线阶段间的接口。

# 2.1 Vertex Process

Vertex Processor是一个操作输入的顶点以及他们相关数据的可编程单元。用来运行在这个处理器上的GLSL编写的编译单元叫做
vertex shader. 当一组vertex shaders成功被编译并且链接，他们会生成一个vertex shader的可执行程序运行在vertex processor上。

Vertex processor一次操作一个顶点。他不替换需要一次知道多个顶点的图形操作。

# 2.2 Tessellation Control Processor

光栅控制处理器，Tessellation Control processor是一个操作一组输入顶点和关联数据并说出一组新的顶点的可编程单元。对应的
GLSL叫做tessellation control shaders.当一组该shader成功编译并链接，会生成一个运行在本处理器上的tessellation control shader可执行文件。

Tessellation control shader对于每一组输出都会被调用。每次调用可以读输入或者输出的任何顶点的属性。