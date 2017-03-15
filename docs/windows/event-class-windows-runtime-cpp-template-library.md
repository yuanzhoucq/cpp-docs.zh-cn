---
title: "Event 类（Windows 运行时 C++ 模板库） | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event"
dev_langs: 
  - "C++"
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event 类（Windows 运行时 C++ 模板库）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一个事件。  
  
## 语法  
  
```  
class Event : public HandleT<HandleTraits::EventTraits>;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[Event::Event 构造函数（Windows 运行时 C\+\+ 模板库）](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|初始化 Event 类的新实例。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[Event::operator\= 运算符](../windows/event-operator-assign-operator.md)|指定对当前 Event 实例的指定 Event 引用。|  
  
## 继承层次结构  
 `HandleT`  
  
 `Event`  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)