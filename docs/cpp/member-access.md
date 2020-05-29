---
title: 成员访问
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
ms.openlocfilehash: 12ea612625e21a8a13021b75e92f3752b0b5ce80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179414"
---
# <a name="member-access"></a>成员访问

可以通过重载成员访问运算符（ **->** ）来控制类成员访问。 此运算符被视为此用法中的一元运算符，而重载运算符函数必须是类成员函数。 因此，此类函数的声明是：

## <a name="syntax"></a>语法

```
class-type *operator->()
```

## <a name="remarks"></a>备注

其中*类类型*是此运算符所属的类的名称。 成员访问运算符函数必须是非静态成员函数。

此运算符（通常与指针取消引用运算符一起使用）用于实现在取消引用用法或对用法计数前验证指针的“智能指针”。

**.** 无法重载成员访问运算符。

## <a name="see-also"></a>另请参阅

[运算符重载](../cpp/operator-overloading.md)
