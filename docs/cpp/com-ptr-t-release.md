---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: f455e855e782a939e79898ee46e445f65d25d37a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170587"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**Microsoft 专用**

在封装的接口指针上调用 `IUnknown` 的**Release**成员函数。

## <a name="syntax"></a>语法

```
void Release( );
```

## <a name="remarks"></a>备注

调用封装的接口指针上 `IUnknown::Release`，如果此接口指针为 NULL，则引发 `E_POINTER` 错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
