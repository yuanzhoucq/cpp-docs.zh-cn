---
title: "HANDLENullTraits::Close 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HANDLENullTraits::Close 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

关闭指定的句柄。  
  
## 语法  
  
```  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
#### 参数  
 `h`  
 关闭的句柄。  
  
## 返回值  
 **true**，如果处理 `h` 成功关闭；否则，返回 **false**。  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [HANDLENullTraits 结构](../windows/handlenulltraits-structure.md)