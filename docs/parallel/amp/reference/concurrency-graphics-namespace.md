---
title: Concurrency::graphics 命名空间
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: 942b3bbace85fa297bba6cd4b509f67006a4aed3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226732"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 命名空间

Graphics 命名空间提供了为图形编程设计的类型和函数。

## <a name="syntax"></a>语法

```cpp
namespace graphics;
```

## <a name="members"></a>成员

### <a name="namespaces"></a>命名空间

|名称|说明|
|----------|-----------------|
|[Concurrency：： graphics：:d irect3d 命名空间](concurrency-graphics-direct3d-namespace.md)|为 Direct3D 互操作提供函数。|

### <a name="typedefs"></a>Typedef

|名称|说明|
|----------|-----------------|
|`uint`|[Uint_2 类](uint-2-class.md)、 [uint_3 类](uint-3-class.md)和[uint_4 类](uint-4-class.md)的元素类型。 定义为 `typedef unsigned int uint;`。|

### <a name="enumerations"></a>枚举

|名称|说明|
|----------|-----------------|
|[Address_mode 枚举](concurrency-graphics-namespace-enums.md#address_mode)。|指定纹理采样支持的地址模式。|
|[filter_mode 枚举](concurrency-graphics-namespace-enums.md#filter_mode)|指定纹理采样支持的筛选模式。|

### <a name="classes"></a>类

|“属性”|说明|
|----------|-----------------|
|[纹理类](texture-class.md)|纹理是在范围域中的 accelerator_view 上的数据聚合。 它是变量集合，每个元素对应于一个范围域中的一个元素。 每个变量都包含与 c + + 基元类型（无符号 int、int、float、double）或标量类型的标准或 unorm （在 concurrency：： graphics 中定义）或在 concurrency：： graphics 中定义的符合条件的短矢量类型相对应的值。|
|[writeonly_texture_view 类](writeonly-texture-view-class.md)|Writeonly_texture_view 提供对纹理的 writeonly 访问。|
|[double_2 类](double-2-class.md)|表示2值的短矢量 **`double`** 。|
|[double_3 类](double-3-class.md)|表示3值的短矢量 **`double`** 。|
|[double_4 类](double-4-class.md)|表示四个值的短矢量 **`double`** 。|
|[float_2 类](float-2-class.md)|表示2值的短矢量 **`float`** 。|
|[float_3 类](float-3-class.md)|表示3值的短矢量 **`float`** 。|
|[float_4 类](float-4-class.md)|表示四个值的短矢量 **`float`** 。|
|[int_2 类](int-2-class.md)|表示2值的短矢量 **`int`** 。|
|[int_3 类](int-3-class.md)|表示3值的短矢量 **`int`** 。|
|[int_4 类](int-4-class.md)|表示四个值的短矢量 **`int`** 。|
|[norm_2 类](norm-2-class.md)|表示2值的短矢量 `norm` 。|
|[norm_3 类](norm-3-class.md)|表示3值的短矢量 `norm` 。|
|[norm_4 类](norm-4-class.md)|表示四个值的短矢量 `norm` 。|
|[uint_2 类](uint-2-class.md)|表示2值的短矢量 `uint` 。|
|[uint_3 类](uint-3-class.md)|表示3值的短矢量 `uint` 。|
|[uint_4 类](uint-4-class.md)|表示四个值的短矢量 `uint` 。|
|[unorm_2 类](unorm-2-class.md)|表示2值的短矢量 `unorm` 。|
|[unorm_3 类](unorm-3-class.md)|表示3值的短矢量 `unorm` 。|
|[unorm_4 类](unorm-4-class.md)|表示四个值的短矢量 `unorm` 。|
|[采样器类](sampler-class.md)|表示用于纹理采样的采样器配置。|
|[short_vector 结构](short-vector-structure.md)|提供值的简短向量的基本实现。|
|[short_vector_traits 结构](short-vector-traits-structure.md)|用于检索短向量的长度和类型。|
|[texture_view 类](texture-view-class.md)|提供对纹理的读访问和写访问权限。|

### <a name="functions"></a>函数

|名称|说明|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|已重载。 将源纹理的内容复制到目标主机缓冲区。|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|已重载。 以异步方式将源纹理的内容复制到目标主机缓冲区。|

## <a name="requirements"></a>要求

**标头：** amp_graphics。h

**命名空间：** 并发

## <a name="see-also"></a>另请参阅

[并发命名空间（C++ AMP）](concurrency-namespace-cpp-amp.md)
