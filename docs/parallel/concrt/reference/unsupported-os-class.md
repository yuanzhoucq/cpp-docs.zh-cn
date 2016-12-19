---
title: "unsupported_os 类 | Microsoft Docs"
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
  - "concrt/concurrency::unsupported_os"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unsupported_os 类"
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unsupported_os 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

此类描述使用不受支持的操作系统时抛出的异常。  
  
## 语法  
  
```  
class unsupported_os : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[unsupported\_os::unsupported\_os 构造函数](../Topic/unsupported_os::unsupported_os%20Constructor.md)|已重载。  构造 `unsupported_os` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `unsupported_os`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)