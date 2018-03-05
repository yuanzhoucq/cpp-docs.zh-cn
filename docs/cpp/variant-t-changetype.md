---
title: "_variant_t::ChangeType |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
dev_langs:
- C++
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fb59090ebc4c6ff9120e813ae12a9defbe618b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Microsoft 专用**  
  
 类型更改`_variant_t`到指示的对象**VARTYPE**。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>参数  
 `vartype`  
 **VARTYPE**此`_variant_t`对象。  
  
 `pSrc`  
 指向要转换的 `_variant_t` 对象的指针。 如果此值为**NULL**，转换将就地。  
  
## <a name="remarks"></a>备注  
 此成员函数将转换`_variant_t`对象插入指示**VARTYPE**。 如果`pSrc`是**NULL**，转换将就地，否则为这`_variant_t`从复制对象`pSrc`，然后进行转换。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)