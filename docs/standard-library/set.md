---
title: '&lt;set&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <set>
dev_langs:
- C++
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aacfbda591755af86857da6c7d0b7891d2e72ebb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857046"
---
# <a name="ltsetgt"></a>&lt;set&gt;

定义容器模板类 set 和 multiset 及其支持的模板。

## <a name="syntax"></a>语法

```cpp
#include <set>

```

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|Set 版本|Multiset 版本|描述|
|-----------------|----------------------|-----------------|
|[operator!= (set)](../standard-library/set-operators.md#op_neq)|[operator!= (multiset)](../standard-library/set-operators.md#op_neq)|测试运算符左侧的 set 或 multiset 对象是否不等于右侧的 set 或 multiset 对象。|
|[operator< (set)](../standard-library/set-operators.md#op_lt)|[operator< (multiset)](../standard-library/set-operators.md#op_lt_multiset)|测试运算符左侧的 set 或 multiset 对象是否小于右侧的 set 或 multiset 对象。|
|[operator<= (set)](../standard-library/set-operators.md#op_lt_eq)|[operator\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|测试运算符左侧的 set 或 multiset 对象是否小于或等于右侧的 set 或 multiset 对象。|
|[operator== (set)](../standard-library/set-operators.md#op_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|测试运算符左侧的 set 或 multiset 对象是否等于右侧的 set 或 multiset 对象。|
|[operator> (set)](../standard-library/set-operators.md#op_gt)|[operator> (multiset)](../standard-library/set-operators.md#op_gt_multiset)|测试运算符左侧的 set 或 multiset 对象是否大于右侧的 set 或 multiset 对象。|
|[operator>= (set)](../standard-library/set-operators.md#op_gt_eq)|[operator>= (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|测试运算符左侧的 set 或 multiset 对象是否大于或等于右侧的 set 或 multiset 对象。|

### <a name="specialized-template-functions"></a>专用化模板函数

|Set 版本|Multiset 版本|描述|
|-----------------|----------------------|-----------------|
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|交换两个集或多个集的元素。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[set 类](../standard-library/set-class.md)|用于存储和检索集合中的数据，此集合中包含的元素值是唯一的，并且用作数据自动排序所依据的关键字值。|
|[multiset 类](../standard-library/multiset-class.md)|用于存储和检索集合中的数据，此集合中包含的元素值不必是唯一的，并且可用作数据自动排序所依据的关键字值。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
