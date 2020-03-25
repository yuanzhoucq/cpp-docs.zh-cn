---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 870e3580ed23ce994d832f7c59b951680d725e41
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180493"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft 专用**

封装此智能指针的类型的原始接口指针。

## <a name="syntax"></a>语法

```
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>parameters

*pInterface*<br/>
原始接口指针。

*fAddRef*<br/>
如果为 TRUE，则调用 `AddRef`。 如果该参数为 FALSE，则 `_com_ptr_t` 对象获取原始接口指针的所有权，而不调用 `AddRef`。

## <a name="remarks"></a>备注

- 不调用**Attach （** *pInterface* **）** `AddRef`。 将接口的所有权传递给此 `_com_ptr_t` 对象。 调用 `Release` 来减小以前封装的指针的引用计数。

- **Attach （**  *pInterface* **，**  *fAddRef*  **）** 如果*fAddRef*为 TRUE，则调用 `AddRef` 来递增封装的接口指针的引用计数。 如果*fAddRef*为 FALSE，则此 `_com_ptr_t` 对象获取原始接口指针的所有权，而不调用 `AddRef`。 调用 `Release` 来减小以前封装的指针的引用计数。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
