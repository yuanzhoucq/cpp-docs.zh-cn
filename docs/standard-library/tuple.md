---
title: '&lt;tuple&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <tuple>
dev_langs:
- C++
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ba25328b86a51e34cba60bd55b63ce2eab696d6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="lttuplegt"></a>&lt;tuple&gt;

定义了一个模板 `tuple`它的实例包括不同类型的对象。

## <a name="syntax"></a>语法

```cpp
#include <tuple>
```

### <a name="classes"></a>类

|类|描述|
|-|-|
|[tuple](../standard-library/tuple-class.md)|包装元素的固定长度序列。|
|[tuple_element 类](../standard-library/tuple-element-class-tuple.md)|包装的 `tuple` 类型的元素。|
|[tuple_size 类](../standard-library/tuple-size-class-tuple.md)|包装 `tuple` 元素计数。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|比较 `tuple` 对象是否相等|
|[operator!=](../standard-library/tuple-operators.md#op_neq)|比较 `tuple` 对象是否不相等|
|[operator<](../standard-library/tuple-operators.md#op_lt)|比较 `tuple` 对象是否更小|
|[operator<=](../standard-library/tuple-operators.md#op_lt_eq)|比较 `tuple` 对象是否更小或相等|
|[operator>](../standard-library/tuple-operators.md#op_gt)|比较 `tuple` 对象是否更大|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|比较 `tuple` 对象是否更大或相等|

### <a name="functions"></a>函数

|函数|描述|
|-|-|
|[get](../standard-library/tuple-functions.md#get)|从 `tuple` 对象获取一个元素。|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|从元素值中生成一个 `tuple`。|
|[tie](../standard-library/tuple-functions.md#tie)|从元素引用中生成一个 `tuple`。|

## <a name="see-also"></a>请参阅

[\<array>](../standard-library/array.md)<br/>
