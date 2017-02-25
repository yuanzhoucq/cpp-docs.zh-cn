---
title: "unsupported_feature 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::unsupported_feature"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unsupported_feature 类"
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# unsupported_feature 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

使用不支持的功能时引发的异常。  
  
## 语法  
  
```  
class unsupported_feature : public runtime_exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[unsupported\_feature::unsupported\_feature 构造函数](../Topic/unsupported_feature::unsupported_feature%20Constructor.md)|构造 `unsupported_feature` 异常的新实例。|  
  
## 继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
 `unsupported_feature`  
  
## 要求  
 **标头：**amprt.h  
  
 **命名空间：** 并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)