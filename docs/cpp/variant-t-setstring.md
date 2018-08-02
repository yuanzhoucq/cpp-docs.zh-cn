---
title: _variant_t::SetString |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 090fd7ed027738ebe7bc9276e3b3f124b9212c4a
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463462"
---
# <a name="varianttsetstring"></a>_variant_t::SetString
**Microsoft 专用**  
  
 将字符串分配给此 `_variant_t` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
void SetString(const char* pSrc);  
```  
  
#### <a name="parameters"></a>参数  
 *pSrc*  
 指向字符串的指针。  
  
## <a name="remarks"></a>备注  
 将 ANSI 字符串转换为 Unicode `BSTR` 字符串并将其分配给此 `_variant_t` 对象。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)