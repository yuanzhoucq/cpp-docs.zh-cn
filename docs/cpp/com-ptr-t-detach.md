---
title: "_com_ptr_t::Detach |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::Detach
dev_langs: C++
helpviewer_keywords: Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c04007df7d40e12f3f416b2f2cd437bdaf1314f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Microsoft 专用**  
  
 提取并返回封装的接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## <a name="remarks"></a>备注  
 提取和返回封装的接口指针，然后再清除封装的指针存储到**NULL**。 这将从封装中移除接口指针。 它将由您来调用**版本**返回的接口指针上。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)