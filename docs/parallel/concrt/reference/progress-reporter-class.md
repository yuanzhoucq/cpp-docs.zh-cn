---
title: "progress_reporter 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppltasks/concurrency::progress_reporter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "progress_reporter 类"
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# progress_reporter 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

进程报告程序类允许报告特定类型的进程通知。  每个 progress\_reporter 对象绑定到特定异步操作。  
  
## 语法  
  
```  
template<  
   typename _ProgressType  
>  
class progress_reporter;  
```  
  
#### 参数  
 `_ProgressType`  
 通过进程报告程序报告的每个进程通知的负载类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[progress\_reporter::progress\_reporter 构造函数](../Topic/progress_reporter::progress_reporter%20Constructor.md)||  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[progress\_reporter::report 方法](../Topic/progress_reporter::report%20Method.md)|将进程报表发送给异步操作或进程报告程序绑定的操作。|  
  
## 备注  
 此类型只能用于 Windows 应用商店应用程序。  
  
## 继承层次结构  
 `progress_reporter`  
  
## 要求  
 **标头：**ppltasks.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [create\_async 函数](../Topic/create_async%20Function.md)