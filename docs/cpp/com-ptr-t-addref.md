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
ms.openlocfilehash: 4bf56e87b8b7949048b1e6006d3aa32f00af1462
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404254"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Microsoft 专用**  
  
 调用`AddRef`成员函数的`IUnknown`上封装的接口指针。  
  
## <a name="syntax"></a>语法  
  
```  
void AddRef( );  
```  
  
## <a name="remarks"></a>备注  
 调用`IUnknown::AddRef`封装的接口指针上引发`E_POINTER`错误如果指针为 NULL。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_com_ptr_t 类](../cpp/com-ptr-t-class.md)