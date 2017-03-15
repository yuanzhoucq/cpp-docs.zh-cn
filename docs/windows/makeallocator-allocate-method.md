---
title: "MakeAllocator::Allocate 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::MakeAllocator::Allocate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Allocate 方法"
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MakeAllocator::Allocate 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
__forceinline void* Allocate();  
```  
  
## 返回值  
 如果成功，将指针指向已分配的内存；否则，返回 `nullptr`。  
  
## 备注  
 分配内存并将它与当前 MakeAllocator 对象。  
  
 分配内存的大小是当前 MakeAllocator 模板参数指定类型的大小。  
  
 开发人员需要只重写 Allocate\(\) 方法实现不同的内存分配模式。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [MakeAllocator 类](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)