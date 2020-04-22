---
title: _com_ptr_t::AddRef
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::AddRef
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
ms.openlocfilehash: 4dcf643357c9b368d4b2ea3bc51e6567acf45a44
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745103"
---
# <a name="_com_ptr_taddref"></a>_com_ptr_t::AddRef

**微软特定**

调用`AddRef`封装接口指针`IUnknown`上的成员函数。

## <a name="syntax"></a>语法

```cpp
void AddRef( );
```

## <a name="remarks"></a>备注

调用`IUnknown::AddRef`封装的接口指针，如果指针为`E_POINTER`NULL，则引发错误。

**结束微软特定**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
