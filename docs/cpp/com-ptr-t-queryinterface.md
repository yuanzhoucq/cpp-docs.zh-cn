---
title: "_com_ptr_t::QueryInterface |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
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
ms.openlocfilehash: 6b5c8fb9ca1d628b178c19b677b90f17cc992373
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface
**Microsoft 专用**  
  
 调用`QueryInterface`成员函数**IUnknown**封装的接口指针上。  
  
## <a name="syntax"></a>语法  
  
```  
  
      template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType*& p   
) throw ( );  
template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType** p  
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `iid`  
 **IID**的接口指针。  
  
 `p`  
 原始接口指针。  
  
## <a name="remarks"></a>备注  
 调用**iunknown:: Queryinterface**具有指定封装的接口指针上**IID**并返回生成的原始接口指针在`p`。 此例程返回 `HRESULT` 以指示成功或失败。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)
