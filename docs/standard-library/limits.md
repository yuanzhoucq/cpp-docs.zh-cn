---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: e23c47b3eaecec92e462af7b2cc47627c5bad86a
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245316"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定义模板类 `numeric_limits` 以及两个有关浮点表示形式和舍入的枚举。

## <a name="requirements"></a>要求

**标头：** \<limits>

**命名空间：** std

## <a name="remarks"></a>备注

显式专用化`numeric_limits`类描述的基本类型，包括字符、 整数和浮点类型的许多属性和**bool**是实现定义而不是通过修复规则的C++语言。 \<limits> 中描述的属性包括准确性、最小和最大尺寸表示形式、舍入和信号类型错误。

## <a name="members"></a>成员

### <a name="enumerations"></a>枚举

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|此枚举描述实现可以选择用于表示非标准化浮点值的各种方法，这种浮点值由于太小而无法表示为规范化值：|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|此枚举描述实现可以选择用于将浮点值舍入为整数值的各种方法。|

### <a name="classes"></a>类

|||
|-|-|
|[numeric_limits 类](../standard-library/numeric-limits-class.md)|该模板类描述内置数字类型的算术属性。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
