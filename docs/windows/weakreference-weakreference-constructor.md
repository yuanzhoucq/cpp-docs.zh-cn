---
title: "WeakReference::WeakReference 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference::WeakReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakReference, 构造函数"
ms.assetid: 4959a9d7-78ea-423d-a46b-50d010d29fff
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# WeakReference::WeakReference 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
WeakReference();  
```  
  
## <a name="remarks"></a>备注  
 新实例初始化 [WeakReference 类](../windows/weakreference-class1.md)。  
  
 WeakReference 对象的强引用指针初始化为 `nullptr`, ，并且强引用计数初始化为 1。  
  
## <a name="requirements"></a>要求  
 **标头︰** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
    
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)