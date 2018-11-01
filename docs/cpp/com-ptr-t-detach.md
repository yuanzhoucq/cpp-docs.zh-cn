---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: affaefd8af4802836733587af62977171ba01410
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537795"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach

**Microsoft 专用**

提取并返回封装的接口指针。

## <a name="syntax"></a>语法

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>备注

提取和返回封装的接口指针，然后再清除为 NULL 的封装的指针存储。 这将从封装中移除接口指针。 它将由您来调用`Release`上返回的接口指针。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)