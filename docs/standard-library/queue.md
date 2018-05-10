---
title: '&lt;queue&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <queue>
dev_langs:
- C++
helpviewer_keywords:
- queue header
ms.assetid: 24fcf350-eb0e-48cf-9fef-978be1aeda1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ba139e2b50f1dd7c9887701a522a002173c21ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="ltqueuegt"></a>&lt;queue&gt;

定义模板类 priority_queue 和 queue 以及多个支持模板。

## <a name="syntax"></a>语法

```cpp
#include <queue>

```

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator!=](../standard-library/queue-operators.md#op_neq)|测试运算符左侧和右侧的 queue 对象是否不相等。|
|[operator<](../standard-library/queue-operators.md#op_lt)|测试运算符左侧的 queue 对象是否小于右侧的 queue 对象。|
|[operator\<=](../standard-library/queue-operators.md#op_gt_eq)|测试运算符左侧的 queue 对象是否小于或等于右侧的 queue 对象。|
|[operator==](../standard-library/queue-operators.md#op_eq_eq)|测试运算符左侧和右侧的 queue 对象是否相等。|
|[operator>](../standard-library/queue-operators.md#op_gt)|测试运算符左侧的 queue 对象是否大于右侧的 queue 对象。|
|[operator>=](../standard-library/queue-operators.md#op_gt_eq)|测试运算符左侧的 queue 对象是否大于或等于右侧的 queue 对象。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[queue 类](../standard-library/queue-class.md)|一个模板容器适配器类，它提供功能的限制，限制一些基本容器类型的前端和后端元素的访问权限。|
|[priority_queue 类](../standard-library/priority-queue-class.md)|一个模板容器适配器类，它提供功能的限制，限制一些基本容器类型顶端元素的访问权限，并且该类通常为最大类。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
