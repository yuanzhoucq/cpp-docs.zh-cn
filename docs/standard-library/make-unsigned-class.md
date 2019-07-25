---
title: make_unsigned 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 4c0224bd5fd7dc8c6589ae474bb9acb9a8f09cf6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456314"
---
# <a name="makeunsigned-class"></a>make_unsigned 类

设置类型或大小大于或等于类型的无符号的最小类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*T*|要修改的类型。|

## <a name="remarks"></a>备注

如果`is_unsigned<T>`保留为 true, 则类型修饰符的实例保留修改后的类型。 否则，它就是适用于 `sizeof (T) <= sizeof (ST)` 的最小的带符号类型 `ST`。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
