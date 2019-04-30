---
title: is_trivially_move_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: b25d16658def4e3cf620ab707d2dabacb2620f33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413382"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable 类

测试类型是否具有普通移动赋值运算符。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*是具有普通移动赋值运算符，否则为 false 的类。

移动赋值运算符的类*Ty*并不重要如果：

它被隐式提供

该类*Ty*不具有虚拟函数

该类*Ty*不具有虚拟基

类类型的所有非静态数据成员的类具有普通移动赋值运算符

类的类型数组的所有非静态数据成员的类具有普通移动赋值运算符

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
