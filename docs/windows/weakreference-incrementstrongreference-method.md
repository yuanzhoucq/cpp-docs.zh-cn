---
title: "WeakReference::IncrementStrongReference 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IncrementStrongReference 方法"
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# WeakReference::IncrementStrongReference 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
ULONG IncrementStrongReference();  
```  
  
## <a name="return-value"></a>返回值  
 递增的强引用计数。  
  
## <a name="remarks"></a>备注  
 递增当前 WeakReference 对象的强引用计数。  
  
## <a name="requirements"></a>要求  
 **标头︰** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
[WeakReference 类](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)