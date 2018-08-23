---
title: is_move_assignable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3af5cbeae84b5b582077f543a39cfe408575bc71
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960051"
---
# <a name="ismoveassignable-class"></a>is_move_assignable 类

测试类型是否可移动赋值。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>参数

*T*查询的类型。

## <a name="remarks"></a>备注

如果类型的右值引用可赋予此类型的引用，则该类型可移动赋值。 类型谓词等效于 `is_assignable<T&, T&&>`。 可移动赋值的类型包括可引用的标量类型和类类型，这些类型具有编译器生成的移动赋值运算符或用户定义的移动赋值运算符。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
