---
title: '&lt;forward_list&gt;'
ms.date: 11/04/2016
f1_keywords:
- <forward_list>
helpviewer_keywords:
- <forward_list>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: a8b343fbe5e175828b4b8470da486a6dea9f3455
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457011"
---
# <a name="ltforwardlistgt"></a>&lt;forward_list&gt;

定义容器模板类 forward_list 和几个支持模板。

## <a name="requirements"></a>要求

**标头：** \<forward_list>

**命名空间：** std

> [!NOTE]
> Forward_list > 库还使用该`#include <initializer_list>`语句。 \<

## <a name="members"></a>成员

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
