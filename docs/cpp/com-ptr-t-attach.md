---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: cb5950e311711dd489b3cab223714b1840773f60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220582"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**Microsoft 专用**

封装此智能指针的类型的原始接口指针。

## <a name="syntax"></a>语法

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>参数

*pInterface*<br/>
原始接口指针。

*fAddRef*<br/>
如果为 **`true`** ，则 `AddRef` 调用。 如果是 **`false`** ，则 `_com_ptr_t` 对象获取原始接口指针的所有权，而不调用 `AddRef` 。

## <a name="remarks"></a>备注

- **附加（**  *pInterface*  **）** `AddRef`不会调用。 将接口的所有权传递给此 `_com_ptr_t` 对象。 `Release`调用以减小先前封装的指针的引用计数。

- **Attach （**  *pInterface* **，**  *fAddRef*  **）** 如果*fAddRef*为 **`true`** ， `AddRef` 则调用来增加封装的接口指针的引用计数。 如果*fAddRef*为 **`false`** ，则此 `_com_ptr_t` 对象将获取原始接口指针的所有权，而不调用 `AddRef` 。 `Release`调用以减小先前封装的指针的引用计数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
