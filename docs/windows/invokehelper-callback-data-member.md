---
title: "InvokeHelper::callback_ 数据成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::InvokeHelper::callback_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "callback_ 数据成员"
ms.assetid: 6f0cbf6d-0448-46f8-ba71-bd6fd8702e3a
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InvokeHelper::callback_ 数据成员
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
TCallback callback_;  
```  
  
## 备注  
 当事件发生时调用的事件处理程序。  
  
 `TCallback` 模板参数指定事件处理程序的类型。  
  
## 要求  
 **标头：**event.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [InvokeHelper 结构](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)