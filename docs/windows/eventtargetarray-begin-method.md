---
title: "EventTargetArray::Begin 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::EventTargetArray::Begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Begin 方法"
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventTargetArray::Begin 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
ComPtr<IUnknown>* Begin();  
```  
  
## 返回值  
 第一个元素的地址在内部数组的事件处理程序。  
  
## 备注  
 第一个元素的地址在内部数组的事件处理程序。  
  
## 要求  
 **标头：**event.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [EventTargetArray 类](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)