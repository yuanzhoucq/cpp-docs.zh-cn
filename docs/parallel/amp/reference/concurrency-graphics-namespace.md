---
title: "Concurrency:: graphics Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AMP_GRAPHICS/Concurrency
dev_langs: C++
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aef7e219190584ec91b08e9c44b4c921ec91d787
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 命名空间
图形命名空间提供的类型和用于图形编程的函数。  
  
## <a name="syntax"></a>语法  
  
```  
namespace graphics;  
```  
  
## <a name="members"></a>成员  
  
### <a name="namespaces"></a>命名空间  
  
|名称|描述|  
|----------|-----------------|  
|[Concurrency::graphics::direct3d 命名空间](concurrency-graphics-direct3d-namespace.md)|提供了用于 Direct3D 互操作的函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`uint`|元素类型[uint_2 类](uint-2-class.md)， [uint_3 类](uint-3-class.md)，和[uint_4 类](uint-4-class.md)。 定义为`typedef unsigned int uint;`。|  
  
### <a name="enumerations"></a>枚举  
  
|name|描述|  
|----------|-----------------|  
|[address_mode 枚举](concurrency-graphics-namespace-enums.md#address_mode)。|指定地址模式支持纹理采样。|  
|[filter_mode 枚举](concurrency-graphics-namespace-enums.md#filter_mode)|指定支持纹理采样的筛选器模式。|  
  
### <a name="classes"></a>类  
  
|名称|描述|  
|----------|-----------------|  
|[texture 类](texture-class.md)|纹理是一种数据聚合范围域中的 accelerator_view 上。 它是变量，一个用于扩展盘区域中的每个元素的集合。 每个变量持有值对应于 c + + 基元类型 (无符号的 int、 int、 float、 double)，或在 concurrency:: graphics 中定义的标量类型 norm 或 unorm （在 concurrency:: graphics 中定义） 或符合条件的短矢量类型。|  
|[writeonly_texture_view 类](writeonly-texture-view-class.md)|Writeonly_texture_view 提供对纹理的 writeonly 访问。|  
|[double_2 类](double-2-class.md)|表示 2 短矢量`double`值。|  
|[double_3 类](double-3-class.md)|表示 3 短矢量`double`值。|  
|[double_4 类](double-4-class.md)|表示 4 短矢量`double`值。|  
|[float_2 类](float-2-class.md)|表示 2 短矢量`float`值。|  
|[float_3 类](float-3-class.md)|表示 3 短矢量`float`值。|  
|[float_4 类](float-4-class.md)|表示 4 短矢量`float`值。|  
|[int_2 类](int-2-class.md)|表示 2 短矢量`int`值。|  
|[int_3 类](int-3-class.md)|表示 3 短矢量`int`值。|  
|[int_4 类](int-4-class.md)|表示 4 短矢量`int`值。|  
|[norm_2 类](norm-2-class.md)|表示 2 短矢量`norm`值。|  
|[norm_3 类](norm-3-class.md)|表示 3 短矢量`norm`值。|  
|[norm_4 类](norm-4-class.md)|表示 4 短矢量`norm`值。|  
|[uint_2 类](uint-2-class.md)|表示 2 短矢量`uint`值。|  
|[uint_3 类](uint-3-class.md)|表示 3 短矢量`uint`值。|  
|[uint_4 类](uint-4-class.md)|表示 4 短矢量`uint`值。|  
|[unorm_2 类](unorm-2-class.md)|表示 2 短矢量`unorm`值。|  
|[unorm_3 类](unorm-3-class.md)|表示 3 短矢量`unorm`值。|  
|[unorm_4 类](unorm-4-class.md)|表示 4 短矢量`unorm`值。|  
|[sampler 类](sampler-class.md)|表示用于纹理采样的采样器配置。|  
|[short_vector 结构](short-vector-structure.md)|提供短矢量的值的基本实现。|  
|[short_vector_traits 结构](short-vector-traits-structure.md)|提供用于检索的长度和短矢量的类型。|  
|[texture_view 类](texture-view-class.md)|提供为纹理的写访问权限和读取访问权限。|  
  
### <a name="functions"></a>函数  
  
|名称|描述|  
|----------|-----------------|  
|[copy](concurrency-graphics-namespace-functions.md#copy)|已重载。 将源纹理的内容复制到目标主机缓冲区。|  
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|已重载。 以异步方式将源纹理的内容复制到目标主机缓冲区。|  
  
## <a name="requirements"></a>惠?  
 **标头：** amp_graphics.h  
  
 **命名空间：** 并发  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
