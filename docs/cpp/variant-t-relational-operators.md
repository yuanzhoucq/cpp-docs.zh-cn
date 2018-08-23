---
title: _variant_t 关系运算符 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
dev_langs:
- C++
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32f9a45fcfaaff02cfb7cf765857957f20c41ba1
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463036"
---
# <a name="variantt-relational-operators"></a>_variant_t 关系运算符
**Microsoft 专用**  
  
 比较两个 `_variant_t` 对象是否相等。  
  
## <a name="syntax"></a>语法  
  
```  
bool operator==(  
   const VARIANT& varSrc) const;  
bool operator==(  
   const VARIANT* pSrc) const;  
bool operator!=(  
   const VARIANT& varSrc) const;  
bool operator!=(  
   const VARIANT* pSrc) const;  
```  
  
#### <a name="parameters"></a>参数  
 *varSrc*  
 一个`VARIANT`进行比较与`_variant_t`对象。  
  
 *pSrc*  
 指向`VARIANT`进行比较与`_variant_t`对象。  
  
## <a name="return-value"></a>返回值  
 返回 **，则返回 true**如果比较保留， **false**如果不是。  
  
## <a name="remarks"></a>备注  
 比较`_variant_t`对象与`VARIANT`，测试是否相等。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)