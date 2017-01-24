---
title: "Event::Event 构造函数（Windows 运行时 C++ 模板库） | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event::Event"
dev_langs: 
  - "C++"
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event::Event 构造函数（Windows 运行时 C++ 模板库）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Event 类的新实例。  
  
## 语法  
  
```  
explicit Event(  
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);  
WRL_NOTHROW Event(  
   _Inout_ Event&& h  
);  
```  
  
#### 参数  
 `h`  
 事件的句柄。  默认情况下，`h` 初始化为 `nullptr`。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Event 类（Windows 运行时 C\+\+ 模板库）](../windows/event-class-windows-runtime-cpp-template-library.md)