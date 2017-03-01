---
title: "Concurrency:: graphics Namespace |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics
- amp_short_vectors/Concurrency::graphics
dev_langs:
- C++
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: fd29b427307e336d560a2caf42e4fc5228e8071f
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 命名空间
图形命名空间提供的类型和用于图形编程的函数。  
  
## <a name="syntax"></a>语法  
  
```  
namespace graphics;  
```  
  
## <a name="members"></a>成员  
  
### <a name="namespaces"></a>命名空间  
  
|名称|说明|  
|----------|-----------------|  
|[Concurrency::graphics::direct3d Namespace](concurrency-graphics-direct3d-namespace.md)|提供用于 Direct3D 互操作函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|名称|说明|  
|----------|-----------------|  
|`uint`|元素类型[uint_2 类](uint-2-class.md)， [uint_3 类](uint-3-class.md)，和[uint_4 类](uint-4-class.md)。 定义为`typedef unsigned int uint;`。|  
  
### <a name="enumerations"></a>枚举  
  
|名称|说明|  
|----------|-----------------|  
|[address_mode 枚举](concurrency-graphics-namespace-enums.md#address_mode)。|指定地址模式支持纹理采样。|  
|[filter_mode 枚举](concurrency-graphics-namespace-enums.md#filter_mode)|指定支持纹理采样的筛选器模式。|  
  
### <a name="classes"></a>类  
  
|名称|描述|  
|----------|-----------------|  
|[texture 类](texture-class.md)|纹理是在扩展盘区域中的 accelerator_view 上聚合的数据。 它是变量，一个用于扩展盘区域中的每个元素的集合。 每个变量包含的值对应于 c + + 基元类型 (unsigned 的 int、 int、 float、 double)，或在 concurrency:: graphics 中定义的标量类型 norm 或 unorm （在 concurrency:: graphics 中定义） 或合格的短矢量类型。|  
|[writeonly_texture_view 类](writeonly-texture-view-class.md)|Writeonly_texture_view 提供对纹理 writeonly 访问。|  
|[double_2 类](double-2-class.md)|表示 2 的短矢量`double`值。|  
|[double_3 类](double-3-class.md)|表示 3 的短矢量`double`值。|  
|[double_4 类](double-4-class.md)|表示 4 的短矢量`double`值。|  
|[float_2 类](float-2-class.md)|表示 2 的短矢量`float`值。|  
|[float_3 类](float-3-class.md)|表示 3 的短矢量`float`值。|  
|[float_4 类](float-4-class.md)|表示 4 的短矢量`float`值。|  
|[int_2 类](int-2-class.md)|表示 2 的短矢量`int`值。|  
|[int_3 类](int-3-class.md)|表示 3 的短矢量`int`值。|  
|[int_4 类](int-4-class.md)|表示 4 的短矢量`int`值。|  
|[norm_2 类](norm-2-class.md)|表示 2 的短矢量`norm`值。|  
|[norm_3 类](norm-3-class.md)|表示 3 的短矢量`norm`值。|  
|[norm_4 类](norm-4-class.md)|表示 4 的短矢量`norm`值。|  
|[uint_2 类](uint-2-class.md)|表示 2 的短矢量`uint`值。|  
|[uint_3 类](uint-3-class.md)|表示 3 的短矢量`uint`值。|  
|[uint_4 类](uint-4-class.md)|表示 4 的短矢量`uint`值。|  
|[unorm_2 类](unorm-2-class.md)|表示 2 的短矢量`unorm`值。|  
|[unorm_3 类](unorm-3-class.md)|表示 3 的短矢量`unorm`值。|  
|[unorm_4 类](unorm-4-class.md)|表示 4 的短矢量`unorm`值。|  
|[sampler 类](sampler-class.md)|表示用于纹理采样的采样器配置。|  
|[short_vector 结构](short-vector-structure.md)|提供的值的短矢量的基本实现。|  
|[short_vector_traits 结构](short-vector-traits-structure.md)|提供用于检索的长度和短矢量类型。|  
|[texture_view 类](texture-view-class.md)|提供了读取访问权限和对纹理写访问权限。|  
  
### <a name="functions"></a>函数  
  
|名称|说明|  
|----------|-----------------|  
|[copy 函数](concurrency-graphics-namespace-functions.md#copy)|已重载。 将源纹理的内容复制到目标主机缓冲区。|  
|[copy_async 函数](concurrency-graphics-namespace-functions.md#copy_async)|已重载。 以异步方式将源纹理的内容复制到目标主机缓冲区。|  
  
## <a name="requirements"></a>要求  
 **标头︰** amp_graphics.h  
  
 **命名空间：** 并发  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

