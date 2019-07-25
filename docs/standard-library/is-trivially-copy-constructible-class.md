---
title: is_trivially_copy_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: f8c4026da424e77b57555dd4c342c9ac7a386591
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447992"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible 类

测试类型是否包含普通复制构造函数。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*T*是具有普通复制构造函数的类, 则类型谓词的实例为 true; 否则为 false。

如果类*t*的复制构造函数被隐式声明、类 t 没有虚拟函数或虚拟基, 则类 t 的所有直接基*都具有普通*复制构造函数, 即所有非静态数据成员的类类类型具有普通复制构造函数, 且类的类型数组的所有非静态数据成员的类具有普通复制构造函数。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
