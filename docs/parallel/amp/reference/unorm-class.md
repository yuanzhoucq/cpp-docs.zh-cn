---
title: "unorm 类 | Microsoft Docs"
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
  - "amp_short_vectors/Concurrency::graphics::unorm"
  - "amp/Concurrency::graphics::unorm"
dev_langs: 
  - "C++"
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unorm 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示一个不规范数。  每个元素都是\[0.0f，1.0f\]范围内的浮点数字。  
  
## 语法  
  
```  
class unorm;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[unorm::unorm 构造函数](../Topic/unorm::unorm%20Constructor.md)|已重载。  默认构造函数。  初始化为 0.0f。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|不规范：操作符\-\-运算符||  
|不规范：操作符 浮点运算符|转换运算符  不规范数转换为浮点值。|  
|不规范：操作符\*\=运算符||  
|不规范：操作符\/\=运算符||  
|不规范：操作符\+\+运算符||  
|不规范：操作符\+\=运算符||  
|不规范：操作符\=运算符||  
|不规范：操作符\-\=运算符||  
  
## 继承层次结构  
 `unorm`  
  
## 要求  
 **页眉：**amp\_short\_vectors.h  
  
 **命名空间：**Concurrency::graphics  
  
## 请参阅  
 [Concurrency::graphics 命名空间](../../../parallel/amp/reference/concurrency-graphics-namespace.md)