---
title: _variant_t::ChangeType |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f3790f4cb357ed830ba2c61b3c2906356dc64da
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465583"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Microsoft 专用**  
  
 更改的类型`_variant_t`所指示的对象`VARTYPE`。  
  
## <a name="syntax"></a>语法  
  
```  
void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>参数  
 *vartype*  
 `VARTYPE`此`_variant_t`对象。  
  
 *pSrc*  
 指向要转换的 `_variant_t` 对象的指针。 如果此值为 NULL，是就地完成转换。  
  
## <a name="remarks"></a>备注  
 此成员函数将转换`_variant_t`到所指示的对象`VARTYPE`。 如果*pSrc*为 NULL，则转换将就地，否则为这`_variant_t`从复制对象*pSrc* ，然后再转换。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)