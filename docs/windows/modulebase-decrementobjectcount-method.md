---
title: "ModuleBase::DecrementObjectCount 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DecrementObjectCount 方法"
ms.assetid: a016fb07-a36e-40cd-bc7b-8f6e85e256e7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ModuleBase::DecrementObjectCount 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
virtual long DecrementObjectCount() = 0;  
```  
  
## 返回值  
 在递增操作之前的计数。  
  
## 备注  
 当实现的，对象的数目由模块跟踪的增量。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [ModuleBase 类](../windows/modulebase-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)