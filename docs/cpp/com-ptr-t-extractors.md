---
title: _com_ptr_t 提取器
description: 描述 _com_ptr_t 类的提取运算符。
ms.date: 07/07/2020
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: fb5441d87dc35ec6fbb495bc38d9041c1f2d2f33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220569"
---
# <a name="_com_ptr_t-extractors"></a>`_com_ptr_t`提取器

**Microsoft 专用**

提取封装的 COM 接口指针。

## <a name="syntax"></a>语法

```c++
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>备注

- **`operator Interface*`** 返回封装的接口指针，它可以为 NULL。

- **`operator Interface&`** 返回对封装的接口指针的引用，如果指针为 NULL，则会发出错误。

- **`operator*`** 允许智能指针对象在取消引用时充当实际封装的接口。

- **`operator->`** 允许智能指针对象在取消引用时充当实际封装的接口。

- **`operator&`** 释放所有封装的接口指针，并将其替换为 NULL，并返回封装的指针的地址。 此运算符允许将智能指针按地址传递到具有*out*参数的函数，该函数通过该函数返回接口指针。

- **`operator bool`** 允许将智能指针对象用于条件表达式。 **`true`** 如果指针不为 NULL，则此运算符返回。

  > [!NOTE]
  > 由于未 **`operator bool`** 声明为，因此可 **`explicit`** `_com_ptr_t` 隐式转换为 **`bool`** ，这可转换为任意标量类型。 这可能会在你的代码中产生意外结果。 启用[编译器警告（等级4） C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md)以防止无意中使用此转换。

## <a name="see-also"></a>另请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
