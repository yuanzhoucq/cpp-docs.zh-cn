---
title: is_trivially_copyable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copyable
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
ms.openlocfilehash: d3062ae311b63be76ba07185f4f8173afa4229cc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459753"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable 类

测试类型是否为普通复制类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*T*是完全复制类型, 则类型谓词的实例为 true; 否则为 false。 普通复制类型不具有任何重要的复制操作、移动操作或析构函数。 一般而言，如果复制操作可作为按位复制实现，则可将其视为普通复制。 内置类型和普通复制类型数组都可进行普通复制。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
