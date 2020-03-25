---
title: _com_ptr_t 提取器
ms.date: 11/04/2016
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
ms.openlocfilehash: 31ac39104c041d1d119f6cd06de5f9c4a620dac0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190022"
---
# <a name="_com_ptr_t-extractors"></a>_com_ptr_t 提取器

**Microsoft 专用**

提取封装的 COM 接口指针。

## <a name="syntax"></a>语法

```
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>备注

- **Operator interface** <strong>\*</strong>返回封装的接口指针，该指针可能为 NULL。

- **操作员界面 &** 返回对封装的接口指针的引用，如果指针为 NULL，则会发出错误。

- **运算符**<strong>\*</strong>允许智能指针对象在取消引用时充当实际封装的接口。

- **operator->** 允许智能指针对象在取消引用时充当实际封装的接口。

- **运算符 &** 释放所有封装的接口指针，并将其替换为 NULL，并返回封装的指针的地址。 这允许将智能指针按地址传递到具有*out*参数的函数，该函数通过该函数返回接口指针。

- **operator bool**允许将智能指针对象用于条件表达式。 如果指针不为 NULL，则此运算符返回 TRUE。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
