---
title: "_com_ptr_t::AddRef |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
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
ms.openlocfilehash: d873d91192dc13f7b1277cbe8ef26b24421b6904
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Microsoft 专用**  
  
 调用`AddRef`成员函数**IUnknown**封装的接口指针上。  
  
## <a name="syntax"></a>语法  
  
```  
  
void AddRef( );  
  
```  
  
## <a name="remarks"></a>备注  
 调用`IUnknown::AddRef`封装的接口指针上引发`E_POINTER`错误如果指针**NULL**。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)
