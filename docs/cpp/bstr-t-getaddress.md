---
title: "_bstr_t::GetAddress |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
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
ms.openlocfilehash: d11479a93cf19b59ae6b824f76f9b00b10fff6b2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Microsoft 专用**  
  
 释放所有现有字符串并返回一个新分配的字符串的地址。  
  
## <a name="syntax"></a>语法  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>返回值  
 指向由 `BSTR` 包装的 `_bstr_t` 的指针。  
  
## <a name="remarks"></a>备注  
 `GetAddress` 影响所有共享 `_bstr_t` 的 `BSTR` 对象。 多个 `_bstr_t` 可以通过使用复制构造函数和 `BSTR` 共享 `operator=`。  
  
## <a name="example"></a>示例  
 请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)示例使用`GetAddress`。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)
