---
title: "HANDLETraits::GetInvalidValue 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInvalidValue 方法"
ms.assetid: e95d2cc1-e70f-463f-8ff0-183cdeac1138
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HANDLETraits::GetInvalidValue 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示无效的句柄。  
  
## 语法  
  
```  
inline static HANDLE GetInvalidValue();  
```  
  
## 返回值  
 始终返回 INVALID\_HANDLE\_VALUE。\(INVALID\_HANDLE\_VALUE 由 Windows 定义的。\)  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [HANDLETraits 结构](../windows/handletraits-structure.md)