---
title: '&lt;allocators&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377878"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 运算符

这些是中定义的全局模板运算符函数&lt;分配器&gt;。 类成员运算符函数，请参阅类文档。

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>operator!=

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
|*left*|要测试是否不相等的其中一个分配器对象。|
|*right*|要测试是否不相等的其中一个分配器对象。|

### <a name="return-value"></a>返回值

如果分配器对象不相等，则为 **true**；如果分配器对象相等，则为 **false**。

### <a name="remarks"></a>备注

模板运算符返回 `!(left == right)`。

## <a name="op_eq_eq"></a>  operator==

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
|*left*|要测试是否相等的其中一个分配器对象。|
|*right*|要测试是否相等的其中一个分配器对象。|

### <a name="return-value"></a>返回值

如果分配器对象相等，则为 **true**；如果分配器对象不相等，则为 **false**。

### <a name="remarks"></a>备注

此模板运算符返回 `left.equals(right)`。

## <a name="see-also"></a>请参阅

[\<allocators>](../standard-library/allocators-header.md)
