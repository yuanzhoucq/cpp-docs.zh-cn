---
title: "_variant_t::Attach |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs: C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: effeaaaf3f8df9eb100d5e92e760eb439a865552
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="varianttattach"></a>_variant_t::Attach
**Microsoft 专用**  
  
 将附加**VARIANT**对象插入`_variant_t`对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      void Attach(  
   VARIANT& varSrc   
);  
```  
  
#### <a name="parameters"></a>参数  
 *varSrc*  
 A **VARIANT**要附加到此对象`_variant_t`对象。  
  
## <a name="remarks"></a>备注  
 将获得的所有权**VARIANT**通过封装。 此成员函数释放所有现有封装**VARIANT**，然后复制提供**VARIANT**，并设置其**VARTYPE**到`VT_EMPTY`若要确保其资源仅通过释放`_variant_t`析构函数。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)