---
title: '&lt;forward_list&gt;'
ms.date: 11/04/2016
f1_keywords:
- <forward_list>
helpviewer_keywords:
- <forward_list>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: 708e16cb4b8a1640f4978b806bc52beed24decd4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688061"
---
# <a name="ltforward_listgt"></a>&lt;forward_list&gt;

定义容器类模板 forward_list 和多个支持模板。

## <a name="requirements"></a>要求

**标头：** \<forward_list>

**命名空间:** std

> [!NOTE]
> > 库 \<forward_list 也使用了 `#include <initializer_list>` 语句。

## <a name="members"></a>Members

### <a name="operators"></a>运算符

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|测试运算符左侧的转发列表对象是否等于右侧的转发列表对象。|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|测试运算符左侧的转发列表对象是否不等于右侧的转发列表对象。|
|[operator<](../standard-library/forward-list-operators.md#op_lt)|测试运算符左侧的转发列表对象是否小于右侧的转发列表对象。|
|[operator<=](../standard-library/forward-list-operators.md#op_lt_eq)|测试运算符左侧的转发列表对象是否小于或等于右侧的转发列表对象。|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|测试运算符左侧的转发列表对象是否大于右侧的转发列表对象。|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|测试运算符左侧的转发列表对象是否大于或等于右侧的转发列表对象。|

### <a name="functions"></a>函数

|||
|-|-|
|[swap](../standard-library/forward-list-functions.md#swap)|交换两个转发列表的元素。|

### <a name="classes"></a>类

|||
|-|-|
|[forward_list](../standard-library/forward-list-class.md)|描述用于控制变长元素序列的对象。 序列存储为元素的单向链接列表，其中每个节点都包含 `Type` 类型的成员。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
