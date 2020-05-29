---
title: _com_ptr_t::Release
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
ms.openlocfilehash: 73de3c2d19063f0738b8b0a3c510ea520f58de0b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745057"
---
# <a name="_com_ptr_trelease"></a>_com_ptr_t::Release

**微软特定**

调用封装**Release**接口指针`IUnknown`上的释放成员函数。

## <a name="syntax"></a>语法

```cpp
void Release( );
```

## <a name="remarks"></a>备注

调用`IUnknown::Release`封装的接口指针，如果此接口指针`E_POINTER`为 NULL，则引发错误。

**结束微软特定**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
