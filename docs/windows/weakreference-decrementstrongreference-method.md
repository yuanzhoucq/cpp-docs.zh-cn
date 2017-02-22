---
title: "WeakReference::DecrementStrongReference 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DecrementStrongReference 方法"
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# WeakReference::DecrementStrongReference 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>备注  
 递减当前 WeakReference 对象的强引用计数。  
  
 当强引用计数变为零时，强引用设置为 `nullptr`。  
  
## <a name="return-value"></a>返回值  
 减少的强引用计数。  
  
## <a name="requirements"></a>要求  
 **标头︰** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
[WeakReference 类](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)