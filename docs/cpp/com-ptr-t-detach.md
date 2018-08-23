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
ms.openlocfilehash: cf38e433f7042707b502a4cba2088db9412adb29
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405829"
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