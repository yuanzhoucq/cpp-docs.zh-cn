---
title: '&lt;queue&gt;'
ms.date: 11/04/2016
f1_keywords:
- <queue>
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
ms.openlocfilehash: d7a13b98ba8cff78839b2afb98371ffba5ced461
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458339"
---
# <a name="ltqueuegt"></a>&lt;queue&gt;

定义模板类 priority_queue 和 queue 以及多个支持模板。

## <a name="requirements"></a>要求

**标头：** \<queue>

**命名空间：** std

> [!NOTE]
> 队列 > 库也使用该`#include <initializer_list>`语句。 \<

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|||
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|测试运算符左侧和右侧的 queue 对象是否不相等。|
|[operator<](../standard-library/queue-operators.md#op_lt)|测试运算符左侧的 queue 对象是否小于右侧的 queue 对象。|
|[operator\<=](../standard-library/queue-operators.md#op_gt_eq)|测试运算符左侧的 queue 对象是否小于或等于右侧的 queue 对象。|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|测试运算符左侧和右侧的 queue 对象是否相等。|
|[operator>](../standard-library/queue-operators.md#op_gt)|测试运算符左侧的 queue 对象是否大于右侧的 queue 对象。|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|测试运算符左侧的 queue 对象是否大于或等于右侧的 queue 对象。|

### <a name="functions"></a>函数

|||
|-|-|
|[swap]()||

### <a name="classes"></a>类

|||
|-|-|
|[queue 类](../standard-library/queue-class.md)|一个模板容器适配器类，它提供功能的限制，限制一些基本容器类型的前端和后端元素的访问权限。|
|[priority_queue 类](../standard-library/priority-queue-class.md)|一个模板容器适配器类，它提供功能的限制，限制一些基本容器类型顶端元素的访问权限，并且该类通常为最大类。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)
