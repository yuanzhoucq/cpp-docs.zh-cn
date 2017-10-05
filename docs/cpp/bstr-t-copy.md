---
title: "_bstr_t::copy |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method
- BSTR object, copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
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
ms.openlocfilehash: 25167305ae817ebd9d979c0145934996bbbfcddc
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtcopy"></a>_bstr_t::copy
**Microsoft 专用**  
  
 构造封装的 `BSTR` 的副本。  
  
## <a name="syntax"></a>语法  
  
```  
  
      BSTR copy(  
  bool fCopy = true  
) const;  
```  
  
#### <a name="parameters"></a>参数  
 `fCopy`  
 如果**true**，**复制**返回所包含的副本`BSTR`，否则为**复制**返回实际的 BSTR。  
  
## <a name="remarks"></a>备注  
 返回封装的 `BSTR` 对象的新分配的副本。  
  
## <a name="example"></a>示例  
  
```  
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)
