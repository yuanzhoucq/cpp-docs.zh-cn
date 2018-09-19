---
title: _com_ptr_t::Detach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7f2f44df96ca339e5d8e4b251b5f2d259cb606b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092136"
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