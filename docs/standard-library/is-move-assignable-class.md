---
title: is_move_assignable 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_assignable
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
ms.openlocfilehash: da4734507bac14ecf0278117deb7668518305be0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351061"
---
# <a name="ismoveassignable-class"></a>is_move_assignable 类

测试类型是否可移动赋值。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>参数

*T*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型的右值引用可赋予此类型的引用，则该类型可移动赋值。 类型谓词等效于 `is_assignable<T&, T&&>`。 可移动赋值的类型包括可引用的标量类型和类类型，这些类型具有编译器生成的移动赋值运算符或用户定义的移动赋值运算符。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
