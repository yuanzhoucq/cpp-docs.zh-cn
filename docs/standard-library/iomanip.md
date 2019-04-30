---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: 983fbc190fb83b81534e3888c748c0bf9c235638
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404931"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

包括`iostreams`标准标头\<iomanip > 来定义多个操控器各自采用单个参数。

## <a name="syntax"></a>语法

```cpp
#include <iomanip>
```

## <a name="remarks"></a>备注

每个操控器返回未指定的类型，称为`T1`通过`T10`，该重载同时`basic_istream` \< **Elem**， **Tr** >`::`[运算符 >>](../standard-library/istream-operators.md#op_gt_gt)并`basic_ostream` \< **Elem**， **Tr** > `::` [运算符 <<](../standard-library/ostream-operators.md#op_lt_lt)。

### <a name="manipulators"></a>操控器

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|获取货币金额（可选择采用国际格式）。|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|使用指定格式以某种时间结构获取时间。|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|提供货币金额（可选择采用国际格式）。|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|采用要使用的时间结构和格式字符串提供时间。|
|[quoted](../standard-library/iomanip-functions.md#quoted)|使用插入和提取运算符实现字符串的方便往返。|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|清除指定标志。|
|[setbase](../standard-library/iomanip-functions.md#setbase)|为整数设置基数。|
|[setfill](../standard-library/iomanip-functions.md#setfill)|设置用于在右对齐显示中填充空格的字符。|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|设置指定标志。|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|为浮点值设置精度。|
|[setw](../standard-library/iomanip-functions.md#setw)|指定显示字段的宽度。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
