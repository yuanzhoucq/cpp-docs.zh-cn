---
title: "_bstr_t::GetBSTR |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
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
ms.openlocfilehash: 376951862a82d6588221b592238c9346d31bad4d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Microsoft 专用**  
  
 指向 `BSTR` 包装的 `_bstr_t` 的开头。  
  
## <a name="syntax"></a>语法  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## <a name="return-value"></a>返回值  
 `BSTR` 包装的 `_bstr_t` 的开头。  
  
## <a name="remarks"></a>备注  
 `GetBSTR` 影响所有共享 `_bstr_t` 的 `BSTR` 对象。 多个 `_bstr_t` 可以通过使用复制构造函数和 `BSTR` 共享 `operator=`。  
  
## <a name="example"></a>示例  
 请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)的使用示例`GetBSTR`。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)
