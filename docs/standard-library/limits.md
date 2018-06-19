---
title: '&lt;limits&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- limits/std::<limits>
- <limits>
dev_langs:
- C++
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3250d9a090dcbd5eaa9a3cc0d51df84600ed3e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912870"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定义模板类 `numeric_limits` 以及两个有关浮点表示形式和舍入的枚举。

## <a name="syntax"></a>语法

```cpp
#include <limits>

```

## <a name="remarks"></a>备注

`numeric_limits` 类的显式专用化描述基本类型（包括字符、整数、浮点类型和由实现定义而非由 C++ 语言规则固定的 `bool`）的许多属性。 \<limits> 中描述的属性包括准确性、最小和最大尺寸表示形式、舍入和信号类型错误。

### <a name="enumerations"></a>枚举

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|此枚举描述实现可以选择用于表示非标准化浮点值的各种方法，这种浮点值由于太小而无法表示为规范化值：|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|此枚举描述实现可以选择用于将浮点值舍入为整数值的各种方法。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[numeric_limits 类](../standard-library/numeric-limits-class.md)|该模板类描述内置数字类型的算术属性。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
