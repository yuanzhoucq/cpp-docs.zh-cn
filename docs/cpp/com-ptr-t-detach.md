---
title: _com_ptr_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::Detach
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
ms.openlocfilehash: 8ba42f19e3474cc4a3199771f761b021221f430e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190009"
---
# <a name="_com_ptr_tdetach"></a>_com_ptr_t::Detach

**Microsoft 专用**

提取并返回封装的接口指针。

## <a name="syntax"></a>语法

```
Interface* Detach( ) throw( );
```

## <a name="remarks"></a>备注

提取并返回封装的接口指针，然后将封装的指针存储清除为 NULL。 这将从封装中移除接口指针。 你需要在返回的接口指针上调用 `Release`。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
