---
title: "EventTargetArray::EventTargetArray 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EventTargetArray, 构造函数"
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventTargetArray::EventTargetArray 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
#### 参数  
 `hr`  
 此构造函数操作之后，参数 `hr` 分配的数组指示是否成功还是失败。  下表列出了 `hr`的可能值。  
  
 S\_OK  
 操作成功。  
  
 E\_OUTOFMEMORY  
 将不会为该数组分配任何内存 。  
  
 S\_FALSE  
 `items` 参数小于或等于零。  
  
 `items`  
 要分配的数组元素的数目。  
  
## 备注  
 初始化 EventTargetArray 类的新实例。  
  
 EventTargetArray 在 EventSource 对象用于保留一组事件处理程序。  
  
## 要求  
 **标头：**event.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [EventTargetArray 类](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)