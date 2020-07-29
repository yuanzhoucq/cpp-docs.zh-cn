---
title: is_nothrow_move_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_move_constructible
helpviewer_keywords:
- is_nothrow_move_constructible
ms.assetid: d186d97b-7b89-470a-8d30-993046a83379
ms.openlocfilehash: 115a1b6c2157a139786c0b8762a9a614bbcd6deb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217722"
---
# <a name="is_nothrow_move_constructible-class"></a>is_nothrow_move_constructible 类

测试类型是否具有 **`nothrow`** 移动构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_nothrow_move_constructible;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*具有 nothrow 移动构造函数，则类型谓词的实例为 true; 否则为 false。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间:** std

## <a name="see-also"></a>另请参阅

[<type_traits>](../standard-library/type-traits.md)
