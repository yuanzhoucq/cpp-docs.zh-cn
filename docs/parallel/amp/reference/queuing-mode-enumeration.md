---
title: "queuing_mode 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::queuing_mode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "queuing_mode 枚举"
ms.assetid: 8c641054-906d-40b3-bbb4-f62af9356a14
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queuing_mode 枚举
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定快捷键支持的排队模式。  
  
## 语法  
  
```  
enum queuing_mode;  
```  
  
## 成员  
  
### 值  
  
|名称|描述|  
|--------|--------|  
|`queuing_mode_immediate`|指定任何命令，如 [parallel\_for\_each 函数 \(C\+\+ AMP\)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md)，只要一返回调用方，就要发送到相应的快捷键设备的排队模式。|  
|`queuing_mode_automatic`|指定命令必须排成与 [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md) 对象对应的命令队列的排队模式。  调用 [accelerator\_view::flush](../Topic/accelerator_view::flush%20Method.md) 时会将命令发送到设备。|  
  
## 要求  
 **标头：**amprt.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)