---
title: _com_ptr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Attach
helpviewer_keywords:
- COM interfaces, attach pointer
- Attach method [C++]
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
ms.openlocfilehash: 057d784bb495aefaeec1b86697a7421f6464cbd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745070"
---
# <a name="_com_ptr_tattach"></a>_com_ptr_t::Attach

**微软特定**

封装此智能指针的类型的原始接口指针。

## <a name="syntax"></a>语法

```cpp
void Attach( Interface* pInterface ) throw( );
void Attach( Interface* pInterface, bool fAddRef ) throw( );
```

#### <a name="parameters"></a>参数

*p接口*<br/>
原始接口指针。

*fAddRef*<br/>
如果为 TRUE，则`AddRef`调用。 如果是 FALSE，则`_com_ptr_t`对象将获取原始接口指针的所有权，而不调用`AddRef`。

## <a name="remarks"></a>备注

- **不调用附加（p***接口***）。** `AddRef`     将接口的所有权传递给此 `_com_ptr_t` 对象。 `Release`调用 以递减以前封装的指针的引用计数。

- **附加***（pInterface，fAddRef）* **,***fAddRef***)** 如果*fAddRef*为`AddRef`TRUE，则调用该值是为了增加封装接口指针的引用计数。       如果*fAddRef*是`_com_ptr_t`FALSE，则此对象将获取原始接口指针`AddRef`的所有权，而不调用 。 `Release`调用 以递减以前封装的指针的引用计数。

**结束微软特定**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
