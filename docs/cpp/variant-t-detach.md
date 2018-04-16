---
title: "_variant_t::Detach |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs:
- C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 577b4874dd6d89c0c6c60b1a7981e74944e77ba8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="varianttdetach"></a>_variant_t::Detach
**Microsoft 专用**  
  
 分离封装**VARIANT**从此对象`_variant_t`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
VARIANT Detach( );  
  
```  
  
## <a name="return-value"></a>返回值  
 封装**VARIANT**。  
  
## <a name="remarks"></a>备注  
 提取和返回封装**VARIANT**，然后清除此`_variant_t`对象而不销毁它。 此成员函数删除**VARIANT**从封装和集**VARTYPE**此`_variant_t`对象传递给`VT_EMPTY`。 它将由您来释放返回**VARIANT**通过调用[VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835)函数。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)