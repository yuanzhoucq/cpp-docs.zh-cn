---
title: is_trivially_default_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: 19a5e8afedf3e59d5dafa937af4f7d35343eb7d9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459644"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible 类

测试类型是否具有普通默认构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>参数

*Ty*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*Ty*是具有普通构造函数的类, 则类型谓词的实例为 true; 否则为 false。

类*Ty*的默认构造函数在以下情况下是普通构造函数:

- 它是一个隐式声明的默认构造函数

- 类*Ty*没有虚函数

- 类*Ty*没有虚拟基

- 类*Ty*的所有直接基都具有普通构造函数

- 类类型的所有非静态数据成员的类具有普通构造函数

- 类的类型数组的所有非静态数据成员的类具有普通构造函数

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
