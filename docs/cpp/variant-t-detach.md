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
- VARIANT object, detatch
- Detach method
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 402d8bfeb6aea45460124bdeaaa8b3ee485df622
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

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
  
## <a name="see-also"></a>另请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)
