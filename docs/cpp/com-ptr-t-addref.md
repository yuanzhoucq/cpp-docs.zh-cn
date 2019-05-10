---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 7408b5c174f76673b56caffd56aaa87895bd08d4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154937"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef

**Microsoft 专用**

调用`AddRef`成员函数的`IUnknown`上封装的接口指针。

## <a name="syntax"></a>语法

```
void AddRef( );
```

## <a name="remarks"></a>备注

调用`IUnknown::AddRef`封装的接口指针上引发`E_POINTER`错误如果指针为 NULL。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)