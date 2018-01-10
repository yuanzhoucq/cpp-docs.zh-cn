---
title: "_com_ptr_t::Release |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs: C++
helpviewer_keywords: Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b0e111103ecf42b44bd03b7b5ed154586676812
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release
**Microsoft 专用**  
  
 调用**版本**成员函数**IUnknown**封装的接口指针上。  
  
## <a name="syntax"></a>语法  
  
```  
  
void Release( );  
  
```  
  
## <a name="remarks"></a>备注  
 调用`IUnknown::Release`封装的接口指针上引发`E_POINTER`错误如果此接口指针是**NULL**。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)