---
title: "&lt;allocators&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs: C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 986d972bdc778ddd47c2c0098955f2b570c881ce
ms.sourcegitcommit: a7e4956c1150273e8dd39fda8b41655a6cf2cb98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/08/2017
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 运算符

这些是中定义的全局模板运算符函数&lt;分配器&gt;。 类成员运算符函数，请参阅类文档。

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

##  <a name="op_neq"></a>operator!=

测试指定类的分配器对象之间是否不相等。

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`left`|要测试是否不相等的其中一个分配器对象。|
|`right`|要测试是否不相等的其中一个分配器对象。|

### <a name="return-value"></a>返回值

如果分配器对象不相等，则为 **true**；如果分配器对象相等，则为 **false**。

### <a name="remarks"></a>备注

模板运算符返回 `!(left == right)`。

##  <a name="op_eq_eq"></a>  operator==

测试指定类的分配器对象之间是否相等。

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`left`|要测试是否相等的其中一个分配器对象。|
|`right`|要测试是否相等的其中一个分配器对象。|

### <a name="return-value"></a>返回值

如果分配器对象相等，则为 **true**；如果分配器对象不相等，则为 **false**。

### <a name="remarks"></a>备注

此模板运算符返回 `left.equals(right)`。

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)  
