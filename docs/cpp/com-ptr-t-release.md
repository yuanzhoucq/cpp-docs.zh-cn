---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: cf4cea35386d1f781d6d2946c1730ba2e18dacea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399221"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release

**Microsoft 专用**

调用**发行**成员函数的`IUnknown`上封装的接口指针。

## <a name="syntax"></a>语法

```
void Release( );
```

## <a name="remarks"></a>备注

调用`IUnknown::Release`封装的接口指针上引发`E_POINTER`错误如果此接口指针为 NULL。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)