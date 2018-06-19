---
title: '&lt;hash_map&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <hash_map>
- std::<hash_map>
dev_langs:
- C++
helpviewer_keywords:
- hash_map header
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0e3948e8697825af6cdd785117647943b33bac0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850048"
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> 此标头已废弃不用。 替代项是[ \<unordered_map >](unordered-map.md)。

定义容器模板类 hash_map 和 hash_multimap 及其支持的模板。

## <a name="syntax"></a>语法

> #<a name="include-hashmap"></a>包括 < hash_map >

### <a name="operators"></a>运算符

|Hash_map 版本|Hash_multimap 版本|描述|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|测试运算符左侧和右侧的 hash_map 或 hash_multimap 对象是否不相等。|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|测试运算符左侧和右侧的 hash_map 或 hash_multimap 对象是否相等。|

### <a name="specialized-template-functions"></a>专用化模板函数

|Hash_map 版本|Hash_multimap 版本|描述|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|交换两个 hash_map 或 hash_multimap 的元素。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[hash_compare 类](hash-compare-class.md)|描述了一个对象，任何哈希关联容器（hash_map、hash_multimap、hash_set 或 hash_multiset）都可将该对象用作默认的 **Traits** 参数对象，以对其所包含的元素进行排序和哈希处理。|
|[value_compare 类](value-compare-class.md)|提供一个函数对象，该对象能通过比较 hash_map 元素的键值来比较这些元素，以确定其在 hash_map 中的相对顺序。|
|[hash_map 类](hash-map-class.md)|用于存储和快速检索集合中的数据，集合中的每个元素都是具有排序键和关联数据值的元素对，而排序键的值是唯一的。|
|[hash_multimap 类](hash-multimap-class.md)|用于存储和快速检索集合中的数据，集合中的每个元素都是具有排序键和关联数据值的元素对，而排序键的值不需要具有唯一性。|

## <a name="requirements"></a>要求

**标头：**\<hash_map>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[标头文件引用](cpp-standard-library-header-files.md)
[c + + 标准库中的线程安全](thread-safety-in-the-cpp-standard-library.md)
[c + + 标准库参考](cpp-standard-library-reference.md)
