---
title: "DeferrableEventArgs::GetDeferral 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DeferrableEventArgs::GetDeferral 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取对[延迟](http://go.microsoft.com/fwlink/?LinkId=526520)对象的引用，该对象表示延迟的事件。  
  
## 语法  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### 参数  
 `result`  
 完成调用后将引用 [Deferral](http://go.microsoft.com/fwlink/?LinkId=526520) 对象的指针。  
  
## 返回值  
 如果成功，则为 S\_OK；否则为指示错误的 HRESULT。  
  
## 备注  
 有关代码示例，请参阅 [DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)。  
  
## 要求  
 **标头：**event.h  
  
 **命名空间：**Microsoft::WRL  
  
## 请参阅  
 [DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)