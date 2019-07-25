---
title: is_trivially_copy_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: c0019257a032d3becc268513336ed59e58a2e1d5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448000"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable 类

测试类型是否具有普通复制赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>参数

*关心*\
要查询的类型。

## <a name="remarks"></a>备注

如果类型*T*是具有普通复制赋值运算符的类, 则类型谓词的实例为 true; 否则为 false。

如果类*t*的赋值构造函数是隐式提供的, 则该类没有虚函数, 类 t 没有虚函数, 类*t*没有虚拟基, 类类型的所有非静态数据成员的类具有普通赋值运算符以及类的类型数组的所有非静态数据成员的类具有普通赋值运算符。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
