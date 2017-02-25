---
title: "HandleT::Detach 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach 方法"
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HandleT::Detach 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

离散从其当前 HandleT 基础句柄的对象。  
  
## 语法  
  
```  
typename HandleTraits::Type Detach();  
```  
  
## 返回值  
 基础句柄。  
  
## 备注  
 当完成此操作时，当前 HandleT 设置为无效状态。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HandleT 类](../windows/handlet-class.md)