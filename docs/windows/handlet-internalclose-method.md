---
title: "HandleT::InternalClose 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InternalClose 方法"
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HandleT::InternalClose 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

关闭当前的 HandleT对象。  
  
## 语法  
  
```  
virtual bool InternalClose();  
```  
  
## 返回值  
 `true`，如果当前 HandleT 成功关闭；否则，返回 `false`。  
  
## 备注  
 InternalClose\(\) 保护。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HandleT 类](../windows/handlet-class.md)