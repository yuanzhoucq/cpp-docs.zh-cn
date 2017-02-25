---
title: "ComPtrRef::ComPtrRef 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtrRef，构造函数"
ms.assetid: ce2d2533-fef6-4b2d-b088-6f3db01df5a5
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ComPtrRef::ComPtrRef 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
ComPtrRef(  
   _In_opt_ T* ptr  
);  
```  
  
#### 参数  
 `ptr`  
 基础值另一 ComPtrRef 对象。  
  
## 备注  
 初始化 ComPtrRef 类的新实例。指定的指针到另一 ComPtrRef 对象。  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [ComPtrRef 类](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)