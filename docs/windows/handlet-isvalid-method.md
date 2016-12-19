---
title: "HandleT::IsValid 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsValid 方法"
ms.assetid: 2c3e72fd-e67b-4908-9929-9007e1a4fc25
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT::IsValid 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示当前 HandleT 对象是否表示句柄。  
  
## 语法  
  
```  
bool IsValid() const;  
```  
  
## 返回值  
 `true`，如果 HandleT 表示句柄；否则，返回 `false`。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HandleT 类](../windows/handlet-class.md)