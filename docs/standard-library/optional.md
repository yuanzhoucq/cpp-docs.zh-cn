---
title: '&lt;optional&gt;'
ms.date: 11/04/2016
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: c73ad2ad94a5de29bc2c457fdf6ca8b9c783615c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268479"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

定义容器模板类的可选和几个支持模板。

## <a name="requirements"></a>要求

**标头：** \<可选 >

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
> 关系进行比较，除了\<可选 > 运算符也支持与比较**nullopt**和`T`。

### <a name="functions"></a>函数

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|提供一个对象。|
|[swap](../standard-library/optional-functions.md#swap)||

### <a name="classes-and-structs"></a>类和结构

|||
|-|-|
|[hash]()||
|[可选类](../standard-library/optional-class.md)|描述一个对象，可能会或可能不能够保持一个值。|
|[nullopt_t 结构](../standard-library/nullopt-t-structure.md)|描述一个对象未保存的值。|
|[bad_optional_access 类](../standard-library/bad-optional-access-class.md)|描述作为异常来报告尝试访问不在那里一个值，引发的对象。|

### <a name="objects"></a>对象

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)||

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
