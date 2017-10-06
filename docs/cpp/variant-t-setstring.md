---
title: "_variant_t::SetString |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
caps.latest.revision: 6
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
ms.openlocfilehash: 0e3502a83b93e89744e280cf9c01aa2d08b09a7e
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="varianttsetstring"></a>_variant_t::SetString
**Microsoft 专用**  
  
 将字符串分配给此 `_variant_t` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void SetString(  
   const char* pSrc   
);  
```  
  
#### <a name="parameters"></a>参数  
 `pSrc`  
 指向字符串的指针。  
  
## <a name="remarks"></a>备注  
 将 ANSI 字符串转换为 Unicode `BSTR` 字符串并将其分配给此 `_variant_t` 对象。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)
