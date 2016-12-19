---
title: "accelerator_view_removed 类 | Microsoft Docs"
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
  - "amprt/Concurrency::accelerator_view_removed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "amprt/Concurrency::accelerator_view_removed 类"
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
caps.latest.revision: 6
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# accelerator_view_removed 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

基础 DirectX 调用因 Windows 超时检测和还原机制而失败时引发的异常。  
  
## 语法  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[accelerator\_view\_removed::accelerator\_view\_removed 构造函数](../Topic/accelerator_view_removed::accelerator_view_removed%20Constructor.md)|初始化 `accelerator_view_removed` 类的新实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[accelerator\_view\_removed::get\_view\_removed\_reason 方法](../Topic/accelerator_view_removed::get_view_removed_reason%20Method.md)|返回一个 `accelerator_view` 对象删除的原因的 HRESULT 错误代码。|  
  
## 继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## 要求  
 **标头：**amprt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)