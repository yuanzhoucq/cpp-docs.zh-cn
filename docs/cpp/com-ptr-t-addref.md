---
title: _com_ptr_t::AddRef |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40ed48b54a3862f7ac5804e7652d98b661bb071d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940987"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Microsoft 专用**  
  
 调用`AddRef`成员函数的`IUnknown`上封装的接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
  
void AddRef( );  
  
```  
  
## <a name="remarks"></a>备注  
 调用`IUnknown::AddRef`封装的接口指针上引发 E_POINTER 错误如果指针为 NULL。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)