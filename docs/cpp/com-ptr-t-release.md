---
title: _com_ptr_t::Release |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a8a734eae486ca5e88009301b13d71b21473d9f
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939251"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release
**Microsoft 专用**  
  
 调用`Release`成员函数的`IUnknown`上封装的接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
void Release( );  
  
```  
  
## <a name="remarks"></a>备注  
 调用`IUnknown::Release`上封装的接口指针，此接口指针为 NULL 时引发了 E_POINTER 错误。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)