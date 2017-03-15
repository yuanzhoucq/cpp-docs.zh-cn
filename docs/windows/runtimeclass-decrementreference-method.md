---
title: "RuntimeClass::DecrementReference 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass::DecrementReference"
dev_langs: 
  - "C++"
ms.assetid: f5ecfeaa-2865-455b-9208-94a0685fd2c6
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# RuntimeClass::DecrementReference 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

递减RuntimeClass当前对象的引用计数。  
  
## 语法  
  
```  
ULONG DecrementReference();  
```  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)