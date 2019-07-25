---
title: is_nothrow_copy_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_constructible
helpviewer_keywords:
- is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
ms.openlocfilehash: 229083f4569647bd65d1ce7e640f753a9418371d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455952"
---
# <a name="isnothrowcopyconstructible-class"></a>is_nothrow_copy_constructible 类

测试类型是否具有 **nothrow** 复制构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_nothrow_copy_constructible;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*具有 nothrow 复制构造函数, 则类型谓词的实例为 true; 否则为 false。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
