---
title: "GetModuleBase 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::GetModuleBase"
dev_langs: 
  - "C++"
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetModuleBase 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索[ModuleBase](../windows/modulebase-class.md)指针，该指针用于递增和递减 [RuntimeClass](../windows/runtimeclass-class.md) 对象的引用数。  
  
## 语法  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## 返回值  
 指向 `ModuleBase` 对象的指针。  
  
## 备注  
 此函数在内部用于递增和递减对象的引用计数。  
  
 可以通过调用 [ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md) 和 [ModuleBase::DecrementObjectCount](../windows/modulebase-decrementobjectcount-method.md)使用此函数控制引用计数。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)