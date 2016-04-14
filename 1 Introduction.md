# 介绍

本文档只说明4.40版本的GLSL。 需要__VERSION__来代替440，需要#version来只接受440.如果#version用一个小一些的数字
声明，所接受的语言是当前文档描述的GLSL的早期版本，会依赖OpenGL API的版本和类型来支持。详情见OpenGL Graphics System
文档，版本4.4来了解哪些语言版本被支持。

早起OpenGL Shading Language，也就是OpenGL ES Shading Language，并不是严格的4.4版本GLSL的子集，尤其是精度、命名隐藏规则，
以及接口变量的处理。详情见对应版本GLSL的说明。

在本说明中引用的所有OpenGL Graphics System说明都是指4.4版本的。

# 1.1 致谢

本文档基于对老版本OpenGL语言说明的贡献者的成果、OpenGL ES 2.0语言说明文档以及下面对于本版本的贡献者：

- Pat Brown, NVIDIA
- Jeff Bolz, NVIDIA
- Frank Chen
- Pierre Boudier, AMD
- Piers Daniell, NVIDIA
- Chris Dodd, NVIDIA
- Nick Haemel, NVIDIA
- Jason Green, TransGaming
- Brent Insko, Intel
- Jon Leech
- Bill Licea-Kane, AMD
- Daniel Koch, TransGaming
- Graeme Leese, Broadcom
- Barthold Lichtenbelt, NVIDIA
- Bruce Merry, ARM
- Robert Ohannessian
- Tom Olson, ARM
- Acorn Pooley, NVIDIA
- Christophe Riccio, AMD
- Kevin Rogovin
- Ian Romanick, Intel
- Greg Roth, Nvidia
- Graham Sellers, AMD
- Dave Shreiner, ARM
- Jeremy Sandmel, Apple
- Robert Simpson, Qualcomm
- Eric Werness, NVIDIA
- Mark Young, AMD

# 1.2 变化

## 1.2.1 自从GLSL 4.40的第八次修订版本以来的变化

## 1.2.2 自从GLSL 4.40的第七次修订版本以来的变化

## 1.2.3 自从GLSL 4.40的第六次修订版本以来的变化

# 1.3 概览

本文档描述了GLSL 4.40版本。

在本语言中独立的编译单元叫做shaders.一个program是一个编译并链接的shader的集合，完全创建一个或多个可编程
OpenGL管线。对于一个单独的可编程阶段所有的shader一定要在同一个program内。一个完成的编程阶段集合可以被放入一个
单独的program或者该阶段可以跨越多个program进行分段。本文档的主旨是为了彻底地说明本编程语言。
The OpenGL Graphics System说明书会说明OpenGL用来操作、和programs、shaders交互的入口点。

# 1.4 错误处理

编译器，通常讲，出于检测所有ill-formed程序不太可能的原因，通常会接受ill-formed的程序。可移植对于well-formed程序来说
是必须的，也是本说明描述的内容。编译器鼓励来检测ill-formed程序并且会发出诊断信息，但是并不是对于所有情况都需要这样做。
编译期错误对于词法、或者语法错误的shader来说是一定会被返回的。其他错误在编译时期或者链接期被指出。
僵尸代码仍然会被错误检查，例如：

```
if(false) // 把其从false改成true不会发现额外的错误
    statemend; // 不管怎样语句一定会被错误检查
```

# 1.5 印刷约定

略

# 1.6 废除内容

OpenGL Shading Language废除了一些特性。这些在本说明中明确地被称为“deprecated”。在本版本GLSL中他们
仍然可以用，但是被标记为在GLSL将来版本可能会被移除。OpenGL API有一个向下兼容的模式会禁止使用这些被废除的特性。
如果在废除特性不允许的模式下编译，这些使用会导致编译期或者链接期的错误。详情见OpenGL Graphics System说明
怎么让废除的特性通过编译或者刻意地编译期报错。