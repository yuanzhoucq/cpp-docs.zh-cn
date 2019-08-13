---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: f3b4896a3cb4774e46b36480dd9769fa131fc287
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957175"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

定义容器模板类 `optional` 和几个支持模板。

## <a name="requirements"></a>要求

**标头:** \<可选 >

**命名空间：** std

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|测试一个对象是否等于另一个对象。|
|[operator!=](../standard-library/optional-operators.md#op_neq)|测试一个对象是否不等于另一个对象。|
|[operator<](../standard-library/optional-operators.md#op_lt)|测试左侧的对象是否小于右侧的对象。|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|测试左侧的对象是否小于或等于右侧的对象。|
|[operator>](../standard-library/optional-operators.md#op_gt)|测试左侧的对象是否大于右侧的对象。|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|测试左侧的对象是否大于或等于右侧的对象。|

> [!NOTE]
> 除了关系比较外, \<可选的 > 运算符还支持与**nullopt**和`T`的比较。

### <a name="functions"></a>函数

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|使对象成为可选的。|
|[swap](../standard-library/optional-functions.md#swap)|交换两个`optional`对象的包含值。|

### <a name="classes-and-structs"></a>类和结构

|||
|-|-|
|hash|返回所包含的对象的哈希值。|
|[可选类](../standard-library/optional-class.md)|描述一个对象, 该对象不能包含值。|
|[nullopt_t 结构](../standard-library/nullopt-t-structure.md)|描述不包含值的对象。|
|[bad_optional_access 类](../standard-library/bad-optional-access-class.md)|描述作为异常引发的对象, 以报告尝试访问不存在的值。|

### <a name="objects"></a>对象

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|`nullopt_t`用于比较的实例。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
