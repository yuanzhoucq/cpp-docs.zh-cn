---
title: "Weakreference:: Weakreference 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference::WeakReference
dev_langs: C++
helpviewer_keywords: WeakReference, constructor
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8608c787b0b5b07c4e619443e751d21d14b0a811
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="weakreferenceweakreference-constructor"></a>WeakReference::WeakReference 构造函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
WeakReference();  
```  
  
## <a name="remarks"></a>备注  
 初始化的新实例[WeakReference 类](../windows/weakreference-class1.md)。  
  
 WeakReference 对象的强引用指针初始化为`nullptr`，并且强引用计数未被初始化为 1。  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
    
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)