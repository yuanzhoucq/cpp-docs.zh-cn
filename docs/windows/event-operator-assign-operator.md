---
title: "Event::operator= 运算符 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 运算符"
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event::operator= 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定对当前 Event 实例的指定 Event 引用。  
  
## 语法  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### 参数  
 `h`  
 为事件实例的一个 Rvalue 引用。  
  
## 返回值  
 为时事实例的指针。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Event 类（Windows 运行时 C\+\+ 模板库）](../windows/event-class-windows-runtime-cpp-template-library.md)