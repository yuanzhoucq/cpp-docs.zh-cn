---
title: is_null_pointer 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_null_pointer
helpviewer_keywords:
- is_null_pointer
ms.assetid: f3b3601b-f162-4803-a6e9-dabf5c3876cc
ms.openlocfilehash: b306753146a51bde842b55e4f36d3c1afa82591d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455837"
---
# <a name="isnullpointer-class"></a>is_null_pointer 类

测试类型是否为 std::nullptr_t。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_null_pointer;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*T*为`std::nullptr_t`, 则类型谓词的实例为 true; 否则为 false。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
