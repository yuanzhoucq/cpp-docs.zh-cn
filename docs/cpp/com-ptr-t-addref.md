---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 51182b461aeac83c12bb18a573a49b2d4347a190
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189919"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**Microsoft 专用**

调用封装的接口指针上 `IUnknown` 的 `AddRef` 成员函数。

## <a name="syntax"></a>语法

```
void AddRef( );
```

## <a name="remarks"></a>备注

调用封装的接口指针上 `IUnknown::AddRef`，如果指针为 NULL，则引发 `E_POINTER` 错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
