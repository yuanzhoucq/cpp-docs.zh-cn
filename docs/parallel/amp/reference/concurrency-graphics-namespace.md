---
title: Concurrency::graphics 命名空间
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: 5bff3bbba3c2ba9e6c51ee20c8701c80a557707f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500485"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 命名空间

图像命名空间提供类型和为图形编程设计的功能。

## <a name="syntax"></a>语法

```
namespace graphics;
```

## <a name="members"></a>成员

### <a name="namespaces"></a>命名空间

|名称|描述|
|----------|-----------------|
|[Concurrency::graphics::direct3d 命名空间](concurrency-graphics-direct3d-namespace.md)|提供 Direct3D 互操作功能。|

### <a name="typedefs"></a>Typedef

|名称|描述|
|----------|-----------------|
|`uint`|元素类型[uint_2 类](uint-2-class.md)， [uint_3 类](uint-3-class.md)，并[uint_4 类](uint-4-class.md)。 定义为`typedef unsigned int uint;`。|

### <a name="enumerations"></a>枚举

|name|描述|
|----------|-----------------|
|[address_mode 枚举](concurrency-graphics-namespace-enums.md#address_mode)。|指定纹理采样支持的地址模式。|
|[filter_mode 枚举](concurrency-graphics-namespace-enums.md#filter_mode)|指定纹理采样支持的筛选器模式。|

### <a name="classes"></a>类

|名称|描述|
|----------|-----------------|
|[texture 类](texture-class.md)|纹理是在范围域中的 accelerator_view 上的数据聚合。 它是变量，一个用于在范围域中的每个元素的集合。 每个变量包含一个值，该值对应于 c + + 基元类型 （无符号的整型、 整型、 浮点、 双精度），或在 concurrency:: graphics 中定义的标量类型 norm 或 unorm （在 concurrency:: graphics 中定义） 或合格短向量类型。|
|[writeonly_texture_view 类](writeonly-texture-view-class.md)|Writeonly_texture_view 提供对纹理的 writeonly 访问。|
|[double_2 类](double-2-class.md)|表示 2 的短矢量`double`值。|
|[double_3 类](double-3-class.md)|表示 3 的短矢量`double`值。|
|[double_4 类](double-4-class.md)|表示 4 短矢量`double`值。|
|[float_2 类](float-2-class.md)|表示 2 的短矢量`float`值。|
|[float_3 类](float-3-class.md)|表示 3 的短矢量`float`值。|
|[float_4 类](float-4-class.md)|表示 4 短矢量`float`值。|
|[int_2 类](int-2-class.md)|表示 2 的短矢量`int`值。|
|[int_3 类](int-3-class.md)|表示 3 的短矢量`int`值。|
|[int_4 类](int-4-class.md)|表示 4 短矢量`int`值。|
|[norm_2 类](norm-2-class.md)|表示 2 的短矢量`norm`值。|
|[norm_3 类](norm-3-class.md)|表示 3 的短矢量`norm`值。|
|[norm_4 类](norm-4-class.md)|表示 4 短矢量`norm`值。|
|[uint_2 类](uint-2-class.md)|表示 2 的短矢量`uint`值。|
|[uint_3 类](uint-3-class.md)|表示 3 的短矢量`uint`值。|
|[uint_4 类](uint-4-class.md)|表示 4 短矢量`uint`值。|
|[unorm_2 类](unorm-2-class.md)|表示 2 的短矢量`unorm`值。|
|[unorm_3 类](unorm-3-class.md)|表示 3 的短矢量`unorm`值。|
|[unorm_4 类](unorm-4-class.md)|表示 4 短矢量`unorm`值。|
|[sampler 类](sampler-class.md)|表示用于纹理采样的采样器配置。|
|[short_vector 结构](short-vector-structure.md)|提供了短向量值的基本实现。|
|[short_vector_traits 结构](short-vector-traits-structure.md)|提供用于检索的长度和短矢量类型。|
|[texture_view 类](texture-view-class.md)|提供了读取访问权限和写入访问权限给纹理。|

### <a name="functions"></a>函数

|名称|描述|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|已重载。 将源纹理的内容复制到目标托管缓冲区。|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|已重载。 以异步方式将源纹理的内容复制到目标托管缓冲区。|

## <a name="requirements"></a>要求

**标头：** amp_graphics.h

**命名空间：** 并发

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
