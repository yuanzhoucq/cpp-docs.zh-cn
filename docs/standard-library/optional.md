---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: 83a0ad52735f92d731dafb32ad1be5a8278776b4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447185"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

定义容器模板类可选和多个支持模板。

## <a name="requirements"></a>要求

**标头:** \<可选 >

**命名空间：** std

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|测试运算符左侧的 `optional` 对象是否等于右侧的 `optional` 对象。|
|[operator!=](../standard-library/optional-operators.md#op_neq)|测试运算符左侧的 `optional` 对象是否不等于右侧的 `optional` 对象。|
|[operator<](../standard-library/optional-operators.md#op_lt)|测试运算符左侧的 `optional` 对象是否小于右侧的 `optional` 对象。|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|测试运算符左侧的 `optional` 对象是否小于或等于右侧的 `optional` 对象。|
|[operator>](../standard-library/optional-operators.md#op_gt)|测试运算符左侧的 `optional` 对象是否大于右侧的 `optional` 对象。|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|测试运算符左侧的 `optional` 对象是否大于或等于右侧的 `optional` 对象。|

> [!NOTE]
> 除了关系比较外, \<可选的 > 运算符还支持与**nullopt**和`T`的比较。

### <a name="functions"></a>函数

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|使对象成为可选的。|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>类和结构

|||
|-|-|
|[hash]()||
|[可选类](../standard-library/optional-class.md)|描述一个对象, 该对象不能包含值。|
|[nullopt_t 结构](../standard-library/nullopt-t-structure.md)|描述不包含值的对象。|
|[bad_optional_access 类](../standard-library/bad-optional-access-class.md)|描述作为异常引发的对象, 以报告尝试访问不存在的值。|

### <a name="objects"></a>对象

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
