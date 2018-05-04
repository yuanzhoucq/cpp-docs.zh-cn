---
title: _bstr_t::operator = |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5537f4ad3abbac9686272e15d06bfa5df0bfca6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =
**Microsoft 专用**  
  
 将新值赋给现有 `_bstr_t` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      _bstr_t& operator=(  
   const _bstr_t& s1   
) throw ( );  
_bstr_t& operator=(  
   const char* s2   
);  
_bstr_t& operator=(  
   const wchar_t* s3   
);  
_bstr_t& operator=(  
   const _variant_t& var   
);  
```  
  
#### <a name="parameters"></a>参数  
 *S1*  
 将分配给现有 `_bstr_t` 对象的 `_bstr_t` 对象。  
  
 *S2*  
 将分配给现有 `_bstr_t` 对象的多字节字符串。  
  
 `s3`  
 将分配给现有 `_bstr_t` 对象的 Unicode 字符串。  
  
 `var`  
 将分配给现有 `_variant_t` 对象的 `_bstr_t` 对象。  
  
 **结束 Microsoft 专用**  
  
## <a name="example"></a>示例  
 请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)有关的使用示例`operator=`。  
  
## <a name="see-also"></a>请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)